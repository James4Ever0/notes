---
created: 2022-04-28T10:22:06+08:00
modified: 2022-04-28T10:56:54+08:00
---

# gpt-2 ram requirements

need p40/m40 which has 24gb vram. need at least 60gb ram to load model.

using low ram devices need library like deepspeed, bminf or megengine.

you can also use others provided web services.

can use colab/kaggle or aistudio to do the job. paid training enviorment is also avaliable.

https://github.com/TsinghuaAI/CPM-1-Generate
https://github.com/arrmansa/Basic-UI-for-GPT-J-6B-with-low-vram
https://pythonawesome.com/finetune-gpt2-xl-and-gpt-neo-on-a-single-gpu-with-huggingface-transformers-using-deepspeed
https://github.com/OpenBMB/BMInf

web api for chinese plug:
https://m.nlp.aliyun.com/mportal#/textGenerate
