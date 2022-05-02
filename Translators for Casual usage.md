---
created: 2022-04-29T23:03:52+08:00
modified: 2022-05-02T17:52:27+08:00
---

# Translators/Paraphraser for casual usage

paraphraser.io

simbert

BERT：原始版本bertRoberta：哈工大开源的中文wwm roberta模型BERT-SQ：本人在百度知道相似句数据集(Sim-Query)上微调后的bert模型Roberta-SQ：同上BERT-Whitening： @苏剑林 最新博客中提出的白化模型。Roberta-Whitening：同上


https://yongzhuo.blog.csdn.net/article/details/89166307

language fluency test:

https://github.com/baojunshan/nlp-fluency

many paraphraser models for english are on huggingface, but few for chinese.

https://huggingface.co/lijingxin/mt5-for-zh-paraphrase
https://pypi.org/project/genienlp/
https://github.com/salesforce/decaNLP
parrot paraphraser
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
