---
created: 2026-07-04T16:37:08+08:00
modified: 2026-07-04T16:37:25+08:00
---

# Effective MLLM Serving for Agentic Visual Grounding and Interactions

A field guide built from experiments on a single NVIDIA RTX 2060 12 GB workstation. We compare serving stacks, model formats, and practical tricks for turning vision-language models into reliable visual agents.

---

## 1. What we are trying to solve

Agentic desktop/mobile automation needs models that can both **see** and **point**:

- OCR an icon or label.
- Return a bounding box or point coordinate for a GUI element.
- Reason about spatial relationships.
- Run locally on consumer hardware.

This is harder than plain image captioning because the output is structured (JSON, bbox tokens, special control tokens) and the serving runtime must preserve those tokens.

---

## 2. The hardware reality

Test bench used throughout these notes:

- **GPU**: NVIDIA GeForce RTX 2060, 12 GB VRAM, compute capability 7.5 (Turing)
- **CPU**: Intel Xeon E5-2673 v3
- **OS**: Ubuntu 24.04
- **Docker**: with `nvidia-container-toolkit`

12 GB sounds generous, but it disappears quickly. A vision encoder, LLM weights, KV cache, CUDA graphs, and a context buffer can consume 9–11 GB before you notice. This forces hard trade-offs between model size, quantization, and context length.

---

## 3. Models evaluated

| Model | Size | Format | Best runtime | Role |
|---|---|---|---|---|
| **Qwen3-VL-8B-Instruct-W4A16-AutoRound-AWQ** | 8B | AWQ (LLM) + FP16 vision | vLLM | General VLM, supports JSON bboxes |
| **Qwen3-VL-2B-Instruct** | 2B | Safetensors / Transformers | vLLM | Fast general VLM, surprisingly good grounding |
| **Qwen3-VL-8B-Instruct-GGUF** (Unsloth) | 8B | Q4_K_M + F16 mmproj | llama.cpp | Local GGUF path for llama.cpp stack |
| **LocateAnything-3B-GGUF** | 3B | Q4_K_M + BF16 mmproj | llama.cpp (mtmd-grounders fork) | Purpose-built grounding model |
| **MiniCPM-V-4.6** | 8B | Safetensors / Transformers | vLLM | General VLM, not optimized for grounding |

### Key observation

Not every vision model can ground. **Qwen3-VL** can output `bbox_2d` JSON. **LocateAnything** was trained specifically for normalized (0–1000) bbox/point tokens. **MiniCPM-V** is a strong general VLM but does not reliably emit structured coordinates.

---

## 4. Two serving stacks that actually work

### Stack A: vLLM for AWQ / Transformers models

Best when:
- You want an OpenAI-compatible `/v1/chat/completions` endpoint.
- The model is in Hugging Face format (AWQ, BnB, BF16, etc.).
- You have enough VRAM for the model + KV cache.

Example for the AWQ 8B model:

```bash
./serve_qwen3vl_awq.sh
```

Key flags learned the hard way:

```bash
--max-model-len 2048        # 4096 OOM'd on RTX 2060
--gpu-memory-utilization 0.95
--limit-mm-per-prompt '{"image": 1}'
```

The original README suggested `max_model_len=4096`, but vLLM failed with:

```text
0.56 GiB KV cache needed, only 0.41 GiB available
```

Reducing context length and raising GPU memory utilization fixed it.

### Stack B: llama.cpp with the mtmd-grounders fork

Best when:
- You want GGUF efficiency.
- You need **special grounding tokens** preserved (`<ref>`, `<box>`, `<0>`–`<999>`).
- You want to run **LocateAnything** or Qwen3-VL GGUF.

Upstream llama.cpp does not expose `--mmproj` in `llama-server` and does not pass `--special` automatically. The fork at [github.com/yuuko-eth/llama.cpp @ mtmd-grounders](https://github.com/yuuko-eth/llama.cpp/tree/mtmd-grounders) adds both.

Build the image:

```bash
./build_llama_cpp_mtmd_grounders_server_cuda.sh
```

Serve LocateAnything:

```bash
./serve_locateanything_q4km.sh
```

Or serve Qwen3-VL 8B GGUF (same image, same endpoint):

```bash
./serve_qwen3vl_8b_gguf_unsloth.sh
```

The same Docker image works for both because both rely on the mtmd multimodal stack.

---

## 5. Why Ollama is not enough

Ollama wraps llama.cpp but hides the knobs that matter for grounding:

- It does not expose `--special`, so grounding control tokens are stripped from output.
- It applies its own chat templates, which can break model-specific grounding prompts.
- It does not reliably pair LLM GGUFs with the correct `mmproj` for newer mtmd models.

Result: a model that grounds perfectly in vLLM or raw llama.cpp returns only plain text in Ollama. For agentic use that depends on structured coordinates, bypass Ollama.

That said, Ollama still works fine for general multimodal tasks — captioning, VQA, or running MiniCPM-V where grounding tokens are not required.

---

## 6. Key scripts in this repo

### Download scripts

| Script | What it pulls |
|---|---|
| `download_awq_qwen3_vl.sh` | Qwen3-VL-8B-Instruct AWQ via hf-mirror |
| `download_qwen3vl_8b_gguf_q4km.sh` | Official Qwen3-VL-8B Q4_K_M + F16 mmproj |
| `download_qwen3vl_8b_gguf_unsloth_q4km.sh` | Unsloth Qwen3-VL-8B Q4_K_M + F16 mmproj |
| `download_locate_anything_gguf.sh` | LocateAnything-3B-GGUF |
| `download_minicpm_v4.6.sh` | MiniCPM-V-4.6 |
| `download_qwen3_2b.sh` | Qwen3-VL-2B-Instruct |

All use `hfd.sh` from [hf-mirror.com/hfd/hfd.sh](https://hf-mirror.com/hfd/hfd.sh) with `HF_ENDPOINT=https://hf-mirror.com` for faster downloads in this region.

### Serve scripts

| Script | Runtime | Model |
|---|---|---|
| `serve_qwen3vl_awq.sh` | vLLM Docker | Qwen3-VL-8B AWQ |
| `serve_qwen3vl_2b.sh` | vLLM Docker | Qwen3-VL-2B |
| `serve_minicpm_v4.6.sh` | vLLM Docker | MiniCPM-V-4.6 |
| `serve_locateanything_q4km.sh` | llama.cpp Docker (mtmd-grounders) | LocateAnything-3B Q4_K_M |
| `serve_qwen3vl_8b_gguf_unsloth.sh` | llama.cpp Docker (mtmd-grounders) | Qwen3-VL-8B Unsloth Q4_K_M |

### Test scripts

| Script | Task |
|---|---|
| `test_qwen3vl_awq_ocr.sh` | OCR with Qwen3-VL-8B AWQ |
| `test_qwen3vl_awq_locate.sh` | JSON bbox grounding with Qwen3-VL-8B AWQ |
| `test_qwen3vl_2b_ocr.sh` | OCR with Qwen3-VL-2B |
| `test_qwen3vl_2b_locate.sh` | JSON bbox grounding with Qwen3-VL-2B |
| `test_locateanything_q4km_ocr.sh` | Scene-text detection with LocateAnything |
| `test_qwen3vl_8b_gguf_unsloth_locate.sh` | JSON bbox grounding with Qwen3-VL-8B GGUF |

---

## 7. Practical lessons

### Lesson 1: full precision vision > quantized vision

The AWQ Qwen3-VL README notes that the **vision tower remains FP16**. Keeping vision at full precision preserves OCR and grounding accuracy. When you quantize vision, coordinate drift and text recognition degrade quickly.

### Lesson 2: smaller models are often the better tool

On an RTX 2060:

- Qwen3-VL-8B AWQ is usable but slow.
- Qwen3-VL-2B is much faster and still outputs decent JSON bboxes.
- LocateAnything-3B is tiny, purpose-built, and runs comfortably in GGUF form.

If the task is grounding, prefer a 2–3 B specialized model over an 8 B generalist.

### Lesson 3: llama.cpp > Ollama for multimodal *grounding*

Raw llama.cpp (or the mtmd-grounders fork) lets you pass `--special`, `--mmproj`, `--jinja`, and `--flash-attn`. Ollama abstracts these away, which breaks grounding for models that rely on special tokens. For plain captioning or VQA, Ollama is still convenient.

### Lesson 4: context length is expensive

vLLM failed at `max_model_len=4096` on the AWQ model because the KV cache alone needed 0.56 GB and only 0.41 GB was free. Dropping to 2048 fixed it. For OCR/grounding tasks you rarely need 4k+ context anyway.

### Lesson 5: one image at a time

Use `--limit-mm-per-prompt '{"image": 1}'` in vLLM to control vision token budget. Vision encoding dominates latency and memory.

---

## 8. Tricks for visual grounding

### Trick 1: ask for structured JSON

Qwen3-VL can be prompted to return JSON:

```text
Locate all icons in this image and return a JSON list with bbox_2d and label.
```

Sample response:

```json
[
  {"bbox_2d": [16, 14, 127, 173], "label": "此电脑"},
  {"bbox_2d": [162, 14, 272, 173], "label": "微信"}
]
```

### Trick 2: use a red grid overlay

If a model cannot ground natively, overlay a numbered grid on the image and ask the model to name the grid cells containing the target. This is an old computer-use-agent trick and works with any VLM.

### Trick 3: two-stage pipeline

1. Use a fast VLM (Qwen3-VL-2B or MiniCPM-V) to **recognize** the scene and choose a target.
2. Use **LocateAnything** to get the precise bbox for that target.

This gives you both semantic understanding and pixel-accurate localization.

---

## 9. Future thoughts

### Runtime convergence

The ideal stack is a single Docker image that can serve:

- AWQ / GPTQ / BnB models via vLLM or SGLang for speed.
- GGUF models via llama.cpp for efficiency and special-token grounding.
- A small router that picks the right backend based on model format and task.

Today we maintain two images. Tomorrow, projects like `llama.cpp`'s mtmd stack or vLLM's multimodal support may absorb the special-token requirement and make the fork unnecessary.

### Better quantization

- **AWQ → Marlin** is much faster on Ampere/Ada GPUs, but not on Turing.
- **GPTQ + ExLlama v2** is often faster than AWQ on consumer GPUs.
- **FP8/INT8 dynamic quantization** may become the sweet spot for vision models once kernels mature.

On RTX 2060, the best immediate move is model size reduction (2–3 B) rather than chasing faster quants.

### Grounding-specialized small models

LocateAnything-3B points to a promising future: tiny models trained specifically for grounding. We expect more 1–4 B parameter models that combine a lightweight VLM with parallel box decoding, making real-time desktop agents feasible on laptop GPUs.

### Beyond bboxes

The next step is **UI element graphs**: models that output not just `(x1, y1, x2, y2)` but also element type, text, relationships, and actionable affordances. This moves from "point at the icon" to "click the Submit button inside the login form."

---

## 10. Quick start checklist

```bash
# 1. Pick a model
./download_qwen3vl_8b_gguf_unsloth_q4km.sh   # or
./download_locate_anything_gguf.sh           # or
./download_awq_qwen3_vl.sh

# 2. Build the llama.cpp image (only needed once)
./build_llama_cpp_mtmd_grounders_server_cuda.sh

# 3. Stop any other GPU container to free VRAM
docker stop vllm-serving

# 4. Serve
./serve_qwen3vl_8b_gguf_unsloth.sh   # or
./serve_locateanything_q4km.sh       # or
./serve_qwen3vl_awq.sh

# 5. Test
./test_qwen3vl_8b_gguf_unsloth_locate.sh   # or
./test_locateanything_q4km_ocr.sh          # or
./test_qwen3vl_awq_locate.sh
```

---

## 11. Important links

- `hfd.sh` downloader: https://hf-mirror.com/hfd/hfd.sh
- LocateAnything-3B: https://huggingface.co/nvidia/LocateAnything-3B
- LocateAnything GGUF: https://huggingface.co/yuuko-eth/LocateAnything-3B-GGUF
- mtmd-grounders llama.cpp fork: https://github.com/yuuko-eth/llama.cpp/tree/mtmd-grounders
- Qwen3-VL-8B-Instruct-GGUF (official): https://huggingface.co/Qwen/Qwen3-VL-8B-Instruct-GGUF
- Qwen3-VL-8B-Instruct-GGUF (Unsloth): https://huggingface.co/unsloth/Qwen3-VL-8B-Instruct-GGUF
- Qwen3-VL-8B-Instruct-AWQ: https://huggingface.co/Vishva007/Qwen3-VL-8B-Instruct-W4A16-AutoRound-AWQ
- vLLM: https://github.com/vllm-project/vllm
- llama.cpp: https://github.com/ggml-org/llama.cpp

---

## 12. Closing note

Effective MLLM serving for agents is not about running the biggest model. It is about matching the right model format, runtime, and prompt to the task. On consumer hardware, a 2–3 B grounding model in GGUF often outperforms an 8 B generalist in both speed and accuracy. Preserve special tokens, respect VRAM limits, and always test the full pipeline end-to-end before committing to a stack.
