---
title: generate publickey again with rsa private key
created: '2022-09-25T03:09:54.074Z'
modified: '2022-09-25T04:02:52.154Z'
---

# generate publickey again with rsa private key

cause the deploy public key does not allow duplicate public key, causing trouble for us to use the git repo sync tool.

```bash
PRIVATE_KEY_PATH=
PUBKEY_PATH=
ssh-keygen -y -f $PRIVATE_KEY_PATH > $PUBKEY_PATH
```
