---
created: 2024-07-26T22:28:15+08:00
modified: 2024-07-30T10:26:10+08:00
---

# copy encrypted linux install to new disk

perform a bit-by-bit clone to new disk

```bash
sudo dd if=<source_disk_device> of=<target_disk_device> bs=4M status=progress
```

remember to detach the old disk and enlarge the system partition on new disk

---

in kde partiton manager, you can resize both the encrypted partition and the root partition as well as the swap partition (install tools prompted by name)

follow the guide here to do it manually:

https://wiki.archlinux.org/title/Resizing_LVM-on-LUKS
