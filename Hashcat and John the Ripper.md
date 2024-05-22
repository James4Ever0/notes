---
title: Hashcat and John the Ripper
created: '2024-05-22T08:11:34.826Z'
modified: '2024-05-22T08:13:59.671Z'
---

# Hashcat and John the Ripper

Hashcat does not support yescript, which is a very slow hashing algorithm developed by some member in JtE. It can crack common password hashes quickly with GPU.

There are plenty of mask generation engines for hashcat. Find them with `apt`.

John the Ripper only provides few formats by default. To get more formats, install `john-jumbo` instead.
