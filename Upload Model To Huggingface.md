---
tags: [backup, git, huggingface, model, network, stub, sync]
title: Upload Model To Huggingface
created: '2022-05-29T08:03:27.000Z'
modified: '2022-08-18T16:30:30.881Z'
---

# Upload Model To Huggingface

via code:
 https://zhuanlan.zhihu.com/p/390826470

from transformers import AutoModelForMaskedLM, AutoTokenizer

checkpoint = "camembert-base"

model = AutoModelForMaskedLM.from_pretrained(checkpoint)
tokenizer = AutoTokenizer.from_pretrained(checkpoint)

model.push_to_hub("dummy-model")
tokenizer.push_to_hub("dummy-model")
# config.push_to_hub("<model_name>")

