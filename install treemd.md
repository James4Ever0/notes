---
created: 2026-03-18T15:39:06+08:00
modified: 2026-03-18T15:42:27+08:00
---

# install treemd

```bash
# update rust toolchain
rustup update

# install treemd
cargo install treemd

# append the binary to path
export PATH=$PATH:"$(realpath ~/.cargo/bin)"

# remember to save it to ~/.bashrc
echo "export PATH=$PATH" >> ~/.bashrc
source ~/.bashrc
```
