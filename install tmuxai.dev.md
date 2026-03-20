---
created: 2026-03-18T15:33:51+08:00
modified: 2026-03-20T18:53:04+08:00
---

# install tmuxai.dev

download binary directly

```bash
curl -OLk https://github.com/alvinunreal/tmuxai/releases/download/v2.1.1/tmuxai_linux_amd64.deb

sudo dpkg -i tmuxai_linux_amd64.deb
```

create config file

```bash
mkdir -p ~/.config/tmuxai

cat << EOF > ~/.config/tmuxai/config.yaml

default_model: 'deepseek-chat'
models:
  deepseek-chat:
    provider: 'deepseek'
    model: 'deepseek-chat'
    base_url: 'https://api.deepseek.com/v1'
    api_key: '<your-api-key>'
EOF
```
