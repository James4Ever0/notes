---
title: 'chatgpt clones, computer automation with ai'
created: '2023-04-02T10:39:51.304Z'
modified: '2023-04-02T16:06:19.277Z'
---

# chatgpt clones, computer automation with ai

simply because the original note on chatgpt is too long, we start a new one, with more topics and more resources.

----

javascript code for extracting model list from huggingface personal homepage:

```javascript
for (var i of document.getElementsByTagName("h4")) {var t = i.innerText; }
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

### papers

[playing atari using q-learning](https://www.arxiv-vanity.com/papers/1312.5602/) (viewing deepmind paper with arxiv vanity)

### models

[video pretraining](https://openai.com/research/vpt) can perform minecraft diamond mining tasks with keyboard and mouse movements

[code and model](https://github.com/openai/Video-Pre-Training)

### data collectors and controllers

[mss](https://python-mss.readthedocs.io/) for screenshot, remember to save raw pixels to SSD, then compress with mp4 for further training. (increase learning experience)

[]()

----

[ViT-pytorch](https://github.com/lucidrains/vit-pytorch) can be used in many ViT-based models, listed and implemented in the repo.

### spaces

openai [universe](https://github.com/openai/universe) (blog post [here](https://openai.com/blog/universe/)) and [starter agents](https://github.com/openai/universe-starter-agent), remotes are using vnc protocol and a reward protocol using websocket sending json (can send actions). they prefer [TigerVNC](https://tigervnc.org/), maybe that will send the existing monitor instead of invisible ones.

## accelerators

### [cformer](https://github.com/NolanoOrg/cformers/)

cpu only

able to install from pip

### [ggml](https://github.com/ggerganov/ggml)

cpu only

cpp, only compile from source

### [flexgen](https://github.com/FMInference/FlexGen)

gpu is mandatory, better than deepspeed and [Hugging Face Accelerate](https://github.com/huggingface/accelerate)

## open source model and weights

[awesome decentralized llm](https://github.com/imaurer/awesome-decentralized-llm) listed up-to-date related chatgpt-like repositories, datasets, model weights and resources.

### [ChatYuan]()

### [ChatGLM]()

Currently only open-sourced 6B version.

### [ChatDoctor](https://huggingface.co/zl111/ChatDoctor)

[LLaMA-65B](https://huggingface.co/datasets/nyanko7/LLaMA-65B) trained on medical dataset [InstructorDoctor-200k](https://drive.google.com/file/d/1lyfqIwlLSClhgrCutWuEe_IACNq6XNUt/view?usp=sharing)

### [dolly](https://github.com/databrickslabs/dolly)

model arch is gpt-j, trained on alpaca dataset

model weights of [dolly-v1-6b](https://huggingface.co/databricks/dolly-v1-6b)

### [FastChat](https://github.com/lm-sys/FastChat) (Vicuna)

[web interface](https://chat.lmsys.org/)

----

community model weights:

| weight path | model name | author |
| -- | -- | -- |
| [vicuna](https://huggingface.co/chavinlo/vicuna) | Vicuna | chavinlo |
| [vicuna2](https://huggingface.co/chavinlo/vicuna2) | Vicuna | chavinlo |

### Bloom-z

there is [bloomz.cpp](https://github.com/NouamaneTazi/bloomz.cpp), converted model weights on [huggingface](https://huggingface.co/models?other=bloom&other=ggml)

### [Alpaca](https://github.com/tatsu-lab/stanford_alpaca)

alpaca is LLaMA tuned on ChatGPT self-instruct dataset. officially there is just code and dataset, model weights are community provided.

ggml version: [alpaca.cpp](https://github.com/antimatter15/alpaca.cpp)

it's better to check for [python bindings](https://github.com/abetlen/llama-cpp-python) and [webui](https://github.com/abdeladim-s/pyllamacpp) like [Alpaca-Turbo](https://github.com/ViperX7/Alpaca-Turbo) for further development and interactions.

----

fine-tuning:

[simple-llama-finetuner](https://github.com/lxe/simple-llama-finetuner) using LoRA, 16GB VRAM minimum

[alpaca-lora](https://github.com/tloen/alpaca-lora): the OG LoRA alpaca

----

community model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [Alpaca Native](https://huggingface.co/chavinlo/alpaca-native) | 7B | Alpaca | chavinlo |
| [Alpaca-65B](https://huggingface.co/chavinlo/Alpaca-65B) | 65B | Alpaca | chavinlo |
| [Alpaca 13B](https://huggingface.co/chavinlo/alpaca-13b) | 13B | Alpaca | chavinlo | 
| [GPT4-X-Alpaca](https://huggingface.co/chavinlo/gpt4-x-alpaca) | 13B | Alpaca | chavinlo |
| [Toolpaca](https://huggingface.co/chavinlo/toolpaca) | 13B | Alpaca | chavinlo |
| [instruct-gpt-j-fp16](https://huggingface.co/nlpcloud/instruct-gpt-j-fp16) | 6B | GPT-J | nlpcloud |

----

[codealpaca](https://github.com/sahil280114/codealpaca) only provides [dataset](https://huggingface.co/datasets/sahil2801/CodeAlpaca-20k) for training a code generation model, there are multiple models trained on this dataset, including [bloom-7b1-lora-codealpaca20k](https://huggingface.co/LinhDuong/bloom-7b1-lora-codealpaca20k)

### [togethercomputer](https://huggingface.co/togethercomputer)

released chat models like [gpt-xt](https://huggingface.co/togethercomputer/GPT-NeoXT-Chat-Base-20B) and [pythia](https://huggingface.co/togethercomputer/Pythia-Chat-Base-7B), [moderation model](https://huggingface.co/togethercomputer/GPT-JT-Moderation-6B) using gpt-jt

[openchatkit](https://github.com/togethercomputer/OpenChatKit) with retrieval ability and [its huggingface space](https://huggingface.co/spaces/togethercomputer/OpenChatKit)

### RWKV

RWKV combines attention with RNN so the token window can be much larger.

[Longformer](https://huggingface.co/docs/transformers/model_doc/led) is similar to this. Model weights in [github repo](https://github.com/allenai/longformer) or [huggingface](https://huggingface.co/allenai/longformer-base-4096).

----

now we have [rwkv.cpp](https://github.com/saharNooby/rwkv.cpp), build upon ggml and sure it works on cpu.

### [gpt4all](https://github.com/nomic-ai/gpt4all) by nomic

LLaMA trained on massive collection of clean assistant dialog data, with model weights

you need to install nomic to run the model:

```bash
pip3 install nomic
```

to run it on gpu, you need to install [this](https://github.com/nomic-ai/nomic/tree/main/bin)

### [openassistant]()

researchers of open-assistant like [andreaskoepf](https://huggingface.co/andreaskoepf) has releasesed [oasst-sft-3-pythia-12b-epoch-3.5](https://huggingface.co/andreaskoepf/oasst-sft-3-pythia-12b-epoch-3.5) and still updating

----

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [oasst-llama-13b-2-epochs](https://huggingface.co/dvruette/oasst-llama-13b-2-epochs) | 13B | LLaMA | dvruette |
|  |  |  |  |
|  |  |  |  |

### [openflamingo](https://github.com/mlfoundations/open_flamingo)

using [CLIP ViT-L](https://huggingface.co/openai/clip-vit-large-patch14) and [LLaMA-7B](https://ai.facebook.com/blog/large-language-model-llama-meta-ai/), model weights on [huggingface](https://huggingface.co/openflamingo/OpenFlamingo-9B)

### [cerebras gpt](https://www.cerebras.net/blog/cerebras-gpt-a-family-of-open-compute-efficient-large-language-models/)

open sourced [model weights](https://huggingface.co/cerebras) and [training code](https://github.com/Cerebras/modelzoo)

### ColossalChat

[Coati-7B](https://github.com/orgs/hpcaitech/projects/17/views/1) has no public model weights, but claimed to be trained efficiently

you need to install [LLaMA compatible transformers library](https://github.com/hpcaitech/transformers)

train on [InstructionWild](https://github.com/XueFuzhao/InstructionWild)

## enhancements

### using external tools

[toolformer-pytorch](https://github.com/lucidrains/toolformer-pytorch) (WORK IN PROGRESS)

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

[ShareGPT52k](https://huggingface.co/datasets/RyokoAI/ShareGPT52K), also [ShareGPT90k](https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered) (Vicuna)

### unsupervised pretraining

[Fandom23K](https://huggingface.co/datasets/RyokoAI/Fandom23K) (text classification), part of BigKnow2022

[Kinda LLaMA](https://github.com/yuxdux/kinda-llama) replicates LLaMA dataset, including scraped webpages, code and stackexchange data.

[oscar-corpus](https://huggingface.co/oscar-corpus) needs to be downloaded with access token, by accepting agreement with account. containing categorized content and adult content.

## dataset preprocessing

[deduplicate text dataset](https://github.com/google-research/deduplicate-text-datasets) in rust, may remove verbose substrings like "to go to the"

[oscar project](https://github.com/oscar-project) (Open Super-large Crawled Aggregated coRpus) contains some tool for adult content filtering and deduplication.

## interfaces

[serge](https://github.com/nsarrazin/serge) is dockerized and the needs of RAM is according to the size of the model (alpaca), using CPU only




