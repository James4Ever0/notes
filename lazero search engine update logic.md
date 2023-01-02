---
title: lazero search engine update logic
created: '2022-12-13T18:09:13.126Z'
modified: '2023-01-02T21:00:54.175Z'
---

# lazero search engine update logic

[docprompting](https://github.com/shuyanzhou/docprompting) generate code from doc retrieval, using [tldr](https://github.com/tldr-pages/tldr) and [CoNaLa](https://conala-corpus.github.io/) for training code generation from prompt

[ColBERT](https://medium.com/@varun030403/colbert-a-complete-guide-1552468335ae) and [RoBERTa](https://medium.com/dataseries/roberta-robustly-optimized-bert-pretraining-approach-d033464bd946) for document retrieval and embedding

the update process shall be atomic. when the update is successful, there should be a file created under index directory. always check the newest index first. cleanup unusable/incompatible indexs.

if there's no previous compatible index present, make index from group up, clean up incompatible index if necessary. if previous compatible index is found, decompose it into small groups, waiting for merge and update.

first checksum all files along with file names. if file is present with matched checksum, don't touch it, or either remove it from index, create new index or replace index.

next create or merge file list.

then we scan those new files then act accordingly to our index.

finally we merge our index, save to a different place, place the flag, remove the flag of old index then remove old index completely. if merge is not possible for huge datasource, we perform search in minibatches.

