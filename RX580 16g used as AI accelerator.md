---
title: RX580 16g used as AI accelerator
created: '2023-12-09T13:47:07.765Z'
modified: '2024-03-10T13:35:33.684Z'
---

# RX580 16g used as AI accelerator

codename: `gfx803`

you may have to [build it yourself](https://github.com/tsl0922/pytorch-gfx803)

---

If you want to use this beefy GPU for computation, then either prepare a suitable ventalized desktop frame or use external GPU connected by OCuLink, which can be found on latest MiniPCs and laptops.

---

Your integrated GPU `gfx90c` [can]() be used for AI.

To run it without container, you build it with codename `gfx900`.

Either way, you need to specify `export HSA_OVERRIDE_GFX_VERSION=9.0.0`.

---

Currently it is not possible to run `ollama` on `gfx90c`.

You can disable GPU by `export HSA_OVERRIDE_GFX_VERSION=1`.

Since latest `ollama` accesses ROCm, run it with `root` account.

If you want to run `ollama` on other GPUs, you may have to compile it yourself, with parameters like
