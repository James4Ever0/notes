---
created: 2024-04-03T08:03:28+08:00
modified: 2024-04-03T08:06:34+08:00
---

# Nmap service resolution

There are two files we are interested in.
- `nmap-services`: a list of well known services by port
- `nmap-service-probes`: matching rules for detecting service by response

The default service to port mapping in Python `socket` module is incomplete.
