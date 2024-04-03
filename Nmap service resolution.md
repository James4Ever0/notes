---
created: 2024-04-03T08:03:28+08:00
modified: 2024-04-03T08:35:00+08:00
---

# Nmap service resolution

There are two files we are interested in.
- `nmap-services`: a list of well known services by port
- `nmap-service-probes`: matching rules for detecting service by response

The default service to port mapping in Python `socket` module is incomplete.

```python
file_path = ...
for line in line_list:
    if line.startswith("#"):
        # it is a comment
        continue
    else:
        # process this line
        components = line.split('#')
```
