---
title: 'chatgpt clones, computer automation with ai'
created: '2023-04-02T10:39:51.304Z'
modified: '2023-04-02T16:06:19.277Z'
---

# chatgpt clones, computer automation with ai

simply because the original note on chatgpt is too long, we start a new one, with more topics and more resources.

convert arxiv paper (pdf) into html: [arxiv vanity](https://www.arxiv-vanity.com/) (you will have a better view than before, though [will not always work](https://www.arxiv-vanity.com/papers/2303.12712/)) code [on github](https://github.com/arxiv-vanity/arxiv-vanity)

someone prefers [bert4keras](https://github.com/bojone/bert4keras) since it implements multiple LLM into Keras, also easy for GPT-2 LoRA training (by adding a single layer)

## computer automation with ai

### papers

[playing atari using q-learning](https://www.arxiv-vanity.com/papers/1312.5602/) (viewing deepmind paper with arxiv vanity)

### models

[video pretraining](https://openai.com/research/vpt) can perform minecraft diamond mining tasks with keyboard and mouse movements

[code and model](https://github.com/openai/Video-Pre-Training)

### spaces

openai [universe]() (blog post [here]()) and [starter agents]()

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

### [dolly](https://github.com/databrickslabs/dolly)

model arch is gpt-j, trained on alpaca dataset

model weights of [dolly-v1-6b](https://huggingface.co/databricks/dolly-v1-6b)

### [alpaca]()

alpaca is LLaMA tuned on ChatGPT self-instruct dataset. officially there is just code and dataset, model weights are community provided.

### [togethercomputer]()

released chat models like [gpt-xt](https://huggingface.co/togethercomputer/GPT-NeoXT-Chat-Base-20B) and [pythia](https://huggingface.co/togethercomputer/Pythia-Chat-Base-7B), [moderation model](https://huggingface.co/togethercomputer/GPT-JT-Moderation-6B) using gpt-jt

[openchatkit](https://github.com/togethercomputer/OpenChatKit) with retrieval ability and [its huggingface space](https://huggingface.co/spaces/togethercomputer/OpenChatKit)

### RWKV

now we have [rwkv.cpp](https://github.com/saharNooby/rwkv.cpp), build upon ggml and sure it works on cpu.

### [gpt4all](https://github.com/nomic-ai/gpt4all) by nomic

LLaMA trained on massive collection of clean assistant dialog data, with model weights

you need to install nomic to run the model:

```bash
pip3 install nomic
```

to run it on gpu, you need to install [this](https://github.com/nomic-ai/nomic/tree/main/bin)

### openassistant

researchers of open-assistant like [andreaskoepf](https://huggingface.co/andreaskoepf) has releasesed [oasst-sft-3-pythia-12b-epoch-3.5](https://huggingface.co/andreaskoepf/oasst-sft-3-pythia-12b-epoch-3.5) and still updating

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

### retrieval plugins

[long term memory](https://github.com/wawawario2/long_term_memory) for [oobabooga/text-generation-webui](https://github.com/oobabooga/text-generation-webui) (can run pythia, galatica, opt, gpt-j, gpt-4chan, rwkv and support quantization/acceleration)

[chatpaper](https://github.com/kaixindelele/ChatPaper) summarize paper content.

similar website: [typeset.io](https://typeset.io/) (can ask questions and explain confusing text, math symbols and tables)

related projects: [ChatReviewer](https://huggingface.co/spaces/ShiwenNi/ChatReviewer) [ChatImprovement](https://huggingface.co/spaces/wangrongsheng/ChatImprovement) [ChatResponse](https://huggingface.co/spaces/ShiwenNi/ChatResponse) [ChatGenTitle](https://github.com/WangRongsheng/ChatGenTitle)

## datasets

### assistant dialogue

[botbots](https://github.com/radi-cho/botbots/) dataset (two chatgpt talking to each other), created by using [datasetGPT](https://github.com/radi-cho/datasetGPT) (LLM automation tool)

[ShareGPT52k](https://huggingface.co/datasets/RyokoAI/ShareGPT52K), also [ShareGPT90k](https://huggingface.co/datasets/anon8231489123/ShareGPT_Vicuna_unfiltered) (Vicuna)

### unsupervised pretraining

[Fandom23K](https://huggingface.co/datasets/RyokoAI/Fandom23K) (text classification), part of BigKnow2022

## dataset preprocessing

[deduplicate text dataset](https://github.com/google-research/deduplicate-text-datasets) in rust, may remove verbose substrings like "to go to the" 

## interfaces

[serge](https://github.com/nsarrazin/serge) is dockerized and the needs of RAM is according to the size of the model (alpaca), using CPU only




