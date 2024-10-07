---
title: Dive into the commits
created: '2024-09-28T08:43:18.037Z'
modified: '2024-10-07T11:28:48.047Z'
---

# Dive into the commits

You need to know the development history of your project in order to recover the contexts and motivations. A most possible use case could be picking up an ongoing project weeks ago, but you do not know where to start or follow.

You can start in two ways, one is to learn the latest modified filepath and start there, one is to view the entire development history and see what can be done after indexed into a vector database.

---

To list latest modified directories:

```bash
ls -lthd */
```

To get modified files:

```bash
git log --name-only # just file paths
git log --name-status # file path with mod status
```

To get file diffs:

```bash
git log -p
```

