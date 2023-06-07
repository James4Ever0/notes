---
title: AGI that controls computer
created: '2023-05-04T09:28:11.000Z'
modified: '2023-06-07T06:20:16.360Z'
---

# AGI that controls computer

make specialized (in RPA) tokenizer and embedding for this new model. add new words to the tokenizer.

----

you can just boot ubuntu/kali/parrot iso without installing.

but that would make us embarrasing. we need to check for the option.

----

use ChatGPT-derived projects for localized propaganda on CyberGod and The Frozen Forest.

## obs remote control

using [obs-websocket](https://github.com/obsproject/obs-websocket) you can use python to do real scripting. but first spin up obs first (with websocket related commandline arguments)

you can also write and load scripts for obs, run on custom intervals and conditions.

## audio recording

your OS may go slient if you want to record audio from "speakers"

----

using pyaudio, on macos, you need blackhole for sending all audio to oblivion, thus able to be recorded.

on Linux, you need audio loopback device.

run: `sudo modprobe snd-aloop`

you use `hw:1:0` or "Analog Device Output" for slient output/speaker, and use `hw:1:1` or "Analog Device Input" for recording.

## benchmarks

it is always a mystery for us to develop the right ML model. however, we can setup guidelines of good performance over specific task.

automate the benchmark, setup metrics. there could be more room for trials and imagination.

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

----

you can add special task specific embedding before passing to main model, then minus that task specific embedding after passing to classification model.

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

```bash
webdav-cli --host=192.168.64.1 --port=8081 --username=root --password=root --path="/Volumes/Toshiba XG3/works/agi_computer_control"
```

## video recording

for Ubuntu ARM VM, `mss` failed on wayland but `pyautogui` works in both cases. write one python script to pipe raw images to ffmpeg for better compression ratio by shell. the final video is not "time-accurate". it is frame by frame, matched with timestamps.

----

forcing ubuntu to use xorg by: `sudo vim /etc/gdm3/custom.conf`

## resize UTM VM disks

you need to first resize the virtio disk in utm setting, then resize partition by using gparted, then [update the device mapper](https://www.albertyw.com/note/resizing-ubuntu-utm#:~:text=For%20an%20Ubuntu%20guest%20OS%20running%20a%20default,be%20corrected%20by%20w%20%28rite%29%20warning%20More%20items)
