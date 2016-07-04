---
layout: post
title:  "Angular2: TypeError: Cannot read property 'visitStatement' of undefined"
date: 2016-07-04 01:00:00
tags: ['angular2']
---

If you get the following runtime error in your Angular2 app,

```
TypeError: Cannot read property ‘visitStatement’ of undefined
```

Remove any empty event handlers like,

```
(click)=""
```
