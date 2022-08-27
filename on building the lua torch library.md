---
title: on building the lua torch library
created: '2022-08-26T14:07:07.000Z'
modified: '2022-08-27T15:22:16.843Z'
---

# on building the lua torch library

## install or run python2.7 to run [im2latex-tensorflow](https://github.com/ArminKaramzade/im2latex)

to install on macos, download the installer [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg)

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

remember to activate torch enviorment by exporting the path to some shell script

difference between cudamalloc and cudamallocasync

qt4 uses CRLF so convert all text files using dos2unix

need to hack qt4 files to build qt4

hack luarocks to allow install from local spec file and download repo from github via https

hack some lua torch file to be compatible with cuda11

about c++ tweaks:

add '+' to force type inference

force type conversion by using brackets

some macro to disable some blocks of code
