---
title: raspberry pi tweaks
created: '2022-12-05T11:54:42.089Z'
modified: '2022-12-06T15:09:18.686Z'
---

# raspberry pi tweaks

openai says i should edit `/etc/wpa_supplicant/wpa_supplicant.conf` like this to connect to 5G wifi:

```bash
network={
    ssid="<SSID>"
    psk="<password>"
    frequency=5180
}
```

also set frequency of wifi card like this:
```bash
sudo ifdown wlan0 && sudo ifup wlan0
sudo iw dev wlan0 set freq 5180
```

unplug ethernet, then we are golden.
```bash
traceroute baidu.com
```

how to check avaliable wifi ssids without `network-manager`:
```bash
sudo iwlist wlan0 scan | grep ESSID

```

default login (maybe not): 
```
username: pi
password: raspberry
```

in order to start `sshd`, `touch ssh` under `boot` partition

recover `dhcpcd` service:
```bash
sudo systemctl enable dhcpcd.service
sudo systemctl restart dhcpcd.service

```

config the password with `proot -S <path_to_rootfs> -b <boot_partition>:/boot -q qemu-arm /usr/bin/bash` and `passwd`

you've installed [raspap](https://raspap.com/) on this device. you use the default credentials. this shit will not connect to our wifi automatically, thus block your way of running docker containers on it with only macbook.

seriously? do you really need docker on macos? or just on raspberry pi?

change apt sources:
```bash
sudo sed -i 's|raspbian.raspberrypi.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|mirrordirector.raspbian.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|archive.raspbian.org|mirrors.ustc.edu.cn/raspbian|g' /etc/apt/sources.list
sudo sed -i 's|archive.raspberrypi.org/debian|mirrors.ustc.edu.cn/archive.raspberrypi.org/debian|g' /etc/apt/sources.list.d/raspi.list
```

using nmcli to scan and connect wifi

```bash
sudo nmcli dev wifi rescan
sudo nmcli dev wifi connect <SSID> password <PASSWORD>
```

sharing network:

```bash
ssh -R 1080 pi@10.42.0.33
```

edit `/etc/network/interfaces`:
```
auto lo

iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.42.0.33
netmask 255.255.255.0
gateway 10.42.0.1

allow-hotplug wlan0
auto wlan0

iface wlan0 inet dhcp
#wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
wpa-ssid "<SSID>"
wpa-psk "<PASSWORD>"
```
install packages:

```bash
sudo apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1080/"  -o Acquire::Check-Valid-Until=false -o Acquire::Check-Date=false update --allow-releaseinfo-change

sudo apt-get -o Acquire::http::proxy="socks5h://127.0.0.1:1080/"  -o Acquire::Check-Valid-Until=false -o Acquire::Check-Date=false upgrade -y
```
