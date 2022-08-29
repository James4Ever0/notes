---
title: on building the lua torch library
created: '2022-08-26T14:07:07.000Z'
modified: '2022-08-29T03:36:36.726Z'
---

# on building the lua torch library
## im2latex-tensorflow sucks, looking for alternatives

**training on gpu is intensive and will occasionally burn hardware if not careful, doing this on kaggle or modify the software to stop training when gpu goes hot, but we are using trainer here**

[harvard nlp showcase](http://nlp.seas.harvard.edu/code/)

for those doesn't provide pretrained models:

[im2latex](https://github.com/guillaumegenthial/im2latex) in tensorflow, with makefile support, run on tensorflow v1 and python3

[im2latex](https://github.com/luopeixiang/im2latex) in pytorch, more recent. the dataset has relocated to [here](https://zenodo.org/record/56198#.YwtB9PcRU5t) according to [official website](https://im2markup.yuntiandeng.com/)

## install or run python2.7 to run [im2latex-tensorflow](https://github.com/ArminKaramzade/im2latex)

you may need to adapt our modified code to load the weights and test the result against our image.

it is reported the performance is poor. maybe it does not worth trying.

download tensorflow 0.12.0 for macos [here](https://pypi.org/project/tensorflow/0.12.0/#files)

visit [here](https://docs.conda.io/en/latest/miniconda.html) to get all miniconda installers

to install on macos, download the installer [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg)

some tutorial [here](https://blog.balasundar.com/install-older-versions-of-python-using-miniconda-on-mac-m1) about libmagic as bonus tips

```bash
CONDA_SUBDIR=osx-64 conda create -n py27 python=2.7  # include other packages here
 
# ensure that future package installs in this env stick to 'osx-64'
conda activate py27
conda config --env --set subdir osx-64
```

after that, do this to get pip on python2.7 (rosetta2)
```bash
curl https://bootstrap.pypa.io/pip/2.7/get-pip.py -o get-pip.py
python get-pip.py
```

install tensorflow version below 1, and doing this can be far more easier on linux. maybe we should do this in conda virtual enviorment to prevent conflicts.

## we are doing this for the original lua implementation of [im2markup](https://github.com/harvardnlp/im2markup)

**it works!**

download libcudnn5 for torch

remember to activate torch enviorment by exporting the path to some shell script

difference between cudamalloc and cudamallocasync, and that's some copying and pasting about some generalized template of memory manager function

qt4 uses CRLF so convert all text files using dos2unix

need to hack qt4 files to build qt4

hack luarocks to allow install from local spec file and download repo from github via https

hack some lua torch file to be compatible with cuda11

about c++ tweaks:

add '+' to force type inference

force type conversion by using brackets

some macro to disable some blocks of code
