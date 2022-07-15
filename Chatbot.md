---
title: Chatbot
created: '2022-07-14T14:19:56.000Z'
modified: '2022-07-15T12:43:06.613Z'
---

# Chatbot Self-hosted Model Cloud Deploy

could use this method to generate title for videos. i mean generally.

could host the model on huggingface, or baidu aistudio, heroku or your own machine

configure accelerated inference on huggingface (free for cpu, paid gpu):
https://huggingface.co/docs/api-inference/quicktour

huggingface inference apis:
https://huggingface.co/inference-api

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

paddlepaddle chat model:
paddlenlp
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
