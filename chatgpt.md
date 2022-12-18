---
title: chatgpt
created: '2022-12-06T07:37:08.000Z'
modified: '2022-12-18T19:33:56.172Z'
---

# chatgpt

this gpt seems really good. currently only api access.

## viable approaches to chatgpt

according to my point of view, chatgpt is just specialized on chat, or socialized in other words.

the elo rating system is the key to facebook social network, many zero-sum games. basically it is some revolution rating system. to do such rating system effectively one shall use along with classifiers and embeddings.

according to the training process of instructgpt and webgpt, we know that gpt has learned more by interacting with people (multiple QA), doing self-examination (learning a reward model) and performing actions (searching and quoting on web).

### RLHF

### GPT3-like models

### autonomous learning

[autonomous-learning-library](https://autonomous-learning-library.readthedocs.io/en/stable/)

[Gu-X](https://github.com/Gu-X) doing god-knows-what experiments

## analysis about how to make such model

gpt3 is capable of imitation (cause it is unsupervised.)

but! if you want to get things done (when you really need it!), you better want some aligned AI.

two similar models by openai: [webgpt](https://openai.com/blog/webgpt/#samples) and instructgpt

### about instructgpt

it is first fine-tuned on supervised datasets, then train some reward model, then use the reward model to handle prompts and do reinforcement learning with PPO.

### details on webgpt environment

guess: create states by performing actions, then generate templates to allow model filling blanks.
```
Our text-based web-browsing environment is written mostly in Python with some JavaScript. For a
high-level overview, see Section 2. Further details are as follows:

• When a search is performed, we send the query to the Microsoft Bing Web Search API, and
convert this to a simplified web page of results.

• When a link to a new page is clicked, we call a Node.js script that fetches the HTML of the
web page and simplifies it using Mozilla’s Readability.js.

• We remove any search results or links to reddit.com or quora.com, to prevent the model
copying answers from those sites.

• We take the simplified HTML and convert links to the special format
【<link ID>†<link text>†<destination domain>】, or
【<link ID>†<link text>】 if the destination and source domains are the same. Here,
the link ID is the index of the link on the page, which is also used for the link-clicking
command. We use special characters such as 【 and 】 because they are rare and encoded
in the same few ways by the tokenizer, and if they appear in the page text then we replace
them by similar alternatives.

• We convert superscripts and subscripts to text using ^ and _, and convert images to the
special format [Image: <alt text>], or [Image] if there is no alt text.

• We convert the remaining HTML to text using html2text.

• For text-based content types other than HTML, we use the raw text. For PDFs, we convert
them to text using pdfminer.six. For all other content types, and for errors and timeouts, we
use an error message.

• We censor any pages that contain a 10-gram overlap with the question (or reference answer,
if provided) to prevent the model from cheating, and use an error message instead.

• We convert the title of the page to text using the format <page title> (<page domain>).
For search results pages, we use Search results for: <query>.

• When a find in page or quote action is performed, we compare the text from the command
against the page text with any links stripped (i.e., including only the text from each link).
We also ignore case. For quoting, we also ignore whitespace, and allow the abbreviated
format <start text>━<end text> to save tokens.

• During browsing, the state of the browser is converted to text as shown in Figure 1(b).
For the answering phase (the last step of the episode), we convert the question to
text using the format <question>■, and follow this by each of the collected quotes
in the format [<quote number>] <quote page title> (<quote page domain>)
<double new line><quote extract>■.
```
## projects related to chatgpt

[chatgpt use cases curated list](https://github.com/jqueryscript/ChatGPT)

[DAILA](https://github.com/mahaloz/DAILA) use chatgpt 
to identify function calls in decompiler

[awesome transformer language models](https://github.com/cedrickchee/awesome-transformer-nlp/blob/f2dbb46a382a30dd3d23d88c1b8d826ba5c34aab/README.md) a huge collection on transformer based LMs, huge models by megacorps, with some introduction and analogy on chatgpt

[huggingface blog](https://github.com/huggingface/blog) on [RLHF](https://github.com/huggingface/blog/blob/dfbaec824b313f88581c761bc10c8943226970be/rlhf.md) containing similar projects and source code

bilibili sends me lots of videos (and articles) on hacking and ai (including chatgpt) via its android app. recommend you to scrape this source and collect transcription and screenshots for searching and content generation.

b站有做免杀 绕过杀软的

[chatgpt原理解析](https://bilibili.com/video/BV1B14y1K7AP)

chatgpt对接搜索引擎

下载链接:
github: https://github.com/josStorer/chat-gpt-search-engine-extension/releases/
百度网盘: https://pan.baidu.com/s/1MnFJTDIatyIIPr5kUMWsAw?pwd=1111 
提取码：1111

原项目: https://github.com/wong2/chat-gpt-google-extension
我创建的fork, 添加了多个搜索引擎支持的版本: https://github.com/josStorer/chat-gpt-search-engine-extension
PR: https://github.com/wong2/chat-gpt-google-extension/pull/31

已修复先前百度需要手动刷新的问题

## access via api

https://github.com/altryne/chatGPT-telegram-bot

https://github.com/taranjeet/chatgpt-api

https://github.com/acheong08/ChatGPT

https://github.com/vincelwt/chatgpt-mac

https://github.com/transitive-bullshit/chatgpt-api

https://github.com/rawandahmad698/PyChatGPT

## models like chatgpt

[lm-human-preferences](https://github.com/openai/lm-human-preferences) by openai

[trl](https://github.com/lvwerra/trl) Train transformer language models with reinforcement learning based on gpt2

[trix](https://github.com/CarperAI/trlx) A repo for distributed training of language models with Reinforcement Learning via Human Feedback (RLHF) by CarperAI

[RL4LMs](https://github.com/allenai/RL4LMs) A modular RL library to fine-tune language models to human preferences

[PaLM-rlhf-pytorch](https://github.com/lucidrains/PaLM-rlhf-pytorch) saying this is basically chatgpt with palm

[gpt-gmlp](https://github.com/lucidrains/g-mlp-gpt) saying this design integrates gpt with gmlps so will use less ram and can be trained on a single gpu

[WebGPT](https://github.com/James4Ever0/webgpt-cli)

[tk-instruct](https://github.com/yizhongw/Tk-Instruct) with [all models](https://huggingface.co/models?search=allenai/tk-instruct) by allenai can be [multilingual](https://huggingface.co/allenai/mtk-instruct-11b-def-pos), trained on [natural instructions](https://instructions.apps.allenai.org/)

there's a ghosted repo named [instructgpt-pytorch](https://github.com/mariusmcl/instructgpt-pytorch) found in bing but no cache preserved, also an empty repo called [InstructFNet](https://github.com/flippe3/InstructFNet) wtf?

[AidMe](https://github.com/nicolas-lair/AidMe) Code and experiment of the article AidMe User-in-the-loop Adaptative Intent Detecttion for Instructable Digital Assistant

[cheese](https://github.com/CarperAI/cheese) Used for adaptive human in the loop evaluation of language and embedding models.

[Kelpie](https://github.com/AndRossi/Kelpie) Explainable AI framework for interpreting Link Predictions on Knowledge Graphs

[GrIPS](https://github.com/archiki/GrIPS)  Gradient-free, Edit-based Instruction Search for Prompting Large Language Models

[queakily](https://github.com/CarperAI/squeakily) nlp datasets cleaner

gpt-j

super big bilingual model [GLM-130B](https://github.com/THUDM/GLM-130B)

[multi-modal deeplearning](https://github.com/JingfengYang/Multi-modal-Deep-Learning) paper collections

[bloom](https://huggingface.co/docs/transformers/model_doc/bloom) a huge model like gpt-3

notice, gpt-2 is somehow inferior to gpt-3 since it has smaller model parameters

[dialogue-generation](https://github.com/bme-chatbots/dialogue-generation) Generating responses with pretrained XLNet and GPT-2 in PyTorch.

[personaGPT](https://github.com/illidanlab/personaGPT) Implementation of PersonaGPT Dialog Model

[DialoGPT](https://github.com/microsoft/DialoGPT) Large-scale pretraining for dialogue
