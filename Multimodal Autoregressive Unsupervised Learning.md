---
title: Multimodal Autoregressive Unsupervised Learning
created: '2024-02-28T14:09:13.086Z'
modified: '2024-02-28T14:32:57.039Z'
---

# Multimodal Autoregressive Unsupervised Learning

Recently search engine & browser augmented generation has become popular. A great tool for creating video scripts. 

---

Google has released a new architecure called Genie, which can generate latent action space only using video unsupervised training. 

---

Do not ever use NTFS in Linux. If you unfortunatedly face disk inaccessible problem when accessing NTFS disks, in the first case run chkdsk /f onthen reboot into Windows twice. The usage of the /f parameter iimportant!

After fixing, copy all files to another place, format the disk into ext4 or xfs, then recover the files.

---

GPT2 models from huggingface accept `inputs_embeds` as parameter of instance call and method "generate".

Typically to adapt ViT into LLM you need `LayerNorm` and a linear projection layer.

You cannot put custom embedding into text generaton pipeline.

---

To encode token manually in GPT2:

```python
input_embeds = model.transformer.wte(input_ids)
```

In LLaMA:

```python
def embed_tokens(self，token_ids):
  if hasattr(self.llama_model.base_model, "model"): # with lora
    embeds = self.llama_model.base_model.model.model.embed_tokens(token_ids)
  else:
    self.llama_model.base_model.embed_tokens(token_ids)
return embeds
```

---

Install pytorch gpu with conda:

```bash
conda install pytorch torchvision torchaudio pytorch-cuda=12.1 -c pytorch -c nvidia
```

---

Set `HF_HUB_OFFLINE=1` while loading local models, to prevent accessing network.

---

Set `Environment="OLLAMA_MODELS=<model_storage_path>"` in ollama systemd service file. Remember to change username and usergroup too, and set appropriate permission to model storage path.
