---
title: Tesla K80 with PVE and PyTorch
created: '2024-09-22T01:44:20.866Z'
modified: '2024-09-22T01:54:41.671Z'
---

# Tesla K80 with PVE and PyTorch

You can install linux driver upto 470.

```bash
sudo apt install -y nvidia-headless-470-server
```

Install CUDA driver 11.8.

```bash
conda install -n <env_name> cudatoolkit=11.8
```
