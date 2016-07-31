---
layout: post
title:  "Git: Revert a file to a previous version"
date: 2016-08-01 22:53:00
tags: ["git"]
---

Using commit hash 

```
git log "some-folder/some-file.txt" #get the SHA commit hash
git checkout <commit-hash> "some-folder/some-file.txt" 
```

Using the HEAD

```
git checkout HEAD~1 "some-folder/some-file.txt"
```
