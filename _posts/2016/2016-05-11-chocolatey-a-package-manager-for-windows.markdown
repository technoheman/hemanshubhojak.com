---
layout: post
title:  "Chocolatey: A package manager for Windows"
date: 2016-05-11 01:00:00
categories: chocolatey package-manager windows-package-manager
---

[Chocolatey](http://chocolatey.org) is an awesome package manager for Windows (based on [NuGet](https://www.nuget.org/)) which I have been using since a couple of years now. Every developer and hacker should have it on their Windows machines. 

A package manager is a tool which makes it easy to install, configure and update a software from the command line.

Chocolatey is like [apt-get](https://en.wikipedia.org/wiki/Advanced_Packaging_Tool) on Linux or [homebrew](http://brew.sh/) on Mac. 

Installing and updating software is a breeze with Chocolatey using very simple commands. 

- Install a package
{% highlight bash %}
$ choco install notepadplusplus
{% endhighlight %}

- Search for a package
{% highlight bash %}
$ choco search notepadplusplus
{% endhighlight %}

- List all installed packages
{% highlight bash %}
$ choco list --localOnly
{% endhighlight %}

- Upgrade chocolatey using chocolatey ;) 
{% highlight bash %}
$ choco upgrade chocolatey
{% endhighlight %}

You can find more usage at [Chocolatey's Wiki](https://github.com/chocolatey/choco/wiki).   
