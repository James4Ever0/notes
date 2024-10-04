---
title: Migrate VM with non-ASCII name from ESXi to PVE
created: '2024-10-03T10:21:54.244Z'
modified: '2024-10-04T16:05:34.518Z'
---

# Migrate VM with non-ASCII name from ESXi to PVE

First, you need to ssh into ESXi, 


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

