---
created: 2026-03-18T15:43:10+08:00
modified: 2026-03-18T15:44:40+08:00
---

# compile and install qman on ubuntu 22.04

system version:

ubuntu 22.04 x86_64

download qman source:

curl -o qman-1.5.1.zip  -Lk https://github.com/plp13/qman/archive/refs/tags/v1.5.1.zip
unzip qman-1.5.1.zip
cd qman-1.5.1

install dependency:

apt install cmake
apt install gcc
apt install pkg-config
apt install libncurses5-dev libncursesw5-dev
apt install zlib1g-dev
apt install libbz2-dev
apt install liblzma-dev
apt install libcunit1-dev
apt install groff

pipx install cogapp

change meson config:

at file meson_options.txt

option('libbsd',
  type: 'feature',
  value: 'enabled',
  description: 'Use libbsd-overlay'
)

build and install qman:

meson setup build/
cd build
meson compile
sudo meson install

reference urls:

https://github.com/plp13/qman/blob/main/doc/BUILDING.md

https://github.com/plp13/qman/blob/main/doc/OS_SPECIFIC.md
