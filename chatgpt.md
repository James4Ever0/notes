---
title: chatgpt
created: '2022-12-06T07:37:08.000Z'
modified: '2023-03-15T23:50:16.926Z'
---

# chatgpt

GPT4 is out.

---

[三个国内镜像站](https://www.ooopn.com/tool/chatgpt/)：

https://chat.forchange.cn
https://aigcfun.com
https://ai.askai.top

---

besides from decent processors, RAM and optimized runtime, in order to load LLMs fast, one would store the model weights on SSDs.

----

now [colossalai](https://github.com/hpcaitech/ColossalAI) supports chatgpt training with a single gpu, using open-source code

check [humata](https://app.humata.ai) for paper QA and information extraction/language understanding from PDF files

----

the syntax of chatgpt's response is obviously markdown.

in order to be unblocked by chatgpt just because we are using static ip of corp's wifi, we can connect through our phone's hotspot.

Microsoft's [EdgeGPT](https://bing.com/chat) needs you to open in Edge browser and join the waitlist of [new Bing](https://bing.com/new), having 3rd party API [here](https://github.com/acheong08/EdgeGPT)

[Merlin](http://getmerlin.in/) is an extension based on ChatGPT which is avaliable for free and all countries, with 11 queries for free each day. Pro subscriptions incoming.

Rallio67 builds [dataset for RLHF](https://github.com/Rallio67/language-model-agents) and has released [multiple chatgpt-like models](https://huggingface.co/Rallio67) on huggingface. namely, [joi](https://huggingface.co/Rallio67/joi_20B_instruct_alpha), [chip](https://huggingface.co/Rallio67/chip_20B_instruct_alpha) and [rosey](https://huggingface.co/Rallio67/rosey_12B_instruct_alpha), all based on [pythia](https://huggingface.co/EleutherAI/pythia-12b) or neox-20b. laion people tend to share loads to CPU in order to run these huge models properly.

[KoboldAI](https://github.com/KoboldAI/KoboldAI-Client) considered [OPT](https://huggingface.co/facebook/opt-2.7b) and [GPT-Neo](https://huggingface.co/EleutherAI/gpt-neo-2.7B) as generic LMs. special models like NSFW shits may serve some purposes better.

[many alternatives](https://alternativeto.net/software/chatgpt/), but many are specialized in marketing and content generation, some are chatgpt replica, like [chatsonic](https://app.writesonic.com/) (with google knowledge) and [youchat](https://you.com/search?q=who+are+you&fromSearchBar=true&tbm=youchat) (from [you.com](https://you.com/) (awesome!))

open assistant now has a [data collection website](https://open-assistant.io/dashboard), in which you can only perform tasks given and earn points (working for free? nah?)

it is adviced to run this chatgpt program with libraries instead of manually, to prevent issues.

my account has been banned from trying chatgpt. though it is not going to be free forever, you need to [moderate your input](https://github.com/golfzert/chatgpt-chinese-prompt-hack) (multi-language support, not only english but chinese) using some api to prevent similar incidents. also some topics outside of blacklist are banned intentionally so you need to check if the model is really producing the answer. if not you should avoid or change the way of asking it.

moderation via [official openai api](https://platform.openai.com/docs/api-reference/moderations), [perspective api](https://developers.perspectiveapi.com/s/?language=en_US) (free), or via some projects like [content moderation deeplearning](https://github.com/fcakyon/content-moderation-deep-learning), [bert text moderation](https://github.com/NanoNets/bert-text-moderation), [bert-base-uncased-hatexplain](https://huggingface.co/Hate-speech-CNERG/bert-base-uncased-hatexplain), [toxic-bert](https://huggingface.co/unitary/toxic-bert), [copilot-toxicity](https://github.com/surge-ai/copilot-toxicity/blob/main/copilot-toxicity.ipynb) and [multilingual-hate-speech-robacofi](https://huggingface.co/Andrazp/multilingual-hate-speech-robacofi), train on datasets like [hate_speech_offensive](https://huggingface.co/datasets/SetFit/hate_speech_offensive), [toxicity](https://github.com/surge-ai/toxicity) (by surge-ai, a dataset labelling workforce) and [multilingual-hate-speech](https://huggingface.co/datasets/vidhur2k/multilingual-hate-speech/)

from my point of view, this is a service you cannot replicate at home, either requires smaller models with different architecture, or requires crowd-sourced computational power.

saying chatgpt is powered by [ray](https://www.ray.io), increasing parallelism.

bigscience [petals colab](https://colab.research.google.com/drive/1Ervk6HPNS6AYVr3xVdQnY5a-TjjmLCdQ?usp=sharing#scrollTo=VsXHWJLuowcn) and [petals repo](https://github.com/bigscience-workshop/petals)

[discord chatroom](https://discord.gg/xBPBXfcFHd) for reproducing chatgpt

since many different models are derived from the original pretrained language model, [opendelta](https://opendelta.readthedocs.io/en/latest/) can save disk space by freezing main parameters, only tuning few of them.

this gpt seems really good. currently only api access.

but it is provided by openai which is no longer so "open" in the sense of "open-source".

[stability.ai](https://stability.ai/) is providing alternative open-source implementations of SOTA AI algorithms, which includes [carper.ai](https://carper.ai/), [eleuther.ai](https://www.eleuther.ai/), dreamstudio, [harmonai](https://github.com/Harmonai-org/) (audio), [laion.ai](https://laion.ai) (datasets and projects)

## viable approaches to chatgpt

according to my point of view, chatgpt is just specialized on chat, or socialized in other words.

the elo rating system is the key to facebook social network, many zero-sum games. basically it is some revolution rating system. to do such rating system effectively one shall use along with classifiers and embeddings.

according to the training process of instructgpt and webgpt, we know that gpt has learned more by interacting with people (multiple QA), doing self-examination (learning a reward model) and performing actions (searching and quoting on web).

### RLHF

#### chainer, prompt engineering

[awesome chatgpt prompts](https://github.com/f/awesome-chatgpt-prompts)

[langchain](https://langchain.readthedocs.io/) extending llm by advanced prompts, llm wrappers actions, databases and memories

#### RL algorithms, tools for providing feedback

[Awesome-RLHF](https://github.com/andy-yangz/Awesome-RLHF) paper and code about RLHF

[openai baselines](https://github.com/openai/baselines)

[stable-baselines 3](https://github.com/DLR-RM/stable-baselines3)

[SetFit](https://huggingface.co/blog/setfit) 
Efficient few-shot learning with Sentence Transformers, used by [FewShotRLGPT](https://github.com/grantCelley/FewShotRLGPT) (no updates till now?)

#### RLHF models

##### non-language models

[image_to_text_rlhf](https://github.com/anshradh/image_to_text_rlhf)

[algorithm-distillation-rlhf](https://github.com/CarperAI/Algorithm-Distillation-RLHF)

##### language models

[chatrwkv](https://github.com/BlinkDL/ChatRWKV) pure rnn language model, with chinese support

[lamda-rlhf-chatgpt](https://github.com/conceptofmind/LaMDA-rlhf-pytorch)

[blenderbot2](https://huggingface.co/facebook/blenderbot-3B) a bot which can search internet, blenderbot3 is US only. install [ParlAI](https://github.com/facebookresearch/ParlAI) then clone [ParlAI_SearchEngine](https://github.com/JulesGM/ParlAI_SearchEngine). [tutorial](https://dev.to/naruaika/how-i-managed-to-run-blenderbot-20-1jac)

[promptCLUE](https://github.com/clue-ai/PromptCLUE) based on T5, created by [clueai](https://www.clueai.cn/doc), trained on [pCLUE](https://github.com/CLUEbenchmark/pCLUE)

[openassistant](https://github.com/LAION-AI/Open-Assistant)

[openchatgpt-neox-125m](https://huggingface.co/mrsteyk/openchatgpt-neox-125m) trained on chatgpt prompts, can be tested [here](https://huggingface.co/spaces/mrsteyk/mrsteyk-openchatgpt-neox-125m), trained from [pythia](https://huggingface.co/EleutherAI/pythia-6.7b-deduped)

[copycat](https://github.com/theblackcat102/copycat) chatgpt replicate

[medicine-chatgpt](https://github.com/lucidrains/medical-chatgpt) shit sick of COVID-19

[baby-rlhf](https://www.github.com/jordan-schneider/baby-rlhf/) both cartpole and languge model

[rlhf-shapespeare](https://github.com/ckkissane/rlhf-shakespeare)

[textrl](https://github.com/voidful/TextRL) 100+stars

[PaLM-RLHF](https://github.com/lucidrains/PaLM-rlhf-pytorch) claims [RETRO](https://github.com/lucidrains/RETRO-pytorch) will be integrated soon?

[RL4LMs](https://github.com/allenai/RL4LMs) with multiple rl methods

[minRLHF](https://github.com/thomfoster/minRLHF)

[webgpt-cli](https://github.com/mukulpatnaik/webgpt-cli/blob/main/webgpt.py) interface openai api to browse web and answer questions

[lm-human-preferences](https://github.com/openai/lm-human-preferences) by openai

[rlhf-magic](https://github.com/TheExGenesis/rlhf-magic) using [trlx](https://github.com/CarperAI/trlx) (supports GPT3-like models) which has PPO and [ILQL](https://github.com/Sea-Snell/Implicit-Language-Q-Learning) (as trainable model)

[trl](https://github.com/lvwerra/trl) only has PPO on GPT2

[Tk-Instruct](https://github.com/yizhongw/Tk-Instruct) T5 trained on natural instruct dataset. is it trained on RLHF systems?

### datasets

[whisperhub](https://rootsignals.ai/W/all) collection of chatgpt prompts by plugin

[hh-rlhf](https://github.com/anthropics/hh-rlhf)

[instructgpt samples](https://github.com/openai/following-instructions-human-feedback)

[natural instructions](https://github.com/allenai/natural-instructions)

### dataset building tools

[open-chatgpt-prompt-collective](https://github.com/SurfaceData/open-chatgpt-prompt-collective)

[crowd-kit](https://github.com/Toloka/crowd-kit) purify noisy data

[promptsource](https://github.com/bigscience-workshop/promptsource)

### reward models

[rankgen](https://github.com/martiansideofthemoon/rankgen) scores model generations given a prefix (or prompt)

[electra-webgpt-rm](https://huggingface.co/theblackcat102/electra-large-webgpt-rm) and [electra-large-reward-model](https://huggingface.co/theblackcat102/electra-large-reward-model) is based on [electra](https://huggingface.co/google/electra-small-discriminator) discriminator

### GPT3-like models

[galactica](https://huggingface.co/facebook/galactica-1.3b) is opt trained on scientific data

[bloomz](https://huggingface.co/bigscience/bloomz) and [mt0](https://huggingface.co/bigscience/mt0-large) trained on [xP3](https://huggingface.co/datasets/bigscience/xP3) (multilingual prompts and code)

[T0PP](https://huggingface.co/bigscience/T0pp) T0 optimized for zero-shot prompts, despite much smaller than GPT-3

[RETRO](https://github.com/lucidrains/RETRO-pytorch) another model with GPT-3 capabilities with fewer parameters? 

gpt3 is gpt2 with [sparse attension](https://github.com/openai/sparse_attention), which enables it to generate long sequence

[Diffusion-LM](https://github.com/XiangLi1999/Diffusion-LM)

[PaLM](https://github.com/lucidrains/PaLM-pytorch)

[metaseq](https://github.com/facebookresearch/metaseq) provides OPT, which is basically GPT3

[GPT-JT](https://huggingface.co/togethercomputer/GPT-JT-6B-v1) altered in many ways, trained on natural instructions [huggingface space](https://huggingface.co/spaces/togethercomputer/GPT-JT)

[GPT-Neo](https://huggingface.co/EleutherAI/gpt-neo-125M)

[GPT-J](https://huggingface.co/docs/transformers/model_doc/gptj)

[GPT-NeoX](https://github.com/EleutherAI/gpt-neox)

[Bloom](https://huggingface.co/bigscience/bloom) large language model by bigscience

### autonomous learning

[autonomous-learning-library doc](https://autonomous-learning-library.readthedocs.io/en/stable/) and [repo](https://github.com/cpnota/autonomous-learning-library)

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

### voice assistants

[voice assistant](https://github.com/tiansztiansz/voice-assistant) in cpp

[ChatWaifu](https://github.com/cjyaddone/ChatWaifu) with anime voice, [ChatWaifu with live2d](https://github.com/cjyaddone/ChatWaifuL2D)

### hacking

[give longterm memory and external resources to gpt3](https://github.com/daveshap/LongtermChatExternalSources)

[write backend logic with gpt](https://github.com/TheAppleTucker/backend-GPT)

[hackgpt](https://github.com/NoDataFound/hackGPT) exploit vulnerabilities

[vulchatgpt](https://github.com/ke0z/VulChatGPT) ida plugin for reverse engineering

[chatgpt-universe](https://github.com/cedrickchee/chatgpt-universe) things related to chatgpt

[galgame using chatgpt](https://www.bilibili.com/video/BV1Gv4y1z7tN/)

记笔记
12.27更新了一个更精简的应用
强烈建议部署到服务器上
huggingface参考：https://huggingface.co/spaces/Mahiruoshi/Lovelive-Nijigasaku-Chat-iSTFT-GPT3
GitHub：https://github.com/Paraworks/vits_with_chatgpt-gpt3
地址：https://drive.google.com/drive/folders/1vtootVMQ7wTOQwd15nJe6akzJUYNOw4d?usp=share_link
你可以先尝试在服务器上部署，之后可以直接解压进文件夹后运行exe（mac、安卓端需要用renpy自行编译）
去https://beta.openai.com/account/api-keys获取api-key
参数照着敲就好了
人物id通常是从0开始的数字，我的模型最大到12
api部署方法：把inference_api.py放入你的vits目录下，进入文件修改config和checkpoint.pth的路径，比起应用程序来说十分简单，可以自行设计。码龄三个月写出的的雪山代码警告
——————————————————————————————————————————————————
Chatgpt部署方法已于12.26更新（视频后部分）
vits参考：https://github.com/CjangCjengh/vits
服务器端建议用ISTFT VITS：https://github.com/innnky/MB-iSTFT-VITS
model库：https://github.com/CjangCjengh/TTSModels
也可以用我的https://huggingface.co/spaces/Mahiruoshi/MIT-VITS-Nijigaku
CHATGPT参考：https://github.com/rawandahmad698/PyChatGPT
示例视频（纯服务器api，gpt3）https://www.bilibili.com/video/BV1hP4y1B7wH/?spm_id_from=333.999.0.0&vd_source=7e8cf9f5c840ec4789ccb5657b2f0512
穗乃果配音来自缪斯的模型﻿@Freeze_Phoenix
gpt3加载参考﻿@ぶらぶら散策中

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

[lfqa](https://yjernite.github.io/lfqa.html) retrival based generative QA

[lm-human-preferences](https://github.com/openai/lm-human-preferences) by openai

[trl](https://github.com/lvwerra/trl) Train transformer language models with reinforcement learning based on gpt2

[trlx](https://github.com/CarperAI/trlx) A repo for distributed training of language models with Reinforcement Learning via Human Feedback (RLHF) by CarperAI

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
