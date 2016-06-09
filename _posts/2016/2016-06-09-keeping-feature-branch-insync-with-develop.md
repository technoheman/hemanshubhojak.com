---
layout: post
title:  "How to keep your feature branch in sync with your develop branch"
date: 2016-06-09 06:12:00
categories: git
---

While using [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow), 
it is a good practice to keep your feature branch in sync with the develop branch to make merging easy. 

I do the following to keep my feature branch in sync with develop.

```
git checkout develop    #if you don't have it already
git checkout feature/x  #if you don't have it already
git pull --all
git merge develop
``` 

You can also do a [rebase instead of merge](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/).