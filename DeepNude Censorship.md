---
title: DeepNude Censorship
created: 2022-05-31T12:00:06+08:00
modified: 2022-07-14T00:05:21+08:00
---

# DeepNude Censorship NSFW

敏感词过滤器 also need a high speed censor engine using trie
https://github.com/gaohuifeng/sensitive-word-filter
https://github.com/lunzima/profanities.txt
https://github.com/nyx1987/forbiddenwords
https://github.com/insoxin/bannedwords
https://github.com/chason777777/mgck
https://github.com/k5h9999/keywordfilter
https://github.com/tomzhang/bannedwords
https://github.com/observerss/textfilter（需要回看历史 查看git历史）
https://github.com/aojiaotage/text-censor

deepnude nsfw nude picture detection:
https://github.com/yuanxiaosc/DeepNude-an-Image-to-Image-technology/blob/master/README-ZH.md

nsfw: not safe for work, inappropriate content, porn, offensive
https://github.com/rockyzhengwu/nsfw
https://github.com/alex000kim/nsfw_data_scraper
https://github.com/yahoo/open_nsfw

nudity, violence and drug
https://github.com/amshrbo/nsfw-detection

to train these networks, suitable datasets are required.
找训练集 找涉政 涉黄 暴力血腥图片训练集 找类似的文字训练集 百度aistudio可能有 github可能有 百度一下也可能有

同样的思路 情绪 情感打分也可以这样打分 根据不同的训练集进行打分

github violence detection:
https://github.com/topics/violence-detection

Bloody Image Classification with Global and Local Features
https://www.researchgate.net/publication/309365631_Bloody_Image_Classification_with_Global_and_Local_Features

Object content understanding in images and videos draws more and more attention nowadays. However, only few existing methods have addressed the problem of bloody scene detection in images. Along with the widespread popularity of the Internet, violent contents have affected our daily life. In this paper, we propose region-based techniques to identify a color image being bloody or not. Firstly, we have established a new dataset containing 25431 bloody images and 25431 non-bloody images. These annotated images are derived from the Violent Scenes Dataset, a public shared dataset for violent scenes detection in Hollywood movies and web videos. Secondly, we design a bloody image classification method with global visual features using Support Vector Machines. Thirdly, we also construct a novel bloody region identification approach using Convolutional Neural Networks. Finally, comparative experiments show that bloody image classification with local features is more effective.

search for nsfw filter providers on google/kaggle

kaggle nsfw image dataset
https://www.kaggle.com/datasets/laxmansingh/nsfw-images-data

search for nsfw image/text on github:
https://github.com/alex000kim/nsfw_data_scraper
https://github.com/nsfw-filter/nsfw-filter
nsfwjs
https://github.com/arufian/Image-Censor-Lightning-Web-Component
https://github.com/enymuss/censorText
https://github.com/fmsky/resnet50_inappropriate_content_detect
https://github.com/CheranMahalingam/Image_Content_Moderation

文本审核框架：
https://github.com/minitrill/TextAudit

规避文本审查：有可能是加密了 但是人眼可以识别
https://github.com/kallydev/shutup

nudenet based inappropriate image censoring

ocr based word censoring

politics
涉及政治：领导人 人脸识别 图标识别

violence 
血腥暴力：图像识别
