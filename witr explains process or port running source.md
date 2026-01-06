---
created: 2026-01-06T09:27:43+08:00
modified: 2026-01-06T09:28:56+08:00
---

# witr explains process or port running source

https://github.com/pranshuparmar/witr

install:

```bash
# Download the binary
curl -fsSL https://github.com/pranshuparmar/witr/releases/latest/download/witr-linux-amd64 -o witr-linux-amd64

# Verify checksum (Optional, should print OK)
curl -fsSL https://github.com/pranshuparmar/witr/releases/latest/download/SHA256SUMS -o SHA256SUMS
grep witr-linux-amd64 SHA256SUMS | sha256sum -c -

# Rename and install
mv witr-linux-amd64 witr && chmod +x witr
sudo mv witr /usr/local/bin/witr

# Install the man page (Optional)
sudo curl -fsSL https://github.com/pranshuparmar/witr/releases/latest/download/witr.1 -o /usr/local/share/man/man1/witr.1
sudo mandb >/dev/null 2>&1 || true
```
