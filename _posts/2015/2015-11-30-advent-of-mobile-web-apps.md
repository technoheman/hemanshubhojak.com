---
layout: post
title:  "Advent of Mobile Web Apps"
date: 2015-12-02 01:00:00
tags: ['web-apps', 'native-vs-web-apps', 'chrome-as-a-platform']
categories: web-apps native-vs-web-apps chrome-as-a-platform
---

## Pros and Cons of Native and Web Applications

* Native Apps
    * Pros
        * Has access to almost all device capabilities (GPS, Serial Communication, Camera, etc.)
        * Easy to find apps from the app store
        * Performance is good
        * Supports push notifications
        * Multi threaded 
    * Cons
        * Needs an install
        * Ensuring everyone is using the latest version is a pain
        * Consumes more space on the disk as compared to a web app 
        * Is regulated by the provider (Google, Apple, etc.)
        * Provider can delist the app at their discretion
        * Provider can charge a one time or an annual fee for listing the app
        * Provider shares earnings when some one buys an app
        * Need to maintain different apps for different platforms (Android, iOS, etc.)
            * Which requires learning and using different software development tools
            * Which also requires having separate teams for every platform   
* Web Apps
    * Pros
        * Does not need an install
        * Updating is mostly easy since it needs to be updated only on the server
        * Since there is no provider there are no extra charges
        * Need to target only one platform
            * Which does not require multiple teams
            * At the most one server team and one client team
            * Uses standard technologies like html, css, javascript
    * Cons
        * Difficult to search for web apps as there is no central store
        * Cannot access all device capabilities
            * All browsers may not provide access to all device capabilities 
        * Performance is not always as good as a native app
        * Does not support push notifications
        * Single threaded


## Modern Web Browsers

* Google Chrome browser is now the most widely used web browser in the world
    * It is one of the best performing web browsers 
    * As of version 42, it supports push notifications using service workers
    * It supports WebGL which brings hardware-accelerated 3D graphics
    * You can add a shortcut to your website on the mobile device using the "Add to Home Screen" option to quickly access your website
    * Chrome is available on a lot of platforms (Windows, Linux, MacBook, Android, iOS, etc.)
    * It also has on option to create packaged web apps on the desktop version
        * These applications can access a lot of device capabilities like serial port communication that a web site
        * It also has a web store for the desktop version
* Although Google is fast to release latest technologies on Chrome, all popular browsers are catching up
    * Microsoft has already started on the path to kill Internet Explorer and create a new and better browser from scratch (Microsoft Edge browser)
* Web application development frameworks like Angular 2.0 are making it easier to create single page apps with features like offline support, etc.
* JavaScript performance has improved in the recent years
    * Latest version of JavaScript are approved by ECMA and are adopted very fast by a lot of browsers
    * A lot of transpilers are developed which enables you to write your javascript using the latest specification but which compiles to a version of javascript which will run on all browsers 
* A lot of apps do not need all the device capabilities and can benefit a lot by converting it to a web app

## How does the future look like?

* Will people prefer using mobile web apps over native apps?
* Will developers create more web apps than native apps?
* Will Google Chrome become a platform in itself for mobile apps?

Let me know your thoughts and opinions in the comments below.
