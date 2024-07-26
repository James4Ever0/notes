---
created: 2024-07-26T22:28:15+08:00
modified: 2024-07-26T22:32:57+08:00
---

# copy encrypted linux install to new disk

perform a bit-by-bit clone to new disk

```bash
sudo dd if=<source_disk_device> of=<target_disk_device> bs=4M status=progress
```

remember to remove the old disk and enlarge the new disk in gui
