---
layout: post
title:  "Git: Create a remote branch"
date: 2016-07-20 11:06:00
tags: ["git"]
---

Create a local branch

  ```
  git checkout -b feature/somefeature
  ```

Push the local branch to the remote server and optionally set upstream with ```-u``` so that the subsequent ```git pull``` will know what to do.

  ```
  git push -u origin feature/somefeature
  ```
