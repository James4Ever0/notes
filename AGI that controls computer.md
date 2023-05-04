---
title: AGI that controls computer
created: '2023-05-04T09:28:11.880Z'
modified: '2023-05-04T09:36:52.318Z'
---

# AGI that controls computer

## encoding

use hfft to transform multipart inputs (special bits, different part of mouse coords (x, y, dx, dy))

if you want to use complex number as input, you may need to swap ViT for ComplexConv2D

----

libraries that handle complex neural networks:

[complexPyTorch](https://github.com/wavefrontshaping/complexPyTorch)

[pytorch-complex](https://github.com/soumickmj/pytorch-complex)

## multimodal

do our model have to output multimodal data?

if you combine some "special" bits along with token embeding by ihfft, you may have to retrain the entire damn network. also in order to make way for special bits, you may have to introduce extra linear layer.

## file sharing and communication

you may host some "execution server" on UTM VMs. you may expose your very large hard disk using WebDAV server. i think x11vnc may suffice, 
