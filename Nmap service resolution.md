---
title: Nmap service resolution
created: '2024-04-03T00:03:28.000Z'
modified: '2024-04-03T03:22:56.265Z'
---

# Nmap service resolution

There are two files we are interested in.
- `nmap-services`: a list of well known services by port
- `nmap-service-probes`: matching rules for detecting service by response

The default service to port mapping in Python `socket` module is incomplete.

```python
# find that with mlocate
# file_path = '/usr/share/nmap/nmap-services'

file_path = "./nmap-services"

with open(file_path, 'r') as f:
    line_list = f.read().split('\n')

for line in line_list:
    if line.startswith("#"):
        # it is a comment
        continue
    else:
        # process this line
        content = line.split('#')[0].strip() # strip away comments
        components = content.split(" ")
        # must be three.
        assert len(components) == 3, f"abnormal component count for content: '{content}'"
```
