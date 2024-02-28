---
title: Multimodal Autoregressive Unsupervised Learning
created: '2024-02-28T14:09:13.086Z'
modified: '2024-02-28T14:14:16.525Z'
---

# Multimodal Autoregressive Unsupervised Learning

GPT2 models from huggingface accept `inputs_embeds` as parameter of instance call and method "generate".

---

Install pytorch gpu with conda:

```bash
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

---

Set `HF HUB OFFLINE=1` while loading local models/
