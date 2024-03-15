---
title: 'AI assisted content creation, gameplay video recording, trending topics'
created: '2024-03-10T14:08:10.638Z'
modified: '2024-03-15T08:31:45.042Z'
---

# AI assisted content creation, gameplay video recording, trending topics

Kdenlive has many video editing features, like automatic scene split, video stabilzation.

---

To extract existing hard-coded subtitles in videos, use [videosubfinder](https://sourceforge.net/projects/videosubfinder/), which is used in Cradle, an Red Dead Redemption II agent.

---

To check if audio is recorded, we can view amplitude instead of hearing.

```bash
ffprobe -f lavfi -i "amovie=<audio_or_video_filepath>,astats=metadata=1:reset=1" -show_entries frame=pkt_pts_time:frame_tags=lavfi.astats.Overall.RMS_level -of default=noprint_wrappers=1:nokey=1 -sexagesimal -v error
```

---

[AI toolbox](https://github.com/OceanNg529/allAI): a comprehensive content creation toolbox with links to related projects

---

Use `streamlit` to write interactive interfaces for video labeling, editing and registration, tracking viewer counts.

Grided image can be used for image selection prompting and image condensation, putting multiple images together to save processing power during tasks like video rating.

When you play video games on low end devices, you can tune down the resolution and image quality, to ensure 30 FPS.

If you change screen resolution during screen recording, you might lose your view.

Train a video grading system with recent and relevant video grades, and when evaluating put grading context into the prompt, thus generalize the system.

Get system predicted labels of video content to train a label predictor out of it, providing necessary context of test video for improving the grading system accuracy.

[Taskmatrix](https://github.com/moymix/TaskMatrix) is a multimodal agent framework suitable for multiple types of image editing, using diffusion models.

You can learn what the viewers are craving about via recommendation engines, dynamic posts and latest bangumi releases.

Post the same content across multiple platforms to increase view counts.
