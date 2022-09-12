---
title: use pyscenedetect dynamically in program
created: '2022-09-12T12:56:17.556Z'
modified: '2022-09-12T14:07:52.853Z'
---

# use pyscenedetect dynamically in program

对于单纯拼接起来的视频 这个算法就如同手术刀一样精准

首尾有可能有一两帧看起来不太对 但是可以通过调节start和end来修正

警惕频繁转场的视频 它们可能是属于同一个小片段的 但是如果不打乱顺序有可能会触发版权识别问题

即使选出来了可以使用的片段 对于同一个视频的制作过程 依旧要隔一段时间采样 **比如两个片段间隔至少5秒** 不要单纯的把所有片段一次性提取出来 避免内容重复和版权问题

当然对于有渐变 转场的视频 可能需要用其他的检测方法

```python
from scenedetect import open_video, SceneManager, split_video_ffmpeg
from scenedetect.detectors import ContentDetector
from scenedetect.video_splitter import split_video_ffmpeg

def split_video_into_scenes(video_path, threshold=27.0):
    # Open our video, create a scene manager, and add a detector.
    video = open_video(video_path)
    scene_manager = SceneManager()
    scene_manager.add_detector(
        ContentDetector(threshold=threshold))
    scene_manager.detect_scenes(video, show_progress=True)
    scene_list = scene_manager.get_scene_list()
    split_video_ffmpeg(video_path, scene_list, show_progress=True)
```
