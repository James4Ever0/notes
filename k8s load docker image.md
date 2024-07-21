---
title: k8s load docker image
created: '2024-07-21T14:35:03.614Z'
modified: '2024-07-21T15:03:46.960Z'
---

# k8s load docker image

first of all, you can build and upload docker image to registry.

```bash
docker login
docker build -t <username>/<imagename>:<tag> -f <dockerfile> <resource_path>
docker push <username>/<imagename>:<tag>
```

you can upload to docker.io or microk8s provided local registry.

https://microk8s.io/docs/registry-built-in

```bash
# for microk8s the registry address is localhost:32000
docker tag <imagename> <registry_addr>/<imagename>
docker push <registry_addr>/<imagename>
```

you can also build image with minikube:

```bash
minikube image build -t <imagename> -f <dockerfile_path> <resource_path>
```

---

load image exported with `docker save <image>:<tag>`

```bash
# ref: 
minikube image load
```

