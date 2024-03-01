---
title: Image and audio feature extraction for Language Models
created: '2024-03-01T01:40:25.443Z'
modified: '2024-03-01T02:05:55.969Z'
---

# Image and audio feature extraction for Language Models

## Image processing

### Split image into patches

Usually images are large so we need to split.

You have three ways to split an image.

#### Patchify

The splited indexs are put in front instead of append back.

```python
import numpy as np
from patchify import patchify

image = np.random.rand(512,512,3)

patches = patchify(image, (128,128,3), step=128)
print(patches.shape) # (4, 4, 1, 128, 128, 3)
```

#### Torch `unwrap`

It works by expanding target dimension and appending a new dimension corresponding to it.

```python
import torch
```


#### EMPatches

```python
from empatches import EMPatches
```

### Convert fixed-size patches into embeddings

The embeddings from ViT cannot be used directly by LLM. Instead, use `LayerNorm` and `Dense` as simple adaptors.

```python


```

## Audio processing

