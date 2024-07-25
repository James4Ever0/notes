---
created: 2024-07-24T07:55:14+08:00
modified: 2024-07-25T14:50:18+08:00
---

# install kubevirt

do not install it on microk8s

---

`VirtualMachine` is like `Deployment` while `VirtualMachineInstance` is like `Pod`

---

export kubeconfig file path to `~/.bashrc`

```bash
export KUBECONFIG=<kubeconfig_filepath>
```

download and modify the manifests

```bash
# prefer ustc and azure mirrors of quay.io

export VERSION=$(curl -s https://api.github.com/repos/kubevirt/kubevirt/releases | grep tag_name | grep -v -- '-rc' | head -1 | awk -F': ' '{print $2}' | sed 's/,//' | xargs)
    
echo $VERSION

curl -OLk https://github.com/kubevirt/kubevirt/releases/download/${VERSION}/kubevirt-operator.yaml
curl -OLk https://github.com/kubevirt/kubevirt/releases/download/${VERSION}/kubevirt-cr.yaml

export VERSION=$(curl -s https://api.github.com/repos/kubevirt/containerized-data-importer/releases | grep tag_name | grep -v -- '-rc' | head -1 | awk -F': ' '{print $2}' | sed 's/,//' | xargs)

curl -LkO https://ghproxy.net/github.com/kubevirt/containerized-data-importer/releases/download/$VERSION/cdi-operator.yaml
curl -LkO https://ghproxy.net/github.com/kubevirt/containerized-data-importer/releases/download/$VERSION/cdi-cr.yaml
```

check if it works

```bash
kubectl get pods -n kubevirt
kubectl get vmi
```

install virtctl 

```bash
# get the download address from: https://github.com/kubevirt/kubevirt/releases/
curl -LkO <download_address>
sudo mv <downloaded_binary> /usr/bin/virtctl
sudo chmod +x /usr/bin/virtctl
```

create vm (already with tun device inside)

```yaml
# init_vm.yaml
apiVersion: kubevirt.io/v1
kind: VirtualMachine
metadata:
  name: <vm_name>
spec:
  runStrategy: Always
  template:
    spec:
      terminationGracePeriodSeconds: 30
      dnsConfig:
        nameservers:
          - 8.8.8.8
      domain:
        resources:
          requests:
            memory: 1024M
        devices:
          disks:
          - name: containerdisk
            disk:
              bus: virtio
          - name: emptydisk
            disk:
              bus: virtio
          - disk:
              bus: virtio
            name: cloudinitdisk
      volumes:
      - name: containerdisk
        containerDisk:
          image: kubevirt/fedora-cloud-container-disk-demo:latest
      - name: emptydisk
        emptyDisk:
          capacity: "2Gi"
      - name: cloudinitdisk
        cloudInitNoCloud:
          userData: |-
            #cloud-config
            password: fedora
            chpasswd: { expire: False }
```
