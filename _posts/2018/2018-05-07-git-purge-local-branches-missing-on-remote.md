---
layout: post
title:  "Git: Purge local branches missing on remote"
date: 2018-05-07 12:20:00
tags: ["git"]
---

Prune tracking branches not on remote
```
git remote prune origin
```

List all local branches with upstream branch

```
git branch -vv
```

Filter the branches with missing upstream

```
git branch -vv | grep ': gone]'
```

Extract the branch names

```
git branch -vv | grep ': gone]' | awk '{print $1}'
```

Delete the extracted branches

```
git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -d
```

(Optional) Create an alias in bash

```
alias git-purge-local="git remote prune origin | git branch -vv | grep ': gone]' | awk '{print $1}' | xargs git branch -d"
```
