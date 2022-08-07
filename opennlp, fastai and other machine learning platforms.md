---
title: 'opennlp, fastai and other machine learning platforms'
created: '2022-08-07T13:57:11.364Z'
modified: '2022-08-07T16:38:56.215Z'
---

# opennlp, fastai and other machine learning platforms

## [opennlp](https://opennlp.apache.org/)

[hands-on docs](https://opennlp.apache.org/docs/2.0.0/manual/opennlp.html)

[model zoo](https://opennlp.apache.org/models.html)

opennlp uses onnx runtime(maybe?), may support m1 inference.

opennlp is written in java. after installing openjdk on macos with homebrew, run this to ensure openjdk is detected:

```bash
 sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

opennlp has a language detector for 103 languages, including chinese. opennlp has a sentence detector (separator) which could be trained on chinese (maybe?)

in order to use opennlp with less code written, here's how to [invoke java from kotlin](https://kotlinlang.org/docs/java-interop.html)

## [dl4j](https://deeplearning4j.konduit.ai/)

found on [mannings article about better search engine suggestions](https://manningbooks.medium.com/more-sensitive-suggestions-1c1c39cbdc12). in this example it is used with lucene, which has image retrieval (LIRE) capability. lucene is also avaliable as [lucene.net](https://lucenenet.apache.org/) in dotnet/c#.

to install lucene.net:

```bash
dotnet add package Lucene.Net --prerelease
```

deep learning library for java

## [xgboost](https://xgboost.readthedocs.io/en/stable/)

gradient boost is used to train decision trees and classification models.

## [lightgbm](https://lightgbm.readthedocs.io/en/v3.3.2/)

## [pymc](https://www.pymc.io/welcome.html)

[docs]()

## [fastai](https://github.com/fastai/fastai)

[docs](https://docs.fast.ai/)

[courses](https://course.fast.ai/)

on the twitter list related to opennlp shown up on its official website, fastai has been spotted.

fastai does not support macos. or is it? fastai is on top of pytorch.

searching 'samoyed' like [this](https://github.com/search?q=org%3Afastai+samoyed&type=code) in github we get a [dataset for pets classification called imagewoof](https://s3.amazonaws.com/fast-ai-imageclas/imagewoof.tgz) from [fastai 2020 tutorial series](https://github.com/fastai/course20/blob/master/index.ipynb). more image classes like subcategories of cats may be found in [imagenet](https://image-net.org/index).

