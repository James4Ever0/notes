---
title: Dive into the commits
created: 2024-09-28T08:43:18+00:00
modified: 2024-10-11T09:12:09+08:00
---

# Dive into the commits

Take notes to a specific file while you code. It is important to note down observations and insights during reading code.

---

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
git log -p -- <specific_file>
```
