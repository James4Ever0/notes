---
created: 2022-05-29T16:03:27+08:00
modified: 2022-05-29T16:05:14+08:00
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

