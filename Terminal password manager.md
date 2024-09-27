---
title: Terminal password manager
created: '2024-09-27T16:34:00.269Z'
modified: '2024-09-27T16:36:35.152Z'
---

# Terminal password manager

install `pass`:

```bash
apt install -y pass
```

create and delete a gpg key:

```bash
gpg --quick-gen-key <user_id>
gpg --delete-secret-and-public-keys <user_id> 
```

initialize, create and view password:

```bash
pass init
pass insert <keyname>
pass show <keyname>
```
