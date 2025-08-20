---
created: 2025-08-20T19:30:10+08:00
modified: 2025-08-20T20:27:48+08:00
---

# run pve in docker

https://www.xrgzs.top/posts/pve-in-docker

you can use nested virtualization to reduce risk of container/hypervisor failure.

For example, run docker in docker, docker in pve or run pve in pve. when the inner virtualization platform crashes, you can simply restart or reset the outer vm.

If by all means you want to restart the physical machine, make sure you use the reboot command instead of poweroff.

most importantly, make sure your machine has qualified and sufficient power supply, with enough and stable internal storage.

k8s might not provide enough single point stability. it is meant to be deployed at scale. you can repair failing nodes while using healthy ones.
