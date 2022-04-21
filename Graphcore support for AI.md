---
created: 2022-04-21T11:33:07+08:00
modified: 2022-04-21T11:49:41+08:00
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
