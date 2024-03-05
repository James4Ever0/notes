---
title: Image and audio feature extraction for Language Models
created: '2024-03-01T01:40:25.000Z'
modified: '2024-03-05T09:25:08.116Z'
---

# Image and audio feature extraction for Language Models

Use `ipython` instead of `python` to test these code, get better parameter hints, and dynamic hints, just like what you saw in brownie.

Use `dataset.transform` instead of `dataset.map` to save loading time.

## Image processing

Many language models resize, reshape & pad the input image into 224x224 square and put into ViT directly.

To simplify the pipeline, we would recommend you to sample the image into fixed size square patches, like 2x2, 4x4 etc.

Or you can skip the ViT embedding part, just use [Fuyu-8b](https://hf-mirror.com/adept/fuyu-8b) or take its architecture `FuyuForCausalLM` and processor `FuyuProcessor` because it supports arbitrary sized images. 

```python
from transformers import FuyuProcessor, FuyuForCausalLM
from PIL import Image
import requests

model_name = "adept/fuyu-8b"

processor = FuyuProcessor.from_pretrained(model_name)
model = FuyuForCausalLM.from_pretrained(model_name)

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

image = torch.rand(512,512,3)

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

The first token is the class token, randomly initialized and processed along with the transformer, output as the summary of the full image, can be extracted for image embedding.

Proof: 

```
224x224 is the shape of input image
16x16 is the patch size

224/16 = 14
14*14 + 1 = 197
```

```python
import torch
import transformers

# not torch.randn (sample from normal distribution)
image = torch.rand(3, 224, 224) # chw

model_name = "google/vit-base-patch16-224-in21k"

processor = transformers.AutoImageProcessor(model_name) # for processing image 

image = processor(image, do_rescale=False) # use this parameter when passing values ranging from 0 to 1

#image = processor(pil_image) # can also handle pil image

model = transformers.ViTModel(model_name)

outputs = model(pixel_values = image)

embeddings = outputs.last_hidden_state[:,0,:] # torch.Size([1, 768])
```

## Audio processing

An useful and related field to speaker diarization in video processing is visual entity recognization, which can help you identify anime or movie characters across different frames.

When unsure, the agent shall consult online search engines, subtitles and existing recognized entities for classification. If a dataset is successfully created, one can train a YOLO model to speed up the process, used along with popular person/anime head detection models.

In most videos speakers and visuals are aligned. You can first identify speakers then get character identification. Remember you need to use special pipeline for long-time diarization.

---

For multilanguage context, you would like to use speaker detection models like [pyannote](https://github.com/pyannote/pyannote-audio). [Diart](https://github.com/juanmc2005/diart) is a speech processing library based on that and can be used in real time, with speaker diarization, voice activity detection training pipelines.

[Whisper-streaming](https://github.com/ufal/whisper_streaming) uses LocalAgreement algoritm to segment chunks of audio and merge common patterns.

---

Whisper architecture is comprised of an audio encoder and transcription decoder. The output of the encoder is feed into every cross attention layer of the decoder. For feature extraction, you only need to use the encoder.

---

You pass single channel audio amplitude array to audio feature extractors with predetermined audio sample rate. If the sample rate mismatch, you need to resample the audio.

---

Different audio transformers choose different context window sizes. Like LLMs, they can be streamed. However during training they must use a fixed context size.

For [Whisper](https://github.com/OpenAI/whisper), the context size is 30 seconds. Confugurable at: `transformers.WhisperFeatureExtractor(chunk_length=30, ...)`

For AST, it is 10.24 seconds. You can find more info about input and output sizes [here](https://github.com/YuanGongND/ast). Configurable at: `transformers.ASTFeatureExtractor(max_length=1024, ...)`

These numbers can be found over respective processor parameters. 

```python
from transformers import AutoProcessor, ASTModel
import torch
from dataset import load_dataset


dataset_name = "hf_internal_testing/librispeech_asr_demo"
model_name = "MIT/ast-finetuned-audioset-10-10-0.4593"

dataset = load_dataset(dataset_name, 'clean', split="validation")
sampling_rate = dataset.features["audio"].sampling_rate

processor = AutoProcessor.from_pretrained(model_name)
model = ASTModel.from_pretrained(model_name)

inputs = processor(dataset[0].audio.array, sampling_rate=sampling_rate, return_tensors='pt')

with torch.no_grad():
    outputs = model(**inputs)

pooler_output = outputs["pooler_output"]
```
