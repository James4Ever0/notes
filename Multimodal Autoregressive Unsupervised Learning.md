---
title: Multimodal Autoregressive Unsupervised Learning
created: '2024-02-28T14:09:13.086Z'
modified: '2024-02-28T14:25:51.080Z'
---

# Multimodal Autoregressive Unsupervised Learning

GPT2 models from huggingface accept `inputs_embeds` as parameter of instance call and method "generate".

Typically to adapt ViT into LLM you need LayerNorm and a linear projection layer.

You cannot put custom embedding into text generaton pipeline.

---

To encode token manually in GPT2:

```python
input_embeds = model.transformer.wte(input_ids)
```

In LLaMA:

```python
def embed_tokens(self，token_ids):
  if hasattr(self.llama_model.base_model, "model"): # with lora
    embeds = self.llama_model.base_model.model.model.embed_tokens(token_ids)
  else:
    self.llama_model.base_model.embed_tokens(token_ids)
return embeds
```

---

Install pytorch gpu with conda:

```bash
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

---

Set `HF_HUB_OFFLINE=1` while loading local models, to prevent accessing network.

---

Set `Environment="OLLAMA_MODELS=<model_storage_path>"` in ollama systemd service file. Remember to change username and usergroup too, and set appropriate permission to model storage path.
