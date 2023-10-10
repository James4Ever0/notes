---
created: 2023-10-10T22:49:03+08:00
modified: 2023-10-10T22:52:04+08:00
---

# execute script before & after system events like startup, suspend & shutdown

for startup use `@reboot` with `crontab -e`

for others, write scripts under `/lib/systemd/system-*`
