---
title: Create sparse matrix based liquid state machine
created: '2023-11-14T13:58:28.712Z'
modified: '2023-11-14T15:38:42.051Z'
---

# Create sparse matrix based liquid state machine

use `tensorly` to create random sparse tensor and eye sparse tensor with ease, which could be numpy only.

`scipy`, `pytorch`, `tensorflow`, `jax` all support sparse tensor construction but advanced apis are not.

use `eye` to create bias and input matrix, extract node values. use random sparse tensor to initialize weight matrix. use self matrix multiplication to perform propagation.

---

the human brain has roughly 87 billion neurons, and every one of them has thousands of synapses.

---

```python
large_number = 1_000_000
>>> import torch
>>> torch.arange(large_number).unsqueeze(0).repeat(2, 1)
>>> index_arr = torch.arange(large_number).unsqueeze(0).repeat(2, 1)
>>> val_arr = torch.ones(large_number)
>>> sparse_eye = torch.sparse_coo_tensor(index_arr, val_arr, (large_number, large_number))

```
