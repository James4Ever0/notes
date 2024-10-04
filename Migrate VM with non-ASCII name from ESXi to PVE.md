---
title: Migrate VM with non-ASCII name from ESXi to PVE
created: '2024-10-03T10:21:54.244Z'
modified: '2024-10-04T16:06:55.756Z'
---

# Migrate VM with non-ASCII name from ESXi to PVE

Relevent file: `/usr/share/perl5/PVE/Storage/ESXiPlugin.pm`

When importing VM from ESXi with non-ASCII names, it will first incorrectly parse the disk name within the `.vmx` file, then in the log it will show that the import path is broken and seems to be decoded twice with non-UTF8 codecs.

First find the VM files in SSH in some path like `/vmfs/volumes/<uuid>/`, rename the folder with an ASCII name then perform the following commands:

```bash
cd <new_folder>

# rename all files
ls -1 | awk '{new_var = $1; sub("<non_ascii_name>", "<ascii_name>"); print "mv " new_var " " $0 }' | awk -I bash -c 'abc'

# change all paths within vmdk/vmx config files
ls | grep -E '.(vmdk|vmx)' | grep -v flat | grep -v sesparse | xargs -Iabc sed -i 's/<non_ascii_name>/<ascii_name>/g' abc
```

Then unregister the old VM, register the new VM and import normally.

---

You can add a line `export PERL_UNICODE=SDA` into `/etc/profile` instead.

Related links:

https://devtut.github.io/perl/file-i-o-reading-and-writing-files.html

https://www.perl.com/pub/2012/05/perlunicook-make-all-io-default-to-utf-8.html/

Related issues:

https://lore.proxmox.com/pve-devel/42ea1a54-f553-4f5a-9892-722b1ad25058@proxmox.com/T/

https://bugzilla.proxmox.com/show_bug.cgi?id=5747

https://bugzilla.proxmox.com/show_bug.cgi?id=1909
---

This issue is caused by Perl.

The method `file_get_contents` in `/usr/share/perl5/PVE/Tools.pm` is not decoding the `.vmx` file as UTF8, which is the root cause of the problem.

