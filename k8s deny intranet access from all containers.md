---
created: 2024-07-21T01:14:43+08:00
modified: 2024-07-21T01:19:00+08:00
---

# k8s deny intranet access from all containers

make sure you have a networkpolicy enabled cni first. usually included but be careful with minikube since that is a different story

apply these configs with `kubectl apply -f <config_path>`

interact with `kubectl exec hello-world -it -- /bin/sh`

pod config:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: hello-world
  labels:
    app: hello-world
spec:
  containers:
    - name: alpine-container
      image: alpine:3.7
      command: ["tail", "-f", "/dev/null"]
  dnsConfig:
    nameservers:
      - 8.8.8.8

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
