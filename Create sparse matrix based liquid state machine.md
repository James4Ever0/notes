---
title: Create sparse matrix based liquid state machine
created: '2023-11-14T13:58:28.712Z'
modified: '2023-11-14T14:04:20.324Z'
---

# Create sparse matrix based liquid state machine

use `tensorly` to create random sparse tensor and eye sparse tensor with ease.

`scipy`, `pytorch`, `tensorflow`, `jax` all support sparse tensor construction but advanced apis are not.

use `eye` to create bias and input matrix, extract node values. use random sparse tensor to initialize weight matrix. use self matrix multiplication to perform propagation.

the human brain has roughly 87 billion neurons, and every one of them has thousands of synapses.
