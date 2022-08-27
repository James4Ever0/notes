---
title: on building the lua torch library
created: '2022-08-26T14:07:07.000Z'
modified: '2022-08-27T15:20:57.736Z'
---

# on building the lua torch library

## install or run python2.7 to run [im2latex-tensorflow](https://github.com/ArminKaramzade/im2latex)

to install on macos, download the installer [here](https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.pkg)

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
