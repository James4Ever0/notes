---
tags: [acceleration, AI, gpu alternative, graphcore, hardware]
title: Graphcore support for AI
created: '2022-04-21T03:33:07.000Z'
modified: '2022-08-19T02:35:20.563Z'
---

# Graphcore support for AI

Graphcore's IPU could be cheaper and faster than NVIDIA's A100, though need sharing on-board RAM.
Supports tensorflow, pytorch, paddlepaddle.
https://docs.graphcore.ai/en/latest/

pytorch: poptorch, pytorch-lightning(tpu and ipu)

tensorflow:
from tensorflow.python import ipu

# Create an IPU distribution strategy
strategy = ipu.ipu_strategy.IPUStrategy()

with strategy.scope():
    ...

paddlepaddle:
https://github.com/graphcore/portfolio-examples/tree/master/paddlepaddle/bert-base

https://github.com/graphcore/Paddle.git

TensorFlow 1 & 2 support with full performant integration with TensorFlow XLA backend
PyTorch support for targeting IPU using the PyTorch ATEN backend 
PopART™ (Poplar Advanced Runtime) for training & inference; supports Python/C++ model building plus ONNX model input
Full support for PaddlePaddle
Other frameworks support coming soon
