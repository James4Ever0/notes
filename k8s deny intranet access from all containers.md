---
title: k8s deny intranet access from all containers
created: '2024-07-20T17:14:43.000Z'
modified: '2024-07-21T08:21:21.872Z'
---

# k8s deny intranet access from all containers

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

https://kubernetes.io/docs/reference/command-line-tools-reference/kube-controller-manager/

https://docs.k3s.io/security/hardening-guide

for `microk8s`, edit `/var/snap/microk8s/current/args/kube-controller-manager`

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
            cidr: 0.0.0.0/0
            except:
              - 10.0.0.0/8
              - 172.16.0.0/12
              - 192.168.0.0/16
```
