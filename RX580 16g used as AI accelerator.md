---
title: RX580 16g used as AI accelerator
created: '2023-12-09T13:47:07.765Z'
modified: '2024-03-19T00:59:45.252Z'
---

# RX580 16g used as AI accelerator

The codename: `gfx803`

You may have to [build it yourself](https://github.com/tsl0922/pytorch-gfx803)

Setup environmental parameters and install drivers:

```bash
sudo echo ROC_ENABLE_PRE_VEGA=1 >> /etc/environment
sudo echo HSA_OVERRIDE_GFX_VERSION=8.0.3 >> /etc/environment
# reboot

wget https://repo.radeon.com/amdgpu-install/22.40.3/ubuntu/focal/amdgpu-install_5.4.50403-1_all.deb
sudo apt install ./amdgpu-install_5.4.50403-1_all.deb
sudo amdgpu-install -y --usecase=rocm,hiplibsdk,mlsdk

sudo usermod -aG video $LOGNAME
sudo usermod -aG render $LOGNAME

# verify
rocminfo
clinfo
```

Build torch:

```bash
git clone https://github.com/pytorch/pytorch.git -b v1.13.1
cd pytorch
export PATH=/opt/rocm/bin:$PATH ROCM_PATH=/opt/rocm HIP_PATH=/opt/rocm/hip
export PYTORCH_ROCM_ARCH=gfx803
export PYTORCH_BUILD_VERSION=1.13.1 PYTORCH_BUILD_NUMBER=1
python3 tools/amd_build/build_amd.py
USE_ROCM=1 USE_NINJA=1 python3 setup.py bdist_wheel
pip3 install dist/torch-1.13.1-cp310-cp310-linux_x86_64.whl
```

---

If you want to use this beefy GPU for computation, then either prepare a suitable ventalized desktop frame or use external GPU connected by OCuLink, which can be found on latest MiniPCs and laptops.

---

Your integrated GPU `gfx90c` [can](https://github.com/ROCm/ROCm/issues/1743) be used for AI.

To run it without container, you build it with codename `gfx900`.

Either way, you need to specify `export HSA_OVERRIDE_GFX_VERSION=9.0.0`.

Run a container:

```bash
sudo docker run --rm -it --cap-add=SYS_PTRACE --security-opt seccomp=unconfined --device=/dev/kfd --device=/dev/dri --group-add video --ipc=host --shm-size 8G rocm/pytorch:latest
```

---
If you want to run `ollama` on AMD GPUs, you must install ROCm 6.

Additinally if the card is [`gfx90c`](https://github.com/ROCm/ROCm/issues/2774), you need to run `export HSA_ENABLE_SDMA=0`.

You can get current ROCm version by `dpkg -l | grep -i rocm`.

You can disable GPU by `export HSA_OVERRIDE_GFX_VERSION=1`.

Since latest `ollama` accesses ROCm, run it with `root` account.

---

In order to circumvent BIOS VRAM limitation for APU, you can follow the instruction [here](https://typeof.pw/archives/pytorch-on-apu-vram).

Related repos:

- [torch-apu-helper](https://github.com/pomoke/torch-apu-helper)
- [force-host-alloction-APU](https://github.com/segurac/force-host-alloction-APU)

