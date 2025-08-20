---
created: 2025-08-20T18:07:16+08:00
modified: 2025-08-20T18:10:03+08:00
---

# use ssh for clash

yaml template: (remember to indent the private key block)

```yaml
# reference: https://wiki.metacubex.one/en/config/proxies/ssh/
# check out the log before using any custom profile
proxies:
- name: "ssh-out"
  type: ssh
  server: <server_ip>
  port: <server_port>
  username: <username>
  private-key: |
     <privkey_multiline>
  host-key: []
  host-key-algorithms:
  - ssh-ed25519
  - ssh-rsa
```
