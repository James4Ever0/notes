---
created: 2026-03-27T00:01:47+08:00
modified: 2026-03-27T00:07:17+08:00
---

# capture display screenshot in swm

```bash
# first get all display ids

swm scrcpy --list-display

# then process each display id, take screenshot

timeout 2 swm scrcpy --display-id 0 --no-control --no-audio --no-playback --record screenshot.mp4

# finally use ffmpeg to get the screenshot

ffmpeg -i input_video.mp4 -frames:v 1 screenshot.png
```
