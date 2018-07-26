---
layout: post
title:  "Custom Domain in Asp.Net Core Kestrel"
date: 2018-07-26 01:00:00
tags: ["asp.net core", "kestrel", "custom domain"]
---


# Update `hosts` file
This file is usually located at

    %SYSTEMROOT%\System32\drivers\etc\hosts

`%SYSTEMROOT%` is usually `C:\Windows`

Add the following line at the end of that file

    127.0.0.1   hemanshubhojak.com

You need to have administrator rights to modify this file. Also run notepad or your text editor as administrator to save the file.

Run the following command to flush the local DNS cache.

    $> ipconfig /flushdns
    Windows IP Configuration
    
    Successfully flushed the DNS Resolver Cache.

# Test `hosts` file changes

Run the following command to test the above changes. The ping command should resolve the IP address to `127.0.0.1`.

    $> ping hemanshubhojak.com
    
    Pinging hemanshubhojak.com [127.0.0.1] with 32 bytes of data:
    Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
    Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
    Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
    Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
    
    Ping statistics for 127.0.0.1:
        Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
    Approximate round trip times in milli-seconds:
        Minimum = 0ms, Maximum = 0ms, Average = 0ms

	
# Update IWebHostBuilder

       return WebHost.CreateDefaultBuilder(args)
           .UseUrls("http://hemanshubhojak.com:8866")
           .UseNLog()
           .UseStartup<Startup>()
           .Build();

# Update Launch Settings

The launchSettings.json file is usually located at 

    <Project Folder>\Properties\launchSettings.json

Modify the `applicationUrl` property for your active config (iisSettings, etc.)

	"applicationUrl": "http://hemanshubhojak.com:8866",

You can also `right click->properties` on your project and modify the `Debug->App URL` instead of modifying the above file manually.

# Run

Run the project now and it should work on your custom domain locally. Browser usually cache the DNS for sometime, in which case it may not work right away. Give it about 5 mins and try again and it should work. If not try searching online, ways to flush cache of the browser you use.
