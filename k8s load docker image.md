---
title: k8s load docker image
created: '2024-07-21T14:35:03.614Z'
modified: '2024-07-21T15:36:49.808Z'
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
# ref: https://minikube.sigs.k8s.io/docs/commands/image/
# remember to set a tag to the image imported
# or set the imagePullPolicy to Never
# ref: https://iximiuz.com/en/posts/kubernetes-kind-load-docker-image/

minikube image load <image_filepath>/<docker_image_name>

microk8s images import <image_filepath>
microk8s ctr image import <image_filepath>

k3s ctr image import <image_filepath>
```

https://blog.scottlowe.org/2020/01/25/manually-loading-container-images-with-containerd/

https://docs.k3s.io/installation/registry-mirror#pushing-images

---

you can also configure k8s to use docker as container runtime instead.

https://github.com/canonical/microk8s/issues/287

https://docs.k3s.io/advanced#using-docker-as-the-container-runtime

