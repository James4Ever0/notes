---
tags: [anime, face landmark, facial, facial expression detection, image segmentation, pyjom, smile]
title: Anime smile detection_ segmentation
created: '2022-05-11T03:48:39.000Z'
modified: '2022-08-18T12:02:59.407Z'
---

# Anime smile detection/ segmentation

when an anime head is detected, cut it out and create dataset with labels. may augmented it with grayscale or edge detection.

segmentation using labeled data and train it on pretrained models. using anme head detection as double verification. no double heads.

ppse recognition may be applied without further training, or else.

我分析需要YOLO确定人物位置 CNN判断服装类型 人物性别 ocr识别字幕 音频分析识别语气 性别 音乐类型 再用seq2seq来把所有的输出概括成我的描述

或者看看有没有文字转关键词的模型

可以的话加上人物姿态估计 动漫人物的

关于光流算法：

熵就是梯度的标准差
一段范围的熵就是起始时间到末尾的熵的标准差
或者起始到末尾的梯度的标准差
