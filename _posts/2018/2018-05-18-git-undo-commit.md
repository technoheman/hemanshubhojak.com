---
layout: post
title:  "Git: Undo a commit"
date: 2018-05-18 11:47:00
tags: ["git"]
---

```
git reset --hard HEAD~number_of_last_commits
```
Or

```
git reset --hard commit_id
```

If the commits are on the server

```
git push --force
```
