---
layout: post
title:  "Git: Purge local branches missing on remote (Powershell)"
date: 2018-10-04 04:13:00
tags: ["git", "powershell"]
---

```
git remote prune origin | git branch -vv | Select-String -Pattern "\[origin/(.*?): gone\]" | %{git branch -d $($_.matches.groups[1].value)}
```
