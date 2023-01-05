---
title: install neo4j as systemd service
created: '2023-01-05T00:03:35.116Z'
modified: '2023-01-05T00:04:29.373Z'
---

# install neo4j as systemd service

save this under `/lib/systemd/system/neo4j.service`

```config
[Unit]
Description=Neo4j Graph Database
Documentation=http://docs.neo4j.org

[Service]
Type=simple
ExecStart=/usr/bin/neo4j console
ExecStop=/usr/bin/neo4j stop
Restart=on-failure

[Install]
WantedBy=multi-user.target

```
