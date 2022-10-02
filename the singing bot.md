---
tags: [lip sync, motion driven video, talking head, video generator, wombo.ai]
title: the singing bot
created: 2022-05-13T21:50:48+08:00
modified: 2022-10-03T03:05:38+08:00
---

# the still image to singing face bot, lip-sync video generation

wombo.ai, likely to be talking head or yanderifier

https://github.com/mchong6/GANsNRoses/

https://github.com/williamyang1991/VToonify

生成高质量的艺术人像视频是计算机图形学和视觉中一项重要且理想的任务。虽然已经提出了一系列基于强大的 StyleGAN 成功的人像图像卡通化模型，但这些面向图像的方法在应用于视频时存在明显的局限性，在这项工作中，我们通过引入一种新颖的 VToonify 框架来研究具有挑战性的可控高分辨率肖像视频风格迁移。具体来说，VToonify 利用StyleGAN 的中高分辨率层基于编码器提取的多尺度内容特征来渲染高质量的艺术肖像，以更好地保留帧细节。作为输入，有助于输出具有自然运动的完整面部区域。 amework 与现有的基于 StyleGAN 的图像卡通化模型兼容，以将其扩展到视频卡通化，并继承了这些模型的吸引人的特性，可灵活地控制颜色和强度。这项工作展示了基于 Toonify 和 DualStyleGAN 的 VToonify 的两个实例，用于基于集合广泛的实验结果证明了我们提出的 VToonify 框架在生成具有灵活风格控制的高质量和时间连贯的艺术肖像视频方面优于现有方法的有效性

all in one colab text to talking face generation, also consider paddlespeech example:
https://github.com/ChintanTrivedi/ask-fake-ai-karen

avaliable from paddlegan as an example used in paddlespeech, the artificial host.

lip-sync accurate wav2lip:
https://github.com/Rudrabha/Wav2Lip

lipgan generate realistic lip-sync talking head animation(fully_pythonic branch or google colab notebook):
https://github.com/Rudrabha/LipGAN

google's lipsync implementation, using tensorflow facemesh:
https://github.com/google/lipsync
https://lipsync.withyoutube.com/
https://github.com/tensorflow/tfjs-models/tree/master/facemesh

network reverse engineering for wombo.ai:
https://github.com/the-garlic-os/wombo-reverse-engineering

matamata using vosk models, recommend to use gentle lip-sync method:
https://github.com/AI-Spawn/Auto-Lip-Sync
https://github.com/Matamata-Animator/Matamata-Core
https://github.com/Yey007/Auto-Lip-Sync

ai-based lip reading might be irrelevant to lip-sync video generation:
https://github.com/eflood23/lipsync
