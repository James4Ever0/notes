---
title: Wake on LAN
created: '2024-09-21T12:10:28.000Z'
modified: '2024-09-22T03:52:20.292Z'
---

# Wake on LAN

If there is no light when your computer is suspended or off, then there is no way to WOL no matter how.

Try following commands:
```bash
ethtool -s <if_name> wol g

nmcli con mod <eth_conn_name>  802-3-ethernet.wake-on-lan magic
nmcli con mod <wireless_conn_name> magic

iw phy <phy_name> wol on
```
---

References:

https://wiki.archlinux.org/title/Wake-on-LAN

https://en.ittrip.xyz/linux/wake-on-lan-linux

https://www.pcmag.com/how-to/turn-on-computer-from-across-the-house-with-wake-on-lan

https://hackernoon.com/wake-on-lan-through-the-internet-491817e2dd41

https://www.cyberciti.biz/faq/configure-wireless-wake-on-lan-for-linux-wifi-wowlan-card/

---

Some devices provide USB wakeup functionality in BIOS, usually keyboard based. You need to plug it in while awake.

To utilize this you need to use a device like OrangePi H3 or Raspberry Pi Zero with USB slave capable ports, such as USB-C, micro-USB etc. Some device like OneCloud or Raspberry Model A has a USB-A slave port.
