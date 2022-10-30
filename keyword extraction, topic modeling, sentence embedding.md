---
title: 'keyword extraction, topic modeling, sentence embedding'
created: '2022-10-29T10:37:05.301Z'
modified: '2022-10-30T02:48:48.811Z'
---

# keyword extraction, topic modeling, sentence embedding


## stopwords

```python
from nltk.corpus import stopwords
```

[stopwordsiso](https://github.com/stopwords-iso/stopwords-iso/tree/master/python) in python

## keyword extraction

[tutorial and libraries](https://heartbeat.comet.ml/keyword-extraction-with-python-498bc18aadc)

[summa](https://pypi.org/project/summa/) TextRank implementation for text summarization and keyword extraction in Python 3, with optimizations on the similarity function.

[keybert](https://blog.csdn.net/whatwho_518/article/details/124481742) uses sentence transformer to do the job

[kwx](https://pypi.org/project/kwx/)

[pke](https://github.com/boudinfl/pke) Python Keyphrase Extraction module

```python
import jieba.analyse as ana
# methods under ana:
# ['analyzer', 'default_textrank', 'default_tfidf', 'extract_tags', 'set_idf_path', 'set_stop_words', 'textrank', 'tfidf']
```

