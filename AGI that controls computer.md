---
title: AGI that controls computer
created: '2023-05-04T09:28:11.880Z'
modified: '2023-05-05T02:01:09.262Z'
---

# AGI that controls computer

## encoding

use hfft/rfft to transform multipart inputs (special bits, different part of mouse coords (x, y, dx, dy))

if you want to use complex number as RNN input, you may need to swap ViT for ComplexConv2D, but maybe you just need a few.

----

libraries that handle complex neural networks:

[complexPyTorch](https://github.com/wavefrontshaping/complexPyTorch)

[pytorch-complex](https://github.com/soumickmj/pytorch-complex)

## multimodal

do our model have to output multimodal data?

if you combine some "special" bits along with token embeding by ihfft, you may have to retrain the entire damn network. also in order to make way for special bits, you may have to introduce extra linear layer.

----

some may prefer "LoRA"? by only introducing few tunable params and changing the overall output?

----

we may not annotate anything in our dataset. in contrast, we will set goals and make multiple interfaces for our model to explore.

## file sharing and communication

make sure you don't share important files as read/write on VM.

----

you may host some "execution server" on UTM VMs. you may expose your very large hard disk using WebDAV server. i think x11vnc and other vnc server may suffice for linux, but we always want to listen to the real operational data, including human operation/intervention, not just those in VNC protocols.

----

WebDAV servers:

[wsgidav](https://github.com/mar10/wsgidav) (python)

```bash
wsgidav --host=192.168.64.1 --port=8081 --root="/Volumes/Toshiba XG3/works/agi_computer_control"  --auth=anonymous
```

[webdav-cli](https://github.com/svtslv/webdav-cli) （nodejs)

----

for Ubuntu ARM VM, `mss` failed but `pyautogui` works. write one python script to pipe raw images to ffmpeg for better compression ratio by shell. the final video is not "time-accurate". it is frame by frame, matched with timestamps.
