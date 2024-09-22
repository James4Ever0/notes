---
title: Tesla K80 with PVE and PyTorch
created: '2024-09-22T01:44:20.866Z'
modified: '2024-09-22T01:58:54.569Z'
---

# Tesla K80 with PVE and PyTorch

You may have to enable some flags like "All functions" and "PCI-E" when passing through Tesla K80 in PVE.

---

You can install NVIDIA Linux driver upto 470.

```bash
sudo apt install -y nvidia-headless-470-server
```

Install CUDA driver 11.8 separatedly, then install PyTorch.

```bash
conda create -n <env_name> python=3.10
conda install -n <env_name> cudatoolkit=11.8
conda run -n <env_name> --no-capture-output pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

Install PyTorch directly with `conda`.

```bash
conda install -n <env_name> python=3.10 pytorch torchvision torchaudio pytorch-cuda=11.8 -c pytorch -c nvidia
```
