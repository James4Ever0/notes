---
title: 'color transfer between images, histogram based style transfer'
created: '2022-09-17T07:20:21.210Z'
modified: '2022-09-17T07:28:17.780Z'
---

# color transfer between images, histogram based style transfer

图像调色风格转换 可以创建蹦迪特效 让视频或者图片五彩斑斓

[color transfer between images](https://github.com/jrosebr1/color_transfer)

```bash
pip install color_transfer
```

[official scikit-learn histogram matching](https://scikit-image.org/docs/dev/auto_examples/color_exposure/plot_histogram_matching.html)

```python
import matplotlib.pyplot as plt

from skimage import data
from skimage import exposure
from skimage.exposure import match_histograms

reference = data.coffee()
image = data.chelsea()

matched = match_histograms(image, reference, channel_axis=-1)

fig, (ax1, ax2, ax3) = plt.subplots(nrows=1, ncols=3, figsize=(8, 3),
                                    sharex=True, sharey=True)
for aa in (ax1, ax2, ax3):
    aa.set_axis_off()

ax1.imshow(image)
ax1.set_title('Source')
ax2.imshow(reference)
ax2.set_title('Reference')
ax3.imshow(matched)
ax3.set_title('Matched')

plt.tight_layout()
plt.show()
```

[histogram matching](https://pyimagesearch.com/2021/02/08/histogram-matching-with-opencv-scikit-image-and-python/)
