---
title: Wake on LAN
created: '2024-09-21T12:10:28.000Z'
modified: '2024-09-22T04:45:17.649Z'
---

# Wake on LAN

If there is no light on the ethernet port when your computer is suspended or off, then there is no way to WOL no matter how.

Try the following commands to enable WOL/WOWLAN:

```bash
ethtool -s <if_name> wol g

nmcli con mod <eth_conn_name>  802-3-ethernet.wake-on-lan magic
nmcli con mod <eth_conn_name>  802-3-ethernet.auto-negotiate on

nmcli con mod <wireless_conn_name> 802-11-wireless.wake-on-wlan magic
nmcli con mod <wireless_conn_name> 802-11-wireless.powersave off

systemctl restart NetworkManager

iw phy <phy_name> wowlan enable

reboot
```

To initiate magic packets:

```bash
# etherwake does not work as expected
wakeonlan -i <target_ip> <target_mac>
# the broadcast ip ends with 255
wakeonlan -i <intranet_broadcast_ip> <target_mac>
```

To receive magic packets:

```bash
# bsd netcat
nc -u -l 9 | xxd
# gnu netcat
nc --udp --listen --local-port=9 --hexdump
```

To suspend a machine:

```bash
echo mem > /sys/power/state
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
