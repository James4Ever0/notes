---
created: 2026-03-19T15:25:07+08:00
modified: 2026-03-19T22:39:55+08:00
---

# install claude code

install from npm

```
npm install -g @anthropic-ai/claude-code
```

set finished onboarding, in file ~/.claude.json

```
claude 
# exit
vim ~/.claude.json

# add the following attr
# "hasCompletedOnboarding": true
```

using deepseek

```
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=${YOUR_API_KEY}
export API_TIMEOUT_MS=600000
export ANTHROPIC_MODEL=deepseek-chat
export ANTHROPIC_SMALL_FAST_MODEL=deepseek-chat
export CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1
```

using kimi-k2

```
export ANTHROPIC_API_KEY=${YOUR_API_KEY}
export ANTHROPIC_BASE_URL="https://api.moonshot.cn/anthropic"
```
