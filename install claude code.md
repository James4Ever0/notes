---
created: 2026-03-19T15:25:07+08:00
modified: 2026-03-20T18:53:56+08:00
---

# install claude code

clause resume session, list history

https://kentgigger.com/posts/claude-code-conversation-history


```bash
mkdir -p ~/.claude/commands

cat > ~/.claude/commands/history.md << 'EOF'
Please read my global conversation history from ~/.claude/history.jsonl and present it in an easy-to-scan format.

For each conversation, show:
- Entry number
- Date/time (human readable format: "Nov 10, 2025 15:48")
- Project name (just the folder name, not full path)
- First 60-80 characters of the conversation topic
- Session ID (if available)

IMPORTANT: Format as a plain text table with properly padded columns (NOT markdown tables).

Focus on the most recent 10 conversations in the first table. If there are more, show another 5-7 in an "Additional Recent Conversations" table.

At the end, include:
---
Tip: Resume any conversation by running:
- claude --resume <session-id>
- claude --resume (to see an interactive list of recent sessions)
EOF
```

---

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
