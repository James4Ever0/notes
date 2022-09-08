---
tags: [paraphraser, rephrase, text generation, translator, 洗稿]
title: Translators for Casual usage
created: '2022-04-29T15:03:52.000Z'
modified: '2022-09-08T14:31:02.808Z'
---

# Translators/Paraphraser for casual usage

[baidu translator](https://github.com/PaddlePaddle/PaddleHub/blob/e03d11260b86a2f49f896e733d68e82edb0d9286/modules/text/machine_translation/baidu_translate/module.py) (api) provided by paddlehub

[baidu language detector](https://github.com/PaddlePaddle/PaddleHub/blob/37fd44e8000e19a61d74cc35ef08af2cdd3d64b4/modules/text/machine_translation/baidu_language_recognition/module.py) (api)

text style transfer:

https://blog.csdn.net/qq_27590277/article/details/106991084

python google translate api:
pip install googletrans

google translate in php:
https://github.com/Stichoza/google-translate-php

paraphrase via rephrasing and reordering

pegasus paraphrase:

increase the num_beams and temperature
https://analyticsindiamag.com/how-to-paraphrase-text-using-pegasus-transformer/

https://www.thepythoncode.com/article/paraphrase-text-using-transformers-in-python

example paraphrase project using LSTM as decoder and encoder:

https://github.com/vsuthichai/paraphraser

paraphrase with t5:

https://github.com/Vamsi995/Paraphrase-Generator

paraphrase dataset:

https://github.com/Wys997/Chinese-Paraphrase-from-Quora

文本纠错
https://github.com/James4Ever0/pycorrector

数据增强 变换句子形式
https://yongzhuo.blog.csdn.net/article/details/89166307
https://github.com/zhanlaoban/eda_nlp_for_Chinese

calculate perplexity:

https://github.com/DUTANGx/Chinese-BERT-as-language-model
https://github.com/James4Ever0/nlp-fluency
https://zhuanlan.zhihu.com/p/265677864
https://github.com/mattzheng/py-kenlm-model

multi-purpose tool for chinese: 偏旁部首 情感分析
https://github.com/SeanLee97/xmnlp

敏感词过滤 语言检测 训练语料库
https://github.com/fighting41love/funNLP


paraphraser.io

multilingual paraphrase database:

paraphrase.org

simbert

https://www.zhihu.com/question/317540171

BERT：原始版本bertRoberta：哈工大开源的中文wwm roberta模型BERT-SQ：本人在百度知道相似句数据集(Sim-Query)上微调后的bert模型Roberta-SQ：同上BERT-Whitening： @苏剑林 最新博客中提出的白化模型。Roberta-Whitening：同上


https://yongzhuo.blog.csdn.net/article/details/89166307

language fluency test:

https://github.com/baojunshan/nlp-fluency

many paraphraser models for english are on huggingface, but few for chinese.

https://huggingface.co/lijingxin/mt5-for-zh-paraphrase
https://pypi.org/project/genienlp/
https://github.com/salesforce/decaNLP

parrot paraphraser with nlu engines for english:
https://github.com/PrithivirajDamodaran/Parrot_Paraphraser

sentence level paraphraser:
https://github.com/vsuthichai/paraphraser

document level paraphraser, with sentence rewriting and reordering(shuffle):
https://github.com/L-Zhe/CoRPG

https://pypi.org/project/lexsub/
https://github.com/hit-joseph/lexical-paraphrase-extraction
synonyms (python library)

you can also train a contextual search tool using fine-tuned repurposed paraphrase model.

https://pypi.org/project/nlp-text-search/

文言文
https://github.com/raynardj/yuan

粤语
https://huggingface.co/x-tech

huggingface有英语翻译到其他语言的模型 没有翻译成中文的模型

在线
https://github.com/nidhaloff/deep-translator
https://github.com/UlionTse/translators
translatepy

离线
https://huggingface.co/tasks/translation
https://huggingface.co/Helsinki-NLP/opus-mt-zh-en
https://github.com/argosopentech/argos-translate
libretranslate
https://github.com/Teuze/translate
https://github.com/xhlulu/dl-translate/
facebook/mbart-large-50-many-to-many-mmt
mbart50
m2m100

view under https://huggingface.co/tasks to see great models fitting exact needs.
