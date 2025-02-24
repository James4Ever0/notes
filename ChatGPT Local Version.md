---
title: ChatGPT Local Version
created: '2023-04-02T13:28:19.395Z'
modified: '2023-04-02T13:28:22.797Z'
---

# ChatGPT Local Version
 
Run some community contributed ChatGPT-like models on commondity PCs.
 
android: https://github.com/a-ghorbani/pocketpal-ai

## Model Selection
 
Below are some models we are about to use:
 
- [ChatRWKV](https://github.com/BlinkDL/ChatRWKV), or [RWKV](https://github.com/BlinkDL/RWKV-LM)-based models, some are [fine-tuned on alpaca dataset](https://huggingface.co/spaces/Hazzzardous/RWKV-Instruct).
- [ChatGLM-6B](https://github.com/THUDM/ChatGLM-6B), open-sourced by Tsinghua KEG, with [INT4 quantized version](https://huggingface.co/silver/chatglm-6b-int4-slim).
- [OpenAssistant](https://huggingface.co/OpenAssistant) by LAION-AI, trained on their own [OIG dataset](https://huggingface.co/datasets/laion/OIG). There are also [few models](https://huggingface.co/Rallio67) contributed by their [discord community](https://ykilcher.com/open-assistant-discord).
- [Alpaca](https://github.com/tatsu-lab/standford_alpaca), trained on alpaca dataset (synthetic, generated by ChatGPT) by Standford University. Model weights are [community provided](https://github.com/antimatter15/alpaca.cpp).
- [ChatYuan](https://huggingface.co/ClueAI/ChatYuan-large-v1) by ClueAI.
 
There are quite a few more models to be listed. You can check [this curated open-sourced ChatGPT-like model list](https://github.com/nichtdax/awesome-totally-open-chatgpt) for updates. But for now, these models shall be sufficient.
 
## Quantization and Optimization
 
Floating-point values in model weights are stored as 32bit. Quantization can reduce storage space and computation by switching to 16bit, 8bit or 4bit values. However, most quantized models cannot be trained or fine-tuned, some 16bit models can only be trained on certain architecture of GPUs, such as Ada and Turing.
 
To make LLM (Large Language Model) inference feasible on common hardware, GPU is usually mandatory. However, most commondity GPUs have smaller VRAM compared to RAM, limiting the size of LLM to be run, thus the capability of the LLM. Most computer have 12GB of VRAM, 32GB of RAM. [GGML](https://github.com/ggerganov/ggml) is a project aiming to make LLM inference on CPU as fast as GPU, utilizing larger RAM compared to VRAM to run larger LLMs. Currently some popular LLMs have been ported to GGML, like [LLaMA](https://github.com/ggerganov/llama.cpp) and [Alpaca](https://github.com/antimatter15/alpaca.cpp).
 
## Training and Fine-tuning
 
In deeplearning, people tend to tune all parameters during training, requiring much VRAM and time. To train GPT3.5 aka ChatGPT, OpenAI spends millions to rent interconnected A100 GPUs. This is impossible for an individual to afford such.
 
With technologies like [LoRA](https://github.com/microsoft/LoRA), by freezing most part of the model and introducing a small fraction of tunable parameters, training requirements can be greatly reduced. One can easily tune [7B LLaMA](https://github.com/tolen/alpaca-lora) or [14B RWKV](https://github.com/Blealtan/RWKV-LM-LoRA) using LoRA on a PC (usually rented on the cloud, such as [AutoDL](www.autodl.com/home)) with a single 80GB A100 card and 200GB of RAM.
 
## Prompting and Chaining
 
LLMs are general problem solvers given enough external storage and access to search engines. Text is the only way to language models (not for multimodal LLMs, like [GPT4](https://openai.com/research/gpt-4), [OFA](https://github.com/OFA-Sys/OFA) or [UniLM](https://github.com/microsoft/unilm)).
 
To enhance the capability of LLMs, you have to [maintain its memory](https://langchain.readthedocs.io/en/latest/modules/memory/getting_started.html), [define action keywords and trigger external actions](https://langchain.readthedocs.io/en/latest/modules/agents.html) during the conversation, connect it to [semantic search engines](https://github.com/deepset-ai/haystack) powered by other AI models like [sentence transformers](https://www.sbert.net/).
 
One such library is [LangChain](https://langchain.readthedocs.io/en/latest/index.html).
 
## Serving as API
 
The process of generation for LLMs is sequential. Server needs to maintain a streaming API to match this behavior. Tokens are fetched one by one from the server with a constant speed, revealed in the frontend.
 
One can check third-party frontend-only or self-hosted projects for conversational LLMs for reference.
