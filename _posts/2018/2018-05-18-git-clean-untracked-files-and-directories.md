---
layout: post
title:  "Git: Clean untracked files and directories"
date: 2018-05-18 11:50:00
tags: ["git"]
---

After a `git pull` I often have empty directories if files are moved around or deleted.

The following commit will clean all untracked files and directories.

```
git clean -fd
```
