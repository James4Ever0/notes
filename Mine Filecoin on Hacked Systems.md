---
created: 2024-05-07T21:42:46+08:00
modified: 2024-05-07T21:50:54+08:00
---

# Mine Filecoin on Hacked Systems

Usually it takes little effort to upload arbitrary files and data to target server than directly getting shell access. This means you can use it as remote storage for mining Filecoin.

To minimize delay you may consider installing the miner to target server but this also exposes your info and make yourself traceable. You may consider upload encrypted version of file in order to cover up your intent.

You can design a custon virtual filesystem which utilizes multiple backups and ranking system for selecting providers and storing data reliably.

---

Similarly you can mask your intent significantly by breaking down your miner source code into multiple parts, only delegate the most computational intensive part to the remote machine and offload the upload part to other lightweight servers.

You can use WASM for building web miners.
