---
title: 'keyword extraction, topic modeling, sentence embedding'
created: '2022-10-29T10:37:05.301Z'
modified: '2022-10-30T13:11:24.294Z'
---

# keyword extraction, topic modeling, sentence embedding

## language models

[allennlp-models](https://github.com/allenai/allennlp-models)

[bert lang street](https://bertlang.unibocconi.it/about)

## recommendation

[deepmatch](https://deepmatch.readthedocs.io/en/latest/Quick-Start.html)

## fuzzy search

[fuzzywuzzy](https://github.com/seatgeek/fuzzywuzzy) or [thefuzz](https://github.com/seatgeek/thefuzz)

[fzf](https://github.com/junegunn/fzf) a commandline fuzzy matcher

[iterfzf](https://www.findbestopensource.com/product/dahlia-iterfzf) as a fzf python binding and its related projects

[rapidfuzz](https://github.com/maxbachmann/rapidfuzz)

## stopwords

```python
from nltk.corpus import stopwords
```

[stopwordsiso](https://github.com/stopwords-iso/stopwords-iso/tree/master/python) in python

## summarization

[sumy](https://pypi.org/project/sumy/) Simple library and command line utility for extracting summary from HTML pages or plain texts

[pytextrank](https://pypi.org/project/pytextrank/) Python implementation of TextRank as a spaCy pipeline extension, for graph-based natural language work plus related knowledge graph practices; used for for phrase extraction and lightweight extractive summarization of text documents

[summa](https://pypi.org/project/summa/) TextRank implementation for text summarization and keyword extraction in Python 3, with optimizations on the similarity function.

## keyword extraction

[rake-nltk](https://pypi.org/project/rake-nltk/) RAKE short for Rapid Automatic Keyword Extraction algorithm, is a domain independent keyword extraction algorithm which tries to determine key phrases in a body of text by analyzing the frequency of word appearance and its co-occurance with other words in the text.

[multi-rake](https://pypi.org/project/multi-rake/) Multilingual Rapid Automatic Keyword Extraction (RAKE) for Python

[yake](https://pypi.org/project/yake/) Unsupervised Approach for Automatic Keyword Extraction using Text Features

[tutorial and libraries](https://heartbeat.comet.ml/keyword-extraction-with-python-498bc18aadc)


[keybert](https://blog.csdn.net/whatwho_518/article/details/124481742) uses sentence transformer to do the job

[kwx](https://pypi.org/project/kwx/)

[pke](https://github.com/boudinfl/pke) Python Keyphrase Extraction module

```python
import jieba.analyse as ana
# methods under ana:
# ['analyzer', 'default_textrank', 'default_tfidf', 'extract_tags', 'set_idf_path', 'set_stop_words', 'textrank', 'tfidf']
```

