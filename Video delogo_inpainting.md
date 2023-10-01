---
tags: [dewatermark, remove watermark, royalty free, stub]
title: Video delogo_inpainting
created: 2022-05-31T06:13:58+00:00
modified: 2023-10-01T08:53:31+08:00
---

# Video delogo/inpainting

propainter remove watermark with tracking, entity segmentation


you can use [clip](https://github.com/LAION-AI/LAION-5B-WatermarkDetection) for watermark detection, but you don't know where. fuck. you better train it yourself.


[watermark detection model](https://wandb.ai/arkseal/laion-watermark-detection/artifacts/model/model/f88165bb9d2cbccc51b5)

```python
import timm
# all other pytorch imports

# Not used but necessary when running on images
transforms = T.Compose([
    T.Resize((256, 256)),
    T.ToTensor(),
    T.Normalize([0.485, 0.456, 0.406], [0.229, 0.224, 0.225])
])

# Create model
model = timm.create_model('efficientnet_b3a', pretrained=False, num_classes=2)
model.classifier = nn.Sequential(
    nn.Linear(in_features=1536, out_features=625),
    nn.ReLU(),
    nn.Dropout(p=0.3),
    nn.Linear(in_features=625, out_features=256),
    nn.ReLU(),
    nn.Linear(in_features=256, out_features=2)
)

# Load model weights
state_dict = torch.load('./model.pt')
model.load_state_dict(state_dict).eval().to(device)

# Sample Image
im = torch.randn(8, 3, 256, 256)
with torch.no_grad():
    pred = model(im)
syms = F.softmax(pred, dim=1).detach().cpu().numpy().tolist()
for water_sym, clear_sym in syms:
    # Do whatever you want with the watermark simlarity
```


## image local contrast enhancement, for removing hard-to-detect watermarks

maybe you can use the same trick (context preserving sliding window) from your search engine to here (image preprocessing)!

paddleocr识别效果最好 可以识别水印位置 以及文字

[Linear Contrast Stretching, HE, AHE, CLAHE of an image using matlab](https://github.com/Tejesh-Raut/Image-Linear-Contrast-Stretching-HE-AHE-CLAHE-Gray-Scale-Transformation)

Histogram Equalization (HE)

Adaptive Histogram Equalization (AHE)

Contrast Limited Adaptive Histogram Equalisation (CLAHE)

experiment path:

`pyjom/tests/remove_subtle_watermark_local_contrast_ocr`

[bing query for image local contrast](https://cn.bing.com/search?q=image+local+contrast&qs=n&form=QBRE&sp=-1&pq=image+local+contrast&sc=2-20&sk=&cvid=55BB4B6B6AE74F8FA6271F34C6201403&ghsh=0&ghacc=0&ghpl=)

[darktable lua api and scripting](https://darktable-org.github.io/luadocs/lua.scripts.manual/scripts/examples/api_version)

[darktable local contrast](https://docs.darktable.org/usermanual/development/en/module-reference/processing-modules/local-contrast/) darktable is an open-sourced photography postprocessing software

configurations:
```log
details: 443
highlights: 36
shadows: 25
midtone range: 0.16
```

[imagej clahe local contrast enhancement](https://imagej.net/plugins/clahe)

[l2uwe](https://github.com/tunai/l2uwe) L^2UWE: A Framework for the Efficient Enhancement of Low-Light Underwater Images Using Local Contrast and Multi-Scale Fusion written in matlab

[glcae](https://github.com/pengyan510/glcae) Global and Local Contrast Adaptive Enhancement for Non-uniform Illumination Color Images in python

[CNN-Based-X-ray-Morphological-Decomposition](https://github.com/tahanimadmad/CNN-Based-X-ray-Morphological-Decomposition-)

[github query for local image contrast](https://github.com/search?p=2&q=image+local+contrast&type=Repositories)

[image processing basics](https://github.com/Auggen21/image_processing_basics) Image Reading, writing, histogram, histogram equalization, local histogram equalization, low pass filter, high pass filter, geometrical transformation

[contrast normalization](https://github.com/Dinista/Contrast-Normalization) is an implementation that applies local contrast normalization to images in matlab

[contrast enhancement](https://github.com/topics/contrast-enhancement?l=python) as a github topic

[mclahe](https://github.com/VincentStimper/mclahe) NumPy and Tensorflow implementation of the Multidimensional Contrast Limited Adaptive Histogram Equalization (MCLAHE) procedure

[deepcontrast](https://github.com/AIM-Harvard/DeepContrast) A deep learning-based fully-automatic intravenous contrast detection tool for head-and-neck and chest CT scans.

[mirnetv2](https://github.com/swz30/MIRNetv2) (TPAMI 2022) Learning Enriched Features for Fast Image Restoration and Enhancement. Results on Defocus Deblurring, Denoising, Super-resolution, and image enhancement

[pymusica](https://github.com/lafith/pymusica) is a contrast enhancement approach involving non linear mapping of Laplacian pyramid.

[imWeightedThresholdedheq](https://github.com/Mamdasn/imWeightedThresholdedheq) attempts to enhance contrast of a given image or video by employing a method called weighted thresholded histogram equalization (WTHE).

[imagemagick wand local_contrast function](https://www.geeksforgeeks.org/wand-local_contrast-function-python/)

[dual gamma clahe](https://github.com/dimimal/dual_gamma_clahe) Automatic Contrast-Limited Adaptive Histogram Equalization With Dual Gamma Correction

[imhblpce](https://github.com/Mamdasn/imhblpce) attempts to enhance contrast of a given image by employing a method called HBLPCE.

[matlab localcontrast for image](https://ww2.mathworks.cn/help/images/ref/localcontrast.html)

## global contrast enhancement

[im2dhiseq](https://github.com/Mamdasn/im2dhisteq)  attempts to enhance contrast of a given image by equalizing its two dimensional histogram.

## previous research

deeplearning_inpainting:
https://github.com/Sanster/lama-cleaner

ffmpeg delogo:
https://www.jianshu.com/p/2eb1811b5fc6
https://hhsprings.bitbucket.io/docs/programming/examples/ffmpeg/blurring_unsharping/delogo_removelogo.html
https://securitronlinux.com/debian-testing/remove-a-logo-from-a-video-easily-with-ffmpeg/

opencv inpainting/blurring with edge blending

opencv morphlogical operations:
https://pyimagesearch.com/2021/04/28/opencv-morphological-operations/
