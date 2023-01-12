---
tags: [chatbot, cloud, conversation, model zoo, pyjom, training data, 白嫖]
title: 'Chatbot, Self-hosted Model, Cloud Deploy, Cloud services, Free website hosting service'
created: '2022-07-14T14:19:56.000Z'
modified: '2023-01-12T22:28:54.016Z'
---

# Chatbot, Self-hosted Model, Cloud Deploy, Cloud services, Free website hosting service

[vercel](https://vercel.com/) hosts frontend only apps, could be useful if you want.

可以提取关键词然后到百度必应上面搜索 获取相关内容 注意语种一致性

search huggingface with julia or python:
huggingface_hub(python)

可以用huggingface的api来翻译 对接英文的chatbot (blenderbot, dialo-gpt)
add timeout to these api requests

可以把训练好的中文chatbot放到huggingface上面去 用kaggle放
https://github.com/yangjianxin1/GPT2-chitchat

could use this method to generate title for videos. i mean generally.

could host the model on huggingface, or baidu aistudio, heroku or your own machine

configure accelerated inference on huggingface (free for cpu, paid gpu):
https://huggingface.co/docs/api-inference/quicktour

huggingface inference apis:
https://huggingface.co/inference-api

huggingface conversational (chatbot) models:
https://huggingface.co/models?pipeline_tag=conversational&sort=downloads

heroku, use fastapi as interface:
https://fastapi.tiangolo.com
https://www.kaggle.com/getting-started/208405
https://signup.heroku.com

heroku alternatives:
back4app, google app engine

aistudio api, maybe you need to train or find a paddpepaddle based chatbot:
https://ai.baidu.com/ai-doc/AISTUDIO/bk3e382cq#创建在线api服务
一个项目可以创建至多五个沙盒服务, 并选择其中一个沙盒服务部署为线上服务.
沙盒服务如果连续超过24小时无调用将自动调整为暂停状态.
线上服务如果连续超过14天无调用将自动调整为暂停状态.

paddlenlp
https://aistudio.baidu.com/aistudio/projectdetail/3723144?channelType=0&channel=0

paddlepaddle chat model:
plato2
https://github.com/PaddlePaddle/Knover
https://github.com/PaddlePaddle/Knover/tree/develop/projects/PLATO-2
https://aistudio.baidu.com/aistudio/projectdetail/1886227?channelType=0&channel=0

中文chatbot:
https://github.com/zhaoyingjun/chatbot
https://github.com/Dimsmary/Ossas_ChatBot

教程
https://github.com/lcdevelop/ChatBotCourse
https://github.com/fendouai/Awesome-Chatbot

语料库
https://github.com/codemayq/chinese_chatbot_corpus
