---
title: Multimodal Autoregressive Unsupervised Learning
created: '2024-02-28T14:09:13.086Z'
modified: '2024-02-28T14:16:41.441Z'
---

# Multimodal Autoregressive Unsupervised Learning

GPT2 models from huggingface accept `inputs_embeds` as parameter of instance call and method "generate".

---

Install pytorch gpu with conda:

```bash
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

---

Set `HF HUB OFFLINE=1` while loading local models, to prevent accessing network.

---

Set `Environment="OLLAMA_MODELS=<model_path>"` in ollama systemd service file. Remember to change username and usergroup too.


