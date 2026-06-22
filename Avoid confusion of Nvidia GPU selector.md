---
created: 2026-06-22T15:43:09+08:00
modified: 2026-06-22T15:46:42+08:00
---

# Avoid confusion of Nvidia GPU selector

Use nvidia-smi -L to list GPU uuids

Use CUDA_VISIBLE_DEVICES=[uuid] for ollama daemon

Or run with docker --gpus '"devices=x"'

docker --gpus '"devices=[uuid]"'
docker -e NVIDIA_VISIBLE_DEVICES=x
