---
title: audio watermark removal
created: 2022-09-13T00:28:28+08:00
modified: 2022-09-13T02:13:04+08:00
---

# audio watermark removal

[deep audio prior](https://github.com/adobe/Deep-Audio-Prior)
Audio Source Separation Without Any Training Data.

DAP can also be successfully applied to address audio watermarker removal with co-separation. Given 3 sounds with audio watermarkers, our cosep model can generate 3 individual music sounds and the corresponding watermarker.

audio watermark may exists in sub or ultra frequencies. use ffmpeg to remove it

process audio with some equalizer
