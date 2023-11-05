---
title: Home Assistant Installation & Setups
created: '2023-11-05T18:51:22.434Z'
modified: '2023-11-05T18:57:48.390Z'
---

# Home Assistant Installation & Setups

Fully functional HA mainly comes into two forms: flashable supervised `.iso` images, and virtual machines (not docker container).

Supervisor need to be 

Since its heavy reliance on docker and github, one need to use [OpenClash]() along with [OpenWrt]() flashed in one dedicated router like [NanoPi R2S]() to smooth the installation process.

You can enter [debug mode](), change the following files:

Some files like `/etc/docker/daemon.json`, `/etc/hosts` cannot be changed after boot. You can change them before boot using card reader.
