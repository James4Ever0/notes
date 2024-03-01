---
title: Image and audio feature extraction for Language Models
created: '2024-03-01T01:40:25.443Z'
modified: '2024-03-01T03:52:04.462Z'
---

# Image and audio feature extraction for Language Models

Use `ipython` instead of `python` to test these code, get better parameter hints.

## Image processing

Many language models resize, reshape & pad the input image into 224x225 square and put into ViT directly.

To simplify the pipeline, we would recommend you to sample the image into fixed size square patches, like 2x2, 4x4 etc.

Or you can skip the ViT embedding part, just use [Fuyu-8b](https://hf-mirror.com/adept/fuyu-8b) or take its architecture `FuyuForCausalLM` and processor `FuyuProcessor` because it supports arbitrary sized images. 

```python
from transformers import FuyuProcessor, FuyuForCausalLM
from PIL import Image
import requests

processor = FuyuProcessor.from_pretrained("adept/fuyu-8b")
model = FuyuForCausalLM.from_pretrained("adept/fuyu-8b")

url = "http://images.cocodataset.org/val2017/000000039769.jpg"
image = Image.open(requests.get(url, stream=True).raw)
prompt = "Generate a coco-style caption.\n"

inputs = processor(text=text_prompt, images=image, return_tensors="pt")
outputs = model(**inputs)

generated_ids = model.generate(**model_inputs, max_new_tokens=7)
generation_text = processor.batch_decode(generated_ids, skip_special_tokens=True)
print(generation_text)
```

### Split image into patches

Usually images are large so we need to split.

You have three ways to split an image.

#### Patchify

The splited indexs are put in front instead of appended back.

```python
import numpy as np
from patchify import patchify

image = np.random.rand(512,512,3)

patches = patchify(image, (128,128,3), step=128)
print(patches.shape) # (4, 4, 1, 128, 128, 3)
```

#### Torch `unfold`

It works by expanding target dimension and appending a new dimension corresponding to it.

```python
import torch

image = torch.randn(512,512,3)

patches = image.unfold(0, 128, 128).unfold(1, 128, 128).unfold(2, 3, 3)
print(patches.shape) # torch.Size([4, 4, 1, 128, 128, 3])
```


#### EMPatches

```python
import numpy as np
from empatches import EMPatches

image = np.random.rand(512, 512, 3)

emp = EMPatches()

patches, indices = emp.extract_patches(image, patchsize = 128, overlap = 0)
print(patches) # a list of numpy arrays, total 16 items
print(indices) # [(x_start, x_end, y_start, y_end), ...], total 16 items
```

### Convert fixed-size patches into embeddings

The embeddings from ViT cannot be used directly by LLM. Instead, use `LayerNorm` and `Dense` as simple adaptors.

```python
# load visual dataset.
from datasets import load_dataset

# Load the ImageNet dataset from Hugging Face Datasets
dataset = load_dataset("mrm8488/ImageNet1K-val")
dataset['image']
```

## Audio processing

