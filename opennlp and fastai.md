---
title: opennlp and fastai
created: '2022-08-07T13:57:11.364Z'
modified: '2022-08-07T15:35:27.950Z'
---

# opennlp and fastai

## [opennlp]()

opennlp uses onnx runtime(maybe?), may support m1 inference.

opennlp is written in java. after installing openjdk on macos with homebrew, run this to ensure openjdk is detected:

```bash
 sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

fastai does not support macos.
