---
title: Image and audio feature extraction for Language Models
created: '2024-03-01T01:40:25.443Z'
modified: '2024-03-01T01:49:23.381Z'
---

# Image and audio feature extraction for Language Models

## Image processing

Usually images are large so we need to crop.

You have three ways to crop an image.

### Patchify

```python

import patchify

```

### Torch `unwrap`

It works by expanding target dimension and appending a new dimension corresponding to it.

```python
import torch


```


### EMPat
