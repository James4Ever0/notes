---
title: Split PCI-E x16 into multiple small PCI-E channels
created: 2024-09-08T14:55:47+00:00
modified: 2024-09-14T10:56:09+08:00
---

# Split PCI-E x16 into multiple small PCI-E channels

For HUANANZHI F8D-Plus motherboard, in order to get three x16 splited, you configure like such:

BIOS:

IIO0_IOU2 x4x4 two M.2 slots
IIO0_IOU0 x8x8 two x8 slots for CPU1
IIO0_IOU1 x8x8 one x16 for CPU1

IIO1_IOU2 x8 one x8 for CPU2
IIO1_IOU0 x8x8 one x16 for CPU2
IIO1_IOU1 x8x8 one x16 for CPU2

Motherboard:

IIO1_IOU1
IIO1_IOU0
IIO1_IOU2

IIO0_IOU1
IIO0_IOU0-0
IIO0_IOU0-2
