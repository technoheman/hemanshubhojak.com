---
layout: post
title:  "Universal Desktop Apps using Web technologies"
date: 2016-05-17 03:44:00
tags: ['universal-desktop-apps', 'electron']
categories: universal-desktop-apps electron
---

[Electron](http://electron.atom.io) is a framework for creating native desktop applications using web technologies like HTML, CSS and JavaScript.

A lot of popular desktop applications are built using GitHub's Electron, like [Visual Studio Code](https://code.visualstudio.com/), [Slack](https://slack.com/), [Atom](https://atom.io/), etc.

Electron apps are like NodeJS applications bundled with a minimal Chromium browser and uses web pages for UI.

Let's see how we can quickly setup our environment and build a "Hello World" electron app.

## Application structure

 Electron apps are generally structured like this,
 
  * app-name\
    * package.json
    * main.js
    * index.html

The ```package.json``` contains information about the app and it follows the exact format of a NodeJS app's ```package.json```.

```
{
    "name": "hello-electron",
    "version": "1.0.0",
    "main": "main.js"
}
``` 

The ```main.js``` is the startup file. If we do not specify a name Electron will look for a ```index.js``` instead.

```javascript
const electron = require('electron')
// Module to control application life.
const app = electron.app
// Module to create native browser window.
const BrowserWindow = electron.BrowserWindow

// Keep a global reference of the window object, if you don't, the window will
// be closed automatically when the JavaScript object is garbage collected.
let mainWindow

function createWindow () {
  // Create the browser window.
  mainWindow = new BrowserWindow({width: 800, height: 600})

  // and load the index.html of the app.
  mainWindow.loadURL('file://' + __dirname + '/index.html')

  // Open the DevTools.
  mainWindow.webContents.openDevTools()

  // Emitted when the window is closed.
  mainWindow.on('closed', function () {
    // Dereference the window object, usually you would store windows
    // in an array if your app supports multi windows, this is the time
    // when you should delete the corresponding element.
    mainWindow = null
  })
}

// This method will be called when Electron has finished
// initialization and is ready to create browser windows.
// Some APIs can only be used after this event occurs.
app.on('ready', createWindow)

// Quit when all windows are closed.
app.on('window-all-closed', function () {
  // On OS X it is common for applications and their menu bar
  // to stay active until the user quits explicitly with Cmd + Q
  if (process.platform !== 'darwin') {
    app.quit()
  }
})

app.on('activate', function () {
  // On OS X it's common to re-create a window in the app when the
  // dock icon is clicked and there are no other windows open.
  if (mainWindow === null) {
    createWindow()
  }
})

// In this file you can include the rest of your app's specific main process
// code. You can also put them in separate files and require them here.
```

The above script loads an ```index.html``` file and opens the developer tools.

```html
<html>
    <head>
        <title>Hello Electron</title>
    </head>
    <body>
        <h1>Hello Electron!</h1>
    </body>
</html>
```

## Running the application

We need the Electron binary to run our application. Let's install the binaries using ```npm```.

```
npm install -g electron-prebuilt --save-dev
```

This command will install the electron binaries globally and save it as a dev dependency for our application.

Once we have the Electron binaries we can run our application using the following command.

```
electron .
```  

## Packaging the application

To distribute our application we need to package it. Quick and easy way to do that is to use the command line tool [Electron Packager](https://github.com/electron-userland/electron-packager).

```electron-packager``` can be installed gobally using ```npm```

```
npm install -g electron-packager
```

To package our app, simply run,

```
electron-packager . --platform=win32 --arch=ia32 --asar=true
```

This command packages our app as a 32 bit Windows application (```--platform=win32 --arch=ia32```).
Electron apps can be packaged as a Windows, Linux and Mac application.

```asar``` *([Electron Archive](https://github.com/electron/asar))* is an archive format like ```tar``` but with indexing capabilities.
 
Specifying the option ```--asar=true``` will archive our application's source files in a single ```.asar``` file instead of packaging it as-is.

## In closing...

Creating desktop apps for all the major platforms *(Windows, Linux and Mac)* is very easy using Electron. 

We can also use popular javascript frameworks like [AngularJS](https://angularjs.org/), [jQuery](http://jquery.com/), etc.

With some changes, an existing AngularJS application can also be packaged as a desktop app using Electron.
        

**References**

 - [Electron Quick Start](http://electron.atom.io/docs/tutorial/quick-start/)
  