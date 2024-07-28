---
title: k8s deny intranet access from all containers
created: '2024-07-20T17:14:43.000Z'
modified: '2024-07-28T10:10:29.893Z'
---

# k8s deny intranet access from all containers

constrain pod resources:

https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/

---

to manually exceed the ephermal storage limit run:

```bash
fallocate -l 10G /bigfile
```

the pod will be evicted, volume and container will be purged, but the record is not automatically removed.

to cleanup the mess one may run a scheduled job like:

```bash
while true;
do
	 microk8s kubectl delete pods --field-selector=status.phase=Failed
	 microk8s kubectl delete pods --field-selector=status.phase=Unknown
	 sleep 60
done
```

or configure implementation dependent `kube-controller-manager` startup argument `terminated-pod-gc-threshold=1`.

for `k3s` edit `/etc/rancher/k3s/config.yaml` like:

```yaml
kube-controller-manager-arg:
  - 'terminated-pod-gc-threshold=1'
```

for `microk8s`, edit `/var/snap/microk8s/current/args/kube-controller-manager`

references:

https://kubernetes.io/docs/reference/command-line-tools-reference/kube-controller-manager/

https://docs.k3s.io/security/hardening-guide

https://github.com/k3s-io/k3s/issues/10448

---

make sure you have a networkpolicy enabled cni first. usually included but be careful with minikube since that is a different story

apply these configs with `kubectl apply -f <config_path>`

interact with `kubectl exec <pod_name> -it -- /bin/sh`

deployment config:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello-world
  labels:
    app: hello-world
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hello-world
  template:
    metadata:
      labels:
        app: hello-world
    spec:
      containers:
        - name: alpine-container
          image: alpine:3.7
          command: ["tail", "-f", "/dev/null"]
          resources:
            limits:
               ephemeral-storage: "4Gi"
      dnsPolicy: None
      dnsConfig:
        nameservers:
          - 8.8.8.8
      terminationGracePeriodSeconds: 0

```

network policy config:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-intranet-egress
spec:
  podSelector:
    matchLabels:
      app: hello-world
  policyTypes:
    - Egress
  egress:
    - to:
        - ipBlock:
            cidr: ::/0
            except:
              - fc00::/7
              - fe80::/10
        - ipBlock:
            cidr: 0.0.0.0/0
            except:
              - 0.0.0.0/8
              - 10.0.0.0/8
              - 100.64.0.0/10
              - 169.254.0.0/16
              - 172.16.0.0/12
              - 192.168.0.0/16
 ```
