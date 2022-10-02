---
title: scan this picture and index the whole video/document/ppt/textbook!
created: 2022-08-25T00:02:15+08:00
modified: 2022-10-03T03:05:08+08:00
---

# scan this picture and index the whole video/document/ppt/textbook!

## non-max suppression in combining similar bounding boxes

the lib:
```python
from imutils.object_detection import non_max_suppression
```

## basically greek letters

maybe you can document another great range of symbols by just enabling the system to search in greek?

could also search among math symbols, do [math ocr](https://github.com/chungkwong/MathOCR).

## kindly reminders

when building python c++ libraries without xcode, please add commandline header files like this:

in order to have this during build:
```/Library/Developer/CommandLineTools/Library/Frameworks/Python3.framework/Versions/3.8/Headers/Python.h```

we need to do:
```bash
ln -s /Library/Developer/CommandLineTools /Applications/Xcode.app/Contents/Developer
```

## search by image instead of cranking latex out

### image search libraries

character level optical char segmentation called [chargrid ocr](https://github.com/akkshita/chargrid-ocr)

[image match used for copyright violation detection, using phash algorithm](https://github.com/ProvenanceLabs/image-match)

## get the latex out

### first detect the location of math formula

[scanning single shot detection for math formulas](https://github.com/MaliParag/ScanSSD)

[dataset for math symbol detection](https://github.com/MaliParag/TFD-ICDAR2019)

[detect different part of document with yolov3](https://github.com/Binhhp/detector-scan-image)

[math expression detection](https://github.com/divya1211/math-expression-detection)

### next find the tool for picture to latex conversion

新开源的Python工具——Pix2Text (P2T)，目标是 Mathpix 的Python开源替代品，现在可以识别截图中的数学公式并转换为Latex表示，也可以识别图片中的中英文文字。在线Demo： https://huggingface.co/spaces/breezedeus/pix2text 。 Github: https://github.com/breezedeus/pix2text ，Gitee: https://gitee.com/breezedeus/pix2text 。

[attention based math ocr](https://github.com/DexterLei/Math-OCR)

[gui of image2latex](https://github.com/yixuanzhou/image2latex)

[im2latex-tensorflow](https://github.com/ritheshkumar95/im2latex-tensorflow)

[im2markup with only nvidia support](https://github.com/harvardnlp/im2markup/) using torch, model for latex conversion can be found [here](https://im2markup.yuntiandeng.com/model/latex/final-model)

[deeplearning picture to latex](https://github.com/kingyiusuen/image-to-latex)

[pix2tex](https://github.com/lukas-blecher/LaTeX-OCR)

[using pix2tex](https://pix2tex.readthedocs.io/en/latest/pix2tex.html#pix2tex-api-package)

[中文公式 手写公式识别 需要进一步训练](https://github.com/LinXueyuanStdio/LaTeX_OCR_PRO)

[中文 手写 pytorch版本](https://github.com/qs956/Latex_OCR_Pytorch)

## mask latex area and get conventional things out

[easyocr with pytorch support](https://github.com/JaidedAI/EasyOCR)

## search the formula

[formula search based on sympy](https://github.com/AzizAlqasem/FormulaLab)

can we render latex to picture with sympy?

[latex search engine](https://github.com/kerryz/latexsymbolsearch)
