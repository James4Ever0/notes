---
title: 'chatgpt clones, computer automation with ai'
created: '2023-04-02T10:39:51.304Z'
modified: '2023-04-02T16:06:19.277Z'
---

# chatgpt clones, computer automation with ai

simply because the original note on chatgpt is too long, we start a new one, with more topics and more resources.

----

visit [poe.com](https://poe.com/) for a bunch of free chatbots, including GPT-4

[chathub](https://github.com/chathub-dev/chathub) is a browser plugin which you can use ChatGPT, Bing and Bard

----

[ts_server](https://bellard.org/ts_server/) supports a bunch of models like GPT-J, GPT-NeoX, GPT-Neo, OPT, Fairseq GPT, M2M100, CodeGen, GPT2, T5, RWKV, LLAMA and Stable Diffusion, used by [textsynth.com](https://textsynth.com/)

----

to manage python versions and environments, [pyenv](https://github.com/pyenv/pyenv) and [venv](https://docs.python.org/3/library/venv.html) is lightweight and [miniconda](https://docs.conda.io/en/latest/miniconda.html) or [mamba](https://mamba.readthedocs.io/en/latest/user_guide/mamba.html) is more sophisticated.

----

javascript code for extracting model list from huggingface personal homepage:

```javascript
var arr = [];
for (var i of document.getElementsByTagName("h4")) {var t = i.innerText; var tlist = t.split("/"); var t0 = tlist[0]; var t1 = tlist[1]; arr.push(`| [${t1}](https://huggingface.co/${t}) | unknown | unknown | ${t0} |`)};
console.log(arr.join('
'));
```

----

convert arxiv paper (pdf) into html: [arxiv vanity](https://www.arxiv-vanity.com/) (you will have a better view than before, though [will not always work](https://www.arxiv-vanity.com/papers/2303.12712/)) code [on github](https://github.com/arxiv-vanity/arxiv-vanity)

[aminer](https://www.aminer.cn/) is similar to [paperswithcode](https://paperswithcode.com/), in which you may find interesting papers.

----

someone prefers [bert4keras](https://github.com/bojone/bert4keras) since it implements multiple LLM into Keras, also easy for GPT-2 LoRA training (by adding a single layer)

----

people love to post uncensorable links and torrents to [internet archive](https://archive.org) and [the-eye](https://github.com/The-Eye-Team), just like the gpt-4chan

----

to create a simple API (compatible with OpenAI APIs) for LLMs, use [SimpleAI](https://github.com/lhenault/simpleAI)

## fine-tuning and tricks

[PEFT](https://github.com/huggingface/peft) (Parameter Efficient Fine Tuning) supports LoRA, Prefix Tuning, P-Tuning and Prompt Tuning.

## computer automation with ai

### virtual machines and environments

it is not feasible to install [ubuntu arm](https://ubuntu.com/download/server/arm) on macos m1 with virtualbox. use [utm.app](https://getutm.app/) instead. [instructions on installing ubuntu with utm](https://docs.getutm.app/guides/ubuntu/) includes guides on sharing clipboard and directory.

### papers

[playing atari using q-learning](https://www.arxiv-vanity.com/papers/1312.5602/) (viewing deepmind paper with arxiv vanity)

### models

[video pretraining](https://openai.com/research/vpt) can perform minecraft diamond mining tasks with keyboard and mouse movements

[code and model](https://github.com/openai/Video-Pre-Training)

----

[mm-cot](https://github.com/amazon-science/mm-cot) (multimodal chain-of-thought) by amazon, with [model weights](https://drive.google.com/file/d/1FtTYOJPHnWnFfCxNC6M3gar4RAX5E21b/view)

### data collectors and controllers

[mss](https://python-mss.readthedocs.io/) for screenshot, remember to save raw pixels to SSD, then compress into mp4 with ffmpeg for further training (mind the timestamp!)

----

[go-vncdriver](https://github.com/openai/go-vncdriver) by openai, to compile you need to clone the repo and modify code to find headers for libjpeg-turbo and python.

[libvncdriver](https://pypi.org/project/libvncdriver/)

[asyncvnc](https://pypi.org/project/asyncvnc/) (supports apple vnc), side project: [asyncssh](https://github.com/ronf/asyncssh)

[python-vnc-client](https://github.com/masamitsu-murase/python_vnc_client) with keydown/keyup event support

[vncdotool](https://pypi.org/project/vncdotool/)

[pyVNC](https://github.com/cair/pyVNC)

----

[pynput](https://python-mss.readthedocs.io/) as input event listener and actor, listener may have some strange keycodes when pressing modifier keys on windows.

note that special care needed for aligning mouse location with screenshot size

----

[ViT-pytorch](https://github.com/lucidrains/vit-pytorch) can be used in many ViT-based models, listed and implemented in the repo.

### spaces

openai [universe](https://github.com/openai/universe) (blog post [here](https://openai.com/blog/universe/)) and [starter agents](https://github.com/openai/universe-starter-agent), remotes are using vnc protocol and a reward protocol using websocket sending json (can send actions). they prefer [TigerVNC](https://tigervnc.org/), maybe that will send the existing monitor instead of invisible ones.

[gym](https://github.com/openai/gym) is classic and modular. [atari-py](https://github.com/openai/atari-py) enables old games

[retro](https://github.com/openai/retro) deprecates universe, but might help with general computer controlling AI systems since they are compatible. human don't play games all day and night. beware of this and don't turn the model into a heavy gamer.

there is no meaning of recording terminal input/output when using tools like `vim`. get screenshots, keystrokes and mouse clicks instead (using `ttyd`, [`gremlins.js`](https://github.com/marmelab/gremlins.js) or [`monkey.js`](https://github.com/zhuochun/monkey.js)). `tkterminal` won't do. it is just a thin wrapper around `subprocess.run`

talking of browser, you can spin up [novnc](https://github.com/novnc/noVNC) server and let the [`gremlins.js`](https://github.com/marmelab/gremlins.js) do its job.

## accelerators

### [cformers](https://github.com/NolanoOrg/cformers/)

cpu only

able to install from pip

### [ggml](https://github.com/ggerganov/ggml)

cpu only

cpp, only compile from source

### [flexgen](https://github.com/FMInference/FlexGen)

gpu is mandatory, better than deepspeed and [Hugging Face Accelerate](https://github.com/huggingface/accelerate)

## open source model and weights

[awesome decentralized llm](https://github.com/imaurer/awesome-decentralized-llm) listed up-to-date related chatgpt-like repositories, datasets, model weights and resources.

----

model weights of open source chatgpt alternatives:

| weight path | model size | model name | author |
| -- | -- | -- | -- |
| [openchatgpt-neox-125m](https://huggingface.co/mrsteyk/openchatgpt-neox-125m) | 125m | gpt-neox | mrsteyk |
| [openchatgpt-neo-125m](https://huggingface.co/mrsteyk/openchatgpt-neo-125m) | 125m | gpt-neo | mrsteyk |


### LLaMA

it's public.

| weight path | model name | author |
| -- | -- | -- |
| [llama-13b-hf-int4](https://huggingface.co/decapoda-research/llama-13b-hf-int4) | 13b |decapoda-research |
| [llama-65b-hf-int4](https://huggingface.co/decapoda-research/llama-65b-hf-int4) | 65b |decapoda-research |
| [llama-30b-hf-int4](https://huggingface.co/decapoda-research/llama-30b-hf-int4) | 30b |decapoda-research |
| [llama-7b-hf-int4](https://huggingface.co/decapoda-research/llama-7b-hf-int4) | 7b |decapoda-research |
| [llama-30b-hf](https://huggingface.co/decapoda-research/llama-30b-hf) | 30b |decapoda-research |
| [llama-65b-hf](https://huggingface.co/decapoda-research/llama-65b-hf) | 65b |decapoda-research |
| [llama-13b-hf](https://huggingface.co/decapoda-research/llama-13b-hf) | 13b |decapoda-research |
| [llama-7b-hf](https://huggingface.co/decapoda-research/llama-7b-hf) | 7b |decapoda-research |
| [llama-smallint-pt](https://huggingface.co/decapoda-research/llama-smallint-pt) | unknown |decapoda-research |
| [llama-7b-hf-int8](https://huggingface.co/decapoda-research/llama-7b-hf-int8) | 7b | decapoda-research |

### [ChatYuan](https://github.com/clue-ai/ChatYuan)

v2 is censored.

----

model weights:

| weight path | model size | model name | author |
| -- | -- | -- | -- |
| [ChatYuan-large-v1](https://huggingface.co/ClueAI/ChatYuan-large-v1) | unknown | unknown | ClueAI |
| [ChatYuan-large-v2-paddle](https://huggingface.co/ClueAI/ChatYuan-large-v2-paddle) | unknown | unknown | ClueAI |
| [ChatYuan-large-v2](https://huggingface.co/ClueAI/ChatYuan-large-v2) | unknown | unknown | ClueAI |
| [ChatYuan-large-v1-paddle](https://huggingface.co/ClueAI/ChatYuan-large-v1-paddle) | unknown | unknown | ClueAI |

### [Deepshard](https://huggingface.co/swype/)

LLaMA trained on [custom instruction dataset](https://huggingface.co/datasets/swype/instruct-102.4k).

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [deepshard-13B-ft](https://huggingface.co/swype/deepshard-13B-ft) | 13b | deepshard | swype |
| [deepshard-13B-raw](https://huggingface.co/swype/deepshard-13B-raw) | 13b | deepshard | swype |

### [ChatGLM](https://chatglm.cn/blog)

Currently only open-sourced 6B version.

You can train ChatGLM using GXT3090: [simple_thu_chatglm6b](https://github.com/yuanzhoulvpi2017/zero_nlp/tree/main/simple_thu_chatglm6b)

Using 7GB VRAM, train ChatGLM with [P-tuning](https://github.com/THUDM/ChatGLM-6B/tree/main/ptuning)

[chatglm_finetuning](https://github.com/ssbuild/chatglm_finetuning) supports loading from int4 weights

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [chatglm-6b-int4-slim](https://huggingface.co/silver/chatglm-6b-int4-slim) | 6b | chatglm | silver |
| [chatglm-6b-slim](https://huggingface.co/silver/chatglm-6b-slim) | 6b | chatglm | silver |
| [chatglm-6b-int4-qe-slim](https://huggingface.co/silver/chatglm-6b-int4-qe-slim) | 6b | chatglm | silver |
| [chatglm-6b-int4](https://huggingface.co/THUDM/chatglm-6b-int4) | 6b | chatglm | THUDM |
| [chatglm-6b-int4-qe](https://huggingface.co/THUDM/chatglm-6b-int4-qe) | 6b | chatglm | THUDM |
| [chatglm-6b](https://huggingface.co/THUDM/chatglm-6b) | 6b | chatglm | THUDM |

### [ChatDoctor](https://huggingface.co/zl111/ChatDoctor)

[LLaMA-65B](https://huggingface.co/datasets/nyanko7/LLaMA-65B) trained on medical dataset [InstructorDoctor-200k](https://drive.google.com/file/d/1lyfqIwlLSClhgrCutWuEe_IACNq6XNUt/view?usp=sharing)

### [BELLE](https://github.com/LianjiaTech/BELLE)

开源中文对话大模型

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [BELLE-LLAMA-7B-0.6M](https://huggingface.co/BelleGroup/BELLE-LLAMA-7B-0.6M) | 7B | LLaMA | BelleGroup |
| [BELLE-LLAMA-7B-2M](https://huggingface.co/BelleGroup/BELLE-LLAMA-7B-2M) | 7B | LLaBLOOMZMA | BelleGroup |
| [BELLE-LLAMA-7B-2M-gptq](https://huggingface.co/BelleGroup/BELLE-LLAMA-7B-2M-gptq) | 7B | LLaMA | BelleGroup |
| [BELLE-LLAMA-13B-2M](https://huggingface.co/BelleGroup/BELLE-LLAMA-13B-2M) | 13B | LLaMA | BelleGroup |
| [BELLE-7B-gptq](https://huggingface.co/BelleGroup/BELLE-7B-gptq) | 7B | BLOOMZ | BelleGroup |
| [BELLE-7B-2M](https://huggingface.co/BelleGroup/BELLE-7B-2M) | 7B | BLOOMZ | BelleGroup |
| [BELLE-7B-0.6M](https://huggingface.co/BelleGroup/BELLE-7B-0.6M) | 7B | BLOOMZ | BelleGroup |
| [BELLE-7B-0.2M](https://huggingface.co/BelleGroup/BELLE-7B-0.2M) | 7B | BLOOMZ | BelleGroup |
| [BELLE-7B-1M](https://huggingface.co/BelleGroup/BELLE-7B-1M) | 7B | BLOOMZ | BelleGroup |

### [baize](https://github.com/project-baize/baize)

trained on ChatGPT self-chatting data

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [baize-lora-30B](https://huggingface.co/project-baize/baize-lora-30B) | 30b | baize | project-baize |
| [baize-lora-13B](https://huggingface.co/project-baize/baize-lora-13B) | 13b | baize | project-baize |
| [baize-healthcare-lora-7b](https://huggingface.co/project-baize/baize-healthcare-lora-7b) | 7B | baize | project-baize |
| [baize-lora-7B](https://huggingface.co/project-baize/baize-lora-7B) | 7B | baize | project-baize |

### [dolly](https://github.com/databrickslabs/dolly)

model arch is gpt-j, trained on alpaca dataset

----

model weights:


| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [dolly-v1-6b](https://huggingface.co/databricks/dolly-v1-6b) | 6b | dolly | databricks |
| [dolly-lora](https://huggingface.co/samwit/dolly-lora) | unknown | dolly | samwit |

### [FastChat](https://github.com/lm-sys/FastChat) (Vicuna)

[web interface](https://chat.lmsys.org/)

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- |
| [vicuna](https://huggingface.co/chavinlo/vicuna) | unknown | Vicuna | chavinlo |
| [vicuna2](https://huggingface.co/chavinlo/vicuna2) | unknown | Vicuna | chavinlo |
| [vicuna-13b-delta-v0](https://huggingface.co/lmsys/vicuna-13b-delta-v0) | 13b | Vicuna | lmsys |
| [vicuna-13b-GPTQ-4bit-128g](https://huggingface.co/anon8231489123/vicuna-13b-GPTQ-4bit-128g) | 13b | vicuna | anon8231489123 |
| [ggml-vicuna-13b-4bit](https://huggingface.co/eachadea/ggml-vicuna-13b-4bit) | 13b | vicuna | eachadea |
| [vicuna-13b](https://huggingface.co/eachadea/vicuna-13b) | 13b | vicuna | eachadea |
| [vicuna4all](https://huggingface.co/vicuna4all/vicuna4all) | 13b | vicuna | vicuna4all |

download official delta weights via [magnet](magnet:?xt=urn:btih:a7fac57094561a63d53eed943f904abf24c6969d&dn=Vicuna-13B-HF-fp16-delta-merged_2023-04-03&tr=udp%3a%2f%2ftracker.opentrackr.org%3a1337%2fannounce&tr=udp%3a%2f%2ftracker-udp.gbitt.info%3a80%2fannounce&tr=udp%3a%2f%2ftracker1.bt.moack.co.kr%3a80%2fannounce&tr=udp%3a%2f%2ftracker.tiny-vps.com%3a6969%2fannounce&tr=udp%3a%2f%2ftracker2.dler.org%3a80%2fannounce&tr=udp%3a%2f%2fopentracker.i2p.rocks%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.altrosky.nl%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.theoks.net%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.dler.org%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.torrent.eu.org%3a451%2fannounce&tr=udp%3a%2f%2ftracker.openbittorrent.com%3a6969%2fannounce&tr=https%3a%2f%2fopentracker.i2p.rocks%3a443%2fannounce&tr=http%3a%2f%2ftracker.openbittorrent.com%3a80%2fannounce&tr=udp%3a%2f%2ftracker.moeking.me%3a6969%2fannounce&tr=udp%3a%2f%2ftracker.monitorit4.me%3a6969%2fannounce&tr=udp%3a%2f%2f9.rarbg.com%3a2810%2fannounce
based)

### Bloom-z

there is [bloomz.cpp](https://github.com/NouamaneTazi/bloomz.cpp), converted model weights on [huggingface](https://huggingface.co/models?other=bloom&other=ggml)

### [Alpaca](https://github.com/tatsu-lab/stanford_alpaca)

alpaca is LLaMA tuned on ChatGPT self-instruct dataset. officially there is just code and dataset, model weights are community provided.

ggml version: [alpaca.cpp](https://github.com/antimatter15/alpaca.cpp)

example on how to load PEFT patched alpaca model: [alpaca-lora/generate.py](0https://github.com/aspctu/alpaca-lora/blob/main/generate.py)

it's better to check for [python bindings](https://github.com/abetlen/llama-cpp-python) and [webui](https://github.com/abdeladim-s/pyllamacpp) like [Alpaca-Turbo](https://github.com/ViperX7/Alpaca-Turbo) and [Dalai](https://cocktailpeanut.github.io/dalai/) for further development and interactions.

----

fine-tuning:

[simple-llama-finetuner](https://github.com/lxe/simple-llama-finetuner) using LoRA, 16GB VRAM minimum

[alpaca-lora](https://github.com/tloen/alpaca-lora): the OG LoRA alpaca

----

community model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [alpaca-lora-7b](https://huggingface.co/tloen/alpaca-lora-7b) | 7b | Alpaca | tloen |
| [Alpaca Native](https://huggingface.co/chavinlo/alpaca-native) | 7B | Alpaca | chavinlo |
| [Alpaca-65B](https://huggingface.co/chavinlo/Alpaca-65B) | 65B | Alpaca | chavinlo |
| [Alpaca 13B](https://huggingface.co/chavinlo/alpaca-13b) | 13B | Alpaca | chavinlo |
| [GPT4-X-Alpaca](https://huggingface.co/chavinlo/gpt4-x-alpaca) | 13B | Alpaca | chavinlo |
| [Toolpaca](https://huggingface.co/chavinlo/toolpaca) | 13B | Alpaca | chavinlo |
| [instruct-gpt-j-fp16](https://huggingface.co/nlpcloud/instruct-gpt-j-fp16) | 6B | GPT-J | nlpcloud |
| [alpaca-30b](https://huggingface.co/baseten/alpaca-30b) | 30b | Alpaca | [baseten](https://abuqader.substack.com/p/releasing-alpaca-30b) |
| [alpaca-lora-65b](https://huggingface.co/chansung/alpaca-lora-65b) | 65b | alpaca | chansung |
| [alpaca-lora-30b](https://huggingface.co/chansung/alpaca-lora-30b) | 30b | alpaca | chansung |
| [koalpaca-lora-13b](https://huggingface.co/chansung/koalpaca-lora-13b) | 13b | koalpaca | chansung |
| [alpaca-lora-13b](https://huggingface.co/chansung/alpaca-lora-13b) | 13b | alpaca | chansung |
| [alpaca13B-lora](https://huggingface.co/samwit/alpaca13B-lora) | 13b | alpaca | samwit |
| [alpaca7B-lora](https://huggingface.co/samwit/alpaca7B-lora) | 7b | alpaca | samwit |
| [bloompaca-7b1-lora](https://huggingface.co/samwit/bloompaca-7b1-lora) | 7b | bloom | samwit |
| [gpt4-x-alpaca-native-13B-ggml](https://huggingface.co/Pi3141/gpt4-x-alpaca-native-13B-ggml) | 13b | alpaca | Pi3141 |
| [alpaca-native-7B-ggml](https://huggingface.co/Pi3141/alpaca-native-7B-ggml) | 7b | alpaca | Pi3141 |
| [alpaca-native-13B-ggml](https://huggingface.co/Pi3141/alpaca-native-13B-ggml) | 13b | alpaca | Pi3141 |
| [alpaca-lora-30B-ggml](https://huggingface.co/Pi3141/alpaca-lora-30B-ggml) | 30b | alpaca | Pi3141 |
| [alpaca-lora-7B-ggml](https://huggingface.co/Pi3141/alpaca-lora-7B-ggml) | 7b | alpaca | Pi3141 |
| [alpaca-lora-13B-ggml](https://huggingface.co/Pi3141/alpaca-lora-13B-ggml) | 13b | alpaca | Pi3141 |
| [alpaca-7b-native-enhanced](https://huggingface.co/Pi3141/alpaca-7b-native-enhanced) | 7b | alpaca | Pi3141 |
| [gpt4-x-alpaca-13b-native-4bit-128g](https://huggingface.co/anon8231489123/gpt4-x-alpaca-13b-native-4bit-128g) | 13b | alpaca | anon8231489123 |
| [ggml-gpt4-x-alpaca-13b-native-4bit](https://huggingface.co/eachadea/ggml-gpt4-x-alpaca-13b-native-4bit) | 13b | alpaca | eachadea |
| [alpaca-13b-hf-fp16](https://huggingface.co/teknium/alpaca-13b-hf-fp16) | 13b | alpaca | teknium |

----

[codealpaca](https://github.com/sahil280114/codealpaca) only provides [dataset](https://huggingface.co/datasets/sahil2801/CodeAlpaca-20k) for training a code generation model, there are multiple models trained on this dataset, including [bloom-7b1-lora-codealpaca20k](https://huggingface.co/LinhDuong/bloom-7b1-lora-codealpaca20k)

### [togethercomputer](https://huggingface.co/togethercomputer)

released [openchatkit](https://github.com/togethercomputer/OpenChatKit) with retrieval ability and [its huggingface space](https://huggingface.co/spaces/togethercomputer/OpenChatKit)

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [GPT-NeoXT-Chat-Base-20B](https://huggingface.co/togethercomputer/GPT-NeoXT-Chat-Base-20B) | 20B | GPT-NeoXT | togethercomputer |
| [Pythia-Chat-Base-7B](https://huggingface.co/togethercomputer/Pythia-Chat-Base-7B) | 7B | Pythia | togethercomputer |

----

moderation model weights:


| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [GPT-JT-Moderation-6B](https://huggingface.co/togethercomputer/GPT-JT-Moderation-6B) | 6B | GPT-JT | togethercomputer |

### [SpikeGPT](https://github.com/ridgerchu/SpikeGPT)

inspired by RWKV

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [SpikeGPT-BookCorpus](https://huggingface.co/ridger/SpikeGPT-BookCorpus) | unknown | SpikeGPT | ridger |

### [RWKV](https://github.com/BlinkDL/RWKV-LM)


----

RWKV combines attention with RNN so the token window can be much larger.

[Longformer](https://huggingface.co/docs/transformers/model_doc/led) is similar to this. Model weights in [github repo](https://github.com/allenai/longformer) or [huggingface](https://huggingface.co/allenai/longformer-base-4096).

----

now we have [rwkv.cpp](https://github.com/saharNooby/rwkv.cpp) (4bit quantization), build upon ggml and sure it works on cpu.

[rwkvstic](https://pypi.org/project/rwkvstic/) (with 8bit & offload for low VRAM GPUs)

----

[RWKV-LoRA](https://github.com/Blealtan/RWKV-LM-LoRA) supports `RWKV-v4-NeoX`

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [RWKV-7B-alpaca-finetuned](https://huggingface.co/BlueSunflower/RWKV-7B-alpaca-finetuned) | 7b | RWKV | BlueSunflower |
| [rwkv-4-14B-alpaca-finetune-lora-weights](https://huggingface.co/BlueSunflower/rwkv-4-14B-alpaca-finetune-lora-weights) | 14b | RWKV | BlueSunflower |
| [rwkv-fastquant](https://huggingface.co/Hazzzardous/rwkv-fastquant) | unknown | rwkv | Hazzzardous |
| [rwkv-onnx](https://huggingface.co/Hazzzardous/rwkv-onnx) | unknown | rwkv | Hazzzardous |
| [RWKV-8Bit](https://huggingface.co/Hazzzardous/RWKV-8Bit) | unknown | rwkv | Hazzzardous |
| [rwkv-4-raven](https://huggingface.co/BlinkDL/rwkv-4-raven) | unknown | rwkv | BlinkDL |
| [rwkv-4-pile-7b](https://huggingface.co/BlinkDL/rwkv-4-pile-7b) | 7b | rwkv | BlinkDL |
| [rwkv-4-pile-14b](https://huggingface.co/BlinkDL/rwkv-4-pile-14b) | 14b | rwkv | BlinkDL |
| [rwkv-4-pile-430m](https://huggingface.co/BlinkDL/rwkv-4-pile-430m) | 430m | rwkv | BlinkDL |
| [rwkv-4-pile-3b](https://huggingface.co/BlinkDL/rwkv-4-pile-3b) | 3b | rwkv | BlinkDL |
| [rwkv-4-pile-1b5](https://huggingface.co/BlinkDL/rwkv-4-pile-1b5) | 1.5b | rwkv | BlinkDL |
| [rwkv-4-pile-169m](https://huggingface.co/BlinkDL/rwkv-4-pile-169m) | 169m | unknown | BlinkDL |
| [rwkv-3-pile-1b5](https://huggingface.co/BlinkDL/rwkv-3-pile-1b5) | 1.5b | rwkv | BlinkDL |
| [rwkv-3-pile-430m](https://huggingface.co/BlinkDL/rwkv-3-pile-430m) | 430m | rwkv | BlinkDL |
| [rwkv-2-pile-430m](https://huggingface.co/BlinkDL/rwkv-2-pile-430m) | 430m | rwkv | BlinkDL |
| [rwkv-3-pile-169m](https://huggingface.co/BlinkDL/rwkv-3-pile-169m) | 169m | rwkv | BlinkDL |
| [RWKV-LM-safetensors](https://huggingface.co/mrsteyk/RWKV-LM-safetensors) | unknown | RWKV | mrsteyk |
| [openchatrwkv-430m-r2.0.1](https://huggingface.co/mrsteyk/openchatrwkv-430m-r2.0.1) | 430m | RWKV | mrsteyk |
| [openchatrwkw-430m-r2](https://huggingface.co/mrsteyk/openchatrwkw-430m-r2) | 430m | RWKV | mrsteyk |
| [openchatrwkv-430m](https://huggingface.co/mrsteyk/openchatrwkv-430m) | 430m | RWKV | mrsteyk |

encrypted alpaca model weights released by point-network: [point-alpaca](https://github.com/pointnetwork/point-alpaca) 

### [gpt4all](https://github.com/nomic-ai/gpt4all) by nomic

LLaMA trained on massive collection of clean assistant dialog data, with model weights

you need to install nomic to run the model:

```bash
pip3 install nomic
```

to run it on gpu, you need to install [this](https://github.com/nomic-ai/nomic/tree/main/bin)

### [openassistant](https://github.com/LAION-AI/Open-Assistant)

researchers of open-assistant like [andreaskoepf](https://huggingface.co/andreaskoepf) has releasesed [oasst-sft-3-pythia-12b-epoch-3.5](https://huggingface.co/andreaskoepf/oasst-sft-3-pythia-12b-epoch-3.5) and still updating

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [oasst-llama-13b-2-epochs](https://huggingface.co/dvruette/oasst-llama-13b-2-epochs) | 13b | llama | dvruette |
| [oasst-llama-13b-1000-steps](https://huggingface.co/dvruette/oasst-llama-13b-1000-steps) | 13b | llama | dvruette |
| [oasst-gpt-neox-20b-1000-steps](https://huggingface.co/dvruette/oasst-gpt-neox-20b-1000-steps) | 20b | gpt-neox | dvruette |
| [oasst-gpt-neox-20b-3000-steps](https://huggingface.co/dvruette/oasst-gpt-neox-20b-3000-steps) | 20b | gpt-neox | dvruette |
| [oasst-pythia-12b-6000-steps](https://huggingface.co/dvruette/oasst-pythia-12b-6000-steps) | 12b | pythia | dvruette |
| [oasst-pythia-12b-3000-steps](https://huggingface.co/dvruette/oasst-pythia-12b-3000-steps) | 12b | pythia | dvruette |
| [oasst-pythia-12b-flash-attn-5000-steps](https://huggingface.co/dvruette/oasst-pythia-12b-flash-attn-5000-steps) | 12b | pythia | dvruette |
| [oasst-pythia-6.9b-4000-steps](https://huggingface.co/dvruette/oasst-pythia-6.9b-4000-steps) | 12b | pythia | dvruette |
| [oasst-sft-1-pythia-12b](https://huggingface.co/OpenAssistant/oasst-sft-1-pythia-12b) | 12b | pythia | OpenAssistant |
| [galactica-6.7b-finetuned](https://huggingface.co/OpenAssistant/galactica-6.7b-finetuned) | 6.7b | galatica | OpenAssistant |
| [oasst-sft-4-pythia-12b-epoch-3.5](https://huggingface.co/andreaskoepf/oasst-sft-4-pythia-12b-epoch-3.5) | 12b | pythia | andreaskoepf |
| [pythia-12b-pre-2000](https://huggingface.co/andreaskoepf/pythia-12b-pre-2000) | 12b | pythia | andreaskoepf |
| [pythia-12b-pre-3500](https://huggingface.co/andreaskoepf/pythia-12b-pre-3500) | 12b | pythia | andreaskoepf |
| [oasst-sft-3-pythia-12b-epoch-3.5](https://huggingface.co/andreaskoepf/oasst-sft-3-pythia-12b-epoch-3.5) | 12b | pythia | andreaskoepf |
| [oasst-sft-3-pythia-12b-epoch-2.35](https://huggingface.co/andreaskoepf/oasst-sft-3-pythia-12b-epoch-2.35) | 12b | pythia | andreaskoepf |
| [oasst-sft-2-candidiate-0](https://huggingface.co/andreaskoepf/oasst-sft-2-candidiate-0) | unknown | unknown | andreaskoepf |
| [oasst-sft-2-pythia-12b-4000](https://huggingface.co/andreaskoepf/oasst-sft-2-pythia-12b-4000) | 12b | pythia | andreaskoepf |
| [oasst-sft-1-gpt-neox-2000](https://huggingface.co/andreaskoepf/oasst-sft-1-gpt-neox-2000) | unknown | gpt-neox | andreaskoepf |
| [oasst-1_12b_4500](https://huggingface.co/andreaskoepf/oasst-1_12b_4500) | 12b | unknown | andreaskoepf |
| [oasst-1_12b_1500](https://huggingface.co/andreaskoepf/oasst-1_12b_1500) | 12b | unknown | andreaskoepf |
| [oasst-1_12b_3000](https://huggingface.co/andreaskoepf/oasst-1_12b_3000) | 12b | unknown | andreaskoepf |

----

reward model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [reward-model-deberta-v3-large](https://huggingface.co/OpenAssistant/reward-model-deberta-v3-large) | unknown | deberta-v3 | OpenAssistant |
| [reward-model-deberta-v3-large-v2](https://huggingface.co/OpenAssistant/reward-model-deberta-v3-large-v2) | unknown | deberta-v3 | OpenAssistant |
| [reward-model-electra-large-discriminator](https://huggingface.co/OpenAssistant/reward-model-electra-large-discriminator) | unknown | electra-large | OpenAssistant |
| [reward-model-deberta-v3-base](https://huggingface.co/OpenAssistant/reward-model-deberta-v3-base) | unknown | deberta-v3 | OpenAssistant |
| [oasst-rm-1-pythia-1b](https://huggingface.co/andreaskoepf/oasst-rm-1-pythia-1b) | 1b | pythia | andreaskoepf |

### [openflamingo](https://github.com/mlfoundations/open_flamingo)

using [CLIP ViT-L](https://huggingface.co/openai/clip-vit-large-patch14) and [LLaMA-7B](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/), model weights on [huggingface](https://huggingface.co/openflamingo/OpenFlamingo-9B)

### [cerebras gpt](https://www.cerebras.net/blog/cerebras-gpt-a-family-of-open-compute-efficient-large-language-models/)

open sourced [model weights](https://huggingface.co/cerebras) and [training code](https://github.com/Cerebras/modelzoo)

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [cerebras-gpt-6.7b-lora](https://huggingface.co/samwit/cerebras-gpt-6.7b-lora) | 6.7b | cerebras-gpt | samwit |
| [Cerebras-GPT-2.7B-Alpaca-SP](https://huggingface.co/lxe/Cerebras-GPT-2.7B-Alpaca-SP) | 2.7b | cerebras-gpt | lxe |
| [Cerebras-GPT-2.7B-Alpaca-SP-ggml](https://huggingface.co/lxe/Cerebras-GPT-2.7B-Alpaca-SP-ggml) | 2.7b | cerebras-gpt | lxe |
| [lora-cerebras-gpt2.7b-alpaca-shortprompt](https://huggingface.co/lxe/lora-cerebras-gpt2.7b-alpaca-shortprompt) | 2.7b | cerebras-gpt | lxe |
| [Cerebras-GPT-13B](https://huggingface.co/cerebras/Cerebras-GPT-13B) | 13b | cerebras-gpt | cerebras |
| [Cerebras-GPT-6.7B](https://huggingface.co/cerebras/Cerebras-GPT-6.7B) | 6.7b | cerebras-gpt | cerebras |
| [Cerebras-GPT-2.7B](https://huggingface.co/cerebras/Cerebras-GPT-2.7B) | 2.7b | cerebras-gpt | cerebras |
| [Cerebras-GPT-1.3B](https://huggingface.co/cerebras/Cerebras-GPT-1.3B) | 1.3b | cerebras-gpt | cerebras |
| [Cerebras-GPT-590M](https://huggingface.co/cerebras/Cerebras-GPT-590M) | 590m | cerebras-gpt | cerebras |
| [Cerebras-GPT-256M](https://huggingface.co/cerebras/Cerebras-GPT-256M) | 256m | cerebras-gpt | cerebras |
| [Cerebras-GPT-111M](https://huggingface.co/cerebras/Cerebras-GPT-111M) | 111m | cerebras-gpt | cerebras |

### ColossalChat

[Coati-7B](https://github.com/orgs/hpcaitech/projects/17/views/1) has no public model weights, but claimed to be trained efficiently

you need to install [LLaMA compatible transformers library](https://github.com/hpcaitech/transformers)

train on [InstructionWild](https://github.com/XueFuzhao/InstructionWild)

## enhancements

### using external tools

[toolformer-pytorch](https://github.com/lucidrains/toolformer-pytorch) (WORK IN PROGRESS)


----

[engshell](https://github.com/emcf/engshell): using LLM to execute command

### using ai models

Microsoft [JARVIS](https://github.com/microsoft/JARVIS) aka [HuggingGPT](https://arxiv.org/abs/2303.17580) leverages huggingface models so ChatGPT can complete complex multimodal tasks.

### retrieval plugins

[long term memory](https://github.com/wawawario2/long_term_memory) for [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui) (can run pythia, galatica, opt, gpt-j, gpt-4chan, rwkv and support quantization/acceleration), also 
[complex memory](https://github.com/theubie/complex_memory) (KoboldAI-like)

----

[chatpaper](https://github.com/kaixindelele/ChatPaper) summarize paper content.

similar website: [typeset.io](https://typeset.io/) (can ask questions and explain confusing text, math symbols and tables)

related projects: [ChatReviewer](https://huggingface.co/spaces/ShiwenNi/ChatReviewer) [ChatImprovement](https://huggingface.co/spaces/wangrongsheng/ChatImprovement) [ChatResponse](https://huggingface.co/spaces/ShiwenNi/ChatResponse) [ChatGenTitle](https://github.com/WangRongsheng/ChatGenTitle)

----

[chatgpt retrieval plugin](https://github.com/openai/chatgpt-retrieval-plugin) chop document into chunks, process them into vectors and search them using one of many vector search backends. hosted as a fastapi service.

## datasets

### assistant dialogue

[botbots](https://github.com/radi-cho/botbots/) dataset (two chatgpt talking to each other), created by using [datasetGPT](https://github.com/radi-cho/datasetGPT) (LLM automation tool)

----

[ShareGPT52k](https://huggingface.co/datasets/RyokoAI/ShareGPT52K), also [ShareGPT90k](https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered) (Vicuna)

----

[instruct-102.4k](https://huggingface.co/datasets/swype/instruct-102.4k) by [swype](https://swype.com)

----

datasets by BELLE:

[train_1M_CN](https://huggingface.co/BelleGroup/train_1M_CN)

[train_0.5M_CN](https://huggingface.co/BelleGroup/train_0.5M_CN)

[multiturn_chat_0.8M](https://huggingface.co/BelleGroup/multiturn_chat_0.8M)

[school_math_0.25M](https://huggingface.co/BelleGroup/school_math_0.25M)

### unsupervised pretraining

[Fandom23K](https://huggingface.co/datasets/RyokoAI/Fandom23K) (text classification), part of [BigKnow2022](https://github.com/RyokoAI/BigKnow2022)

[Kinda LLaMA](https://github.com/yuxdux/kinda-llama) replicates LLaMA dataset, including scraped webpages, code and stackexchange data.

[oscar-corpus](https://huggingface.co/oscar-corpus) needs to be downloaded with access token, by accepting agreement with account. containing categorized content and adult content.

## dataset preprocessing

[deduplicate text dataset](https://github.com/google-research/deduplicate-text-datasets) in rust, may remove verbose substrings like "to go to the"

[oscar project](https://github.com/oscar-project) (Open Super-large Crawled Aggregated coRpus) contains some tool for adult content filtering and deduplication.

## NLP tools & training methods

[fasttext](https://fasttext.cc/docs/en/support.html) for efficient learning of word representations and sentence classification.

----

[langchain](https://docs.langchain.com/docs/)

[prompt-engine](https://github.com/microsoft/prompt-engine)

[chatml](https://github.com/openai/openai-python/blob/main/chatml.md): markup language for ChatGPT, by openai

[react-agent-ts](https://github.com/Intuitive-Systems/react-agent-ts) enables LLM to chat and use tools by internal dialogues.

[babyagi](https://github.com/yoheinakajima/babyagi): AI-powered task management system. original post on [twitter](https://twitter.com/yoheinakajima/status/1640934505048588290)

----

[Chain-of-hindsights](https://arxiv-vanity.com/papers/2302.02676) (can learn from negative feedback) in [jax](https://github.com/lhao499/CoH) and [pytorch](https://github.com/mukhal/CoH-pytorch)


## interfaces

[serge](https://github.com/nsarrazin/serge) is dockerized and the needs of RAM is according to the size of the model (alpaca), using CPU only
