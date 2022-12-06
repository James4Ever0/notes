---
title: raspberry pi tweaks
created: '2022-12-05T11:54:42.089Z'
modified: '2022-12-06T10:54:30.547Z'
---

# raspberry pi tweaks

default login: 
```
username: pi
password: raspberry
```

you've installed [raspap](https://raspap.com/) on this device. you use the default credentials. this shit will not connect to our wifi automatically, thus block your way of running docker containers on it with only macbook.

seriously? do you really need docker on macos? or just on raspberry pi?

change apt sources:
```bash
sudo sed -i 's|raspbian.raspberrypi.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|mirrordirector.raspbian.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|archive.raspbian.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|archive.raspberrypi.org/debian|mirrors.ustc.edu.cn/archive.raspberrypi.org/debian|g' /etc/apt/sources.list.d/raspi.list
```

sharing network:

```bash
ssh -R 1080 pi@10.42.0.33
```

install packages:

```bash
sudo apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1080/"  -o Acquire::Check-Valid-Until=false -o Acquire::Check-Date=false update --allow-releaseinfo-change

sudo apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1080/"  -o Acquire::Check-Valid-Until=false -o Acquire::Check-Date=false upgrade -y
```
