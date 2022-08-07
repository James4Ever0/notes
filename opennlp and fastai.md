---
title: opennlp and fastai
created: '2022-08-07T13:57:11.364Z'
modified: '2022-08-07T15:39:33.238Z'
---

# opennlp and fastai

## [opennlp](https://opennlp.apache.org/)

opennlp uses onnx runtime(maybe?), may support m1 inference.

opennlp is written in java. after installing openjdk on macos with homebrew, run this to ensure openjdk is detected:

```bash
 sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

## [fastai]

[docs](https://docs.fast.ai/)

[courses](https://course.fast.ai/)
on twitter list related to opennlp shown up on its official website, fastai has been spotted.

fastai does not support macos.

searching '' like [this]() in github we get a [dataset for pets classification]() from [fastai 2020 tutorial series](https://github.com/fastai/course20/blob/master/index.ipynb)

