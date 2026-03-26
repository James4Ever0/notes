---
created: 2026-03-27T00:01:47+08:00
modified: 2026-03-27T00:41:02+08:00
---

# capture virtual display screenshot in swm

you can get current focused app as well from the adb side.

question: what does scrcpy-server does when we push it to android phone? how can we run it with root permission? can we run scrcpy client on android?

```bash
# using scrcpy 3.3.1
# first get all display ids

swm scrcpy --list-display

# then process each display id, take screenshot

timeout 2 swm scrcpy --display-id 0 --no-control --no-audio --no-playback --no-window --time-limit 1 --record screenshot.mp4

# finally use ffmpeg to get the screenshot

ffmpeg -i input_video.mp4 -frames:v 1 screenshot.png
```
