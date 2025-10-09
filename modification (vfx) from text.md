---
title: video generation/modification (vfx) from text
created: 2022-10-09T05:54:25+00:00
modified: 2025-10-09T22:20:09+08:00
---

# video generation/modification (vfx) from text

need to provide feedback to video creator, like openai sora app

translation: https://github.com/liuzhao1225/YouDub

opencut: capcut Foss alternative 

full video generation with audio, music and cut

https://github.com/bilibili/Index-anisora

---

Sora is the new SOTA video generation model from OpenAI.

Following up projects:

- [Open-Sora](https://github.com/hpcaitech/Open-Sora)
- [SoraReview](https://github.com/lichao-sun/SoraReview)
- [opensora](https://github.com/hku/opensora)
- [Open-Sora-Plan](https://github.com/PKU-YuanGroup/Open-Sora-Plan)

---

达摩院放出了[文本生成视频模型](https://modelscope.cn/models/damo/text-to-video-synthesis/summary)，支持英文输入

[huggingface space](https://huggingface.co/damo-vilab/modelscope-damo-text-to-video-synthesis)

model weights:

| weight path | weight size | model name | author |
| -- | -- | -- | -- |
| [text-to-video-ms-1.7b](https://huggingface.co/damo-vilab/text-to-video-ms-1.7b) | unknown | unknown | damo-vilab |
| [modelscope-damo-text-to-video-synthesis](https://huggingface.co/damo-vilab/modelscope-damo-text-to-video-synthesis) | unknown | unknown | damo-vilab |
| [text-to-video-ms-1.7b-legacy](https://huggingface.co/damo-vilab/text-to-video-ms-1.7b-legacy) | unknown | unknown | damo-vilab |

can also use from modelscope:

```python
from modelscope.pipelines import pipeline
from modelscope.utils.constant import Tasks

p = pipeline('text-to-video-synthesis', 'damo/text-to-video-synthesis')
```
----


[PAIR](https://huggingface.co/spaces/PAIR) now releases [Text2Video-Zero](https://huggingface.co/spaces/PAIR/Text2Video-Zero) which leverages existing stable diffusion models to generate video. also released a bunch of controlnet dreambooth weights.

----

[lucidrains](https://github.com/lucidrains) is a workaholic on transformer implementations. we should scrape all the repos and index them. there are [faster language models](https://github.com/lucidrains/memory-efficient-attention-pytorch) to train.

-----

[Phenaki Video](https://github.com/lucidrains/phenaki-pytorch), which uses Mask GIT to produce text guided videos of up to 2 minutes in length, in Pytorch

[dreamix](https://dreamix-video-editing.github.io/) (not open-source)

[instruct-pix2pix](https://github.com/timothybrooks/instruct-pix2pix) requires 16GB+ VRAM

[text2live](https://github.com/omerbt/Text2LIVE) modify video by text prompt (such as add fire in mouth)

[recurrent-interface-network-pytorch](https://github.com/lucidrains/recurrent-interface-network-pytorch) using diffusion to generate images and video

high quality! [imagegen-video code](https://github.com/lucidrains/imagen-pytorch/blob/main/imagen_pytorch/imagen_video.py) with [demo](https://imagen.research.google/video/) and [paper](https://arxiv.org/pdf/2210.02303.pdf)

抄视频 视频的时间要讲究 看看是抄一年前的好还是抄刚刚发布的好

在发布的一个视频当中 最多抄某个作者的两三个符合要求的片段

use editly smooth/slick transitions and subtitles to beat the copy-detection algorithm, also consider color change in ffmpeg

动态 专栏也可以抄

[make-a-video](https://github.com/lucidrains/make-a-video-pytorch)

谷歌AI歌手震撼来袭！AudioLM简单听几秒，便能谱曲写歌 https://www.kuxai.com/article/398
