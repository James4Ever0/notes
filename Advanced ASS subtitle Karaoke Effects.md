---
tags: [dog video, karaoke, lyric effects, music video, pets video, project, pyjom, subtitle, video effects, video generator, video with bgm]
title: Advanced ASS subtitle Karaoke Effects
created: '2022-07-10T15:56:16.000Z'
modified: '2022-08-20T15:20:05.313Z'
---

# Advanced ASS Subtitle Karaoke Effects

## lrc files

lrc files only have start time but no end time.
we group parallel lyrics by time, if they are close enough we make it into a group.

groups act as time separators.

[all ass file tags, for custom karaoke effects creation](https://web.archive.org/web/20200722050630/http://docs.aegisub.org/3.2/ASS_Tags/)

play ass file with mpv on demo video, full screen, no audio:
```bash
rootpath=/Users/jamesbrown/desktop/works/pyjom_remote/
mpv --fs --no-audio --sub-file="$rootpath/tests/karaoke_effects/pyonfx_test/examples/2 - Beginner/Output.ass" "$rootpath/samples/video/karaoke_effects_source.mp4"
```

create karaoke effects
https://github.com/Kagu-chan/FXSpindle

karaoke effects
https://github.com/Youka/NyuFX
[pyonfx code](https://github.com/CoffeeStraw/PyonFX)
recommend to use effect `2 beginners -> 3 variants` in examples, while `3 advanced -> 2 testing pixels` as reference (more advanced but incomplete, and might be very intensive)
[pyonfx documentation](https://pyonfx.readthedocs.io/en/latest/quick%20start.html#starting-out)
https://github.com/logarrhythmic/karaOK

aegisub and its plugins
https://github.com/Myaamori/aegisub-cli
https://github.com/qwe7989199/Lyric-Importer-for-Aegisub
https://github.com/qwe7989199/aegisub_scripts
https://github.com/lyger/Aegisub_automation_scripts
http://www.aegisub.org/

eyecandy create karaoke ass files:
https://github.com/Alquimista/Eyecandy-py

create karaoke effects subtitle with lrc file, support chinese
https://github.com/DYY-Studio/lrc2ass_py3
