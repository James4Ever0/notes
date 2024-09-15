---
title: Split PCI-E x16 into multiple small PCI-E channels
created: '2024-09-08T14:55:47.000Z'
modified: '2024-09-15T05:48:01.565Z'
---

# Split PCI-E x16 into multiple small PCI-E channels

For smaller motherboards there is no need to configure PCI-E spliting, otherwise you may not be able to use the GPU during boot (BIOS banner). If you do please reset the BIOS by physical motherboard jumpers.

You may still want to enable SR-IOV and Above 4G decoding in PCI-E settings.

---

For HUANANZHI F8D-Plus motherboard, in order to get three x16 splited, you configure like such:

BIOS:

```
IIO0_IOU2 x4x4 two M.2 slots
IIO0_IOU0 x8x8 two x8 slots for CPU1
IIO0_IOU1 x8x8 one x16 for CPU1

IIO1_IOU2 x8 one x8 for CPU2
IIO1_IOU0 x8x8 one x16 for CPU2
IIO1_IOU1 x8x8 one x16 for CPU2
```

Motherboard:

```
IIO1_IOU1
IIO1_IOU0
IIO1_IOU2

IIO0_IOU1
IIO0_IOU0-0
IIO0_IOU0-2
```
