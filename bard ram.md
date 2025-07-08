boot step stuck at ram related codes usually means ram or cpu issues

chech for loose cpu heatsink screws, loose rams

If problem only happens after boot, you may block bad ram via grub option. you can scan for bad ram sectors via memtest86+

specify memtest kernel option may mitigate this issue

---

you may block bad sectors via e2fsck on ext4 file system, but too many of them usually means your disk is unfixable.