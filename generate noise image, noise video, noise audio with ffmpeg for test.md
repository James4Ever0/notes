---
title: 'generate noise image, noise video, noise audio with ffmpeg for test'
created: '2022-11-09T16:43:31.580Z'
modified: '2022-11-09T16:44:51.354Z'
---

# generate noise image, noise video, noise audio with ffmpeg for test

[simulating tv noise](https://stackoverflow.com/questions/15792105/simulating-tv-noise)

```bash
ffmpeg -f lavfi -i nullsrc=s=1280x720 -filter_complex \
"geq=random(1)*255:128:128;aevalsrc=-2+random(0)" \
-t 5 output.mkv
```

```bash
ffmpeg -f rawvideo -video_size 1280x720 -pixel_format yuv420p -framerate 25 \
-i /dev/urandom -ar 48000 -ac 2 -f s16le -i /dev/urandom -codec:a copy \
-t 5 output.mkv
```
