---
title: 'Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots'
created: '2023-01-09T03:22:12.950Z'
modified: '2023-01-10T20:16:59.551Z'
---

# Everything you need to startup your media project: viral video generator, viral video analyzer, trend analyzer, automated email account registration, download only a portion of video, peek video screenshots

## Viral videos

### Video editors

#### [Gifcurry](https://github.com/lettier/gifcurry)

Adding text to video, has typing effects, written in haskell. You can add `-m` flag to export video instead of GIF.

#### [Backgroundremover](https://github.com/nadermx/backgroundremover)

A commandline tool powered by torch, removing background from images and video

#### [Moviepy](https://github.com/Zulko/moviepy) most loved commandline video editor?

There are some [cool text effects](https://zulko.github.io/moviepy/examples/moving_letters.html) called "Text with moving letters" (PPT-like), and a [dancing video generator](https://zulko.github.io/moviepy/examples/dancing_knights.html) based on tempo finder and video loop maker. The [Star-Wars Text Effect](https://zulko.github.io/moviepy/examples/star_worms.html) reminds me of easing functions used with page scrolling.

### Data collect/analyze

#### [Youtube Viral Video Machine Learning Analysis](https://github.com/gdemos01/yttresearch-machine-learning-algorithms-analysis)

Refer to this [document](https://github.com/gdemos01/yttresearch-machine-learning-algorithms-analysis/blob/master/Documentation/Thesis.pdf) for details in data collection and machine learning methods.

Dataset creation:

Monitoring video right at the time it is posted, monitor for a few days, calculate features, then wait for a month or two (it must stablize then), judge the video is viral or not by view counts.

Using multiple machine learning techniques, there are some top features matters the most for viral video forecasting (though you can derive your own by collecting more data (like the follower-view theory if applied), and beware if your video all sucks, you may not get an accurate model out of your data alone):

| Feature Importance | Feature Name | Importance|
|---|---|---|
| 1                  | views_acc | 12%|
| 2                  | views_1 | 11%|
| 3                  | ageRatioReviews_1 | 9%   |
| 4                  | video_duration| 9%  |
| 5                  | comments_1| 5%|
| 6                  | channel_uploads|5%|
| 7                  | ageRatioLikes_1 | 4%|
| 8                  | comments_acc | 4% |
| 9                  | channel_views| 4% |

#### [ViralCaster](https://github.com/jjbreen/ViralCaster)

[TitleParser.py](https://github.com/jjbreen/ViralCaster/blob/master/TitleParser.py) analyses views along with words, getting the most "popular" word or word combinations. It has demo data. It generates "max" "min" "mean" views related to single word or word combinations.

#### [Predictube](https://github.com/dubstack/Predictube)

[peak_detection.py](https://github.com/dubstack/Predictube/blob/master/predictube/analyze/peak_detection/peak_detection.py) use daily view count to categorize and identify trends. "MonoIncr" might be our desired category.

#### 
