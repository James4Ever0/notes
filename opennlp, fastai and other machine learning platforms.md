---
title: 'opennlp, fastai and other machine learning platforms'
created: '2022-08-07T13:57:11.364Z'
modified: '2022-08-07T15:48:14.212Z'
---

# opennlp, fastai and other machine learning platforms

## [opennlp](https://opennlp.apache.org/)

opennlp uses onnx runtime(maybe?), may support m1 inference.

opennlp is written in java. after installing openjdk on macos with homebrew, run this to ensure openjdk is detected:

```bash
 sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

opennlp has a language detector for 103 languages, including chinese. opennlp has a sentence detector (separator) which could be trained on chinese (maybe?)

in order to use opennlp with less code written, here's how to [invoke java from kotlin]()

## [dl4j]()

found on [mannings article about search engine suggestions](). in this example it is used with lucene, which has

deep learning library for java

## [xgboost]()

gradient boost is used to train decision trees and classification models.

## [lightgdm]()

## [pymc]()

## [fastai]()

[docs](https://docs.fast.ai/)

[courses](https://course.fast.ai/)

on the twitter list related to opennlp shown up on its official website, fastai has been spotted.

fastai does not support macos.

searching '' like [this]() in github we get a [dataset for pets classification]() from [fastai 2020 tutorial series](https://github.com/fastai/course20/blob/master/index.ipynb)

