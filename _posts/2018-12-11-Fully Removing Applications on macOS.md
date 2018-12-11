---
title: Fully Removing Applications on macOS
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Intro
While macOS handles the removal of applications better than the mess of `%APPDATA%` files and registry keys found on Windows. If you are like me and want to remove ALL traces of an application from your computer, finding where an application creates folders and files on your system is pretty useful.

## Applications Folder
The first step in removing and an application from macOS is to open the Finder and click on `Applications` on the left-hand sidebar.

Right click on the application you want to uninstall and click *Move to Trash*.

With the simple part out of the way, let's go file hunting!

## The Two Library folders
There are two locations on your disk drive, both named `Library`, where applications store their preferences and supporting files. The first is located at the top level of your disk drive `/` and the second is inside your Home Folder `~`. Removing files from both these locations is necessary to completely uninstall applications.

### Top Level Library Folder
Let's start with the top-level `Library` folder, which contains systemwide preferences and application support files. You can get to this directory using the *Go to Folder...* shortcut in Finder. To use this shortcut open Finder and make sure it is in focus, then just hold <kbd>⇧</kbd> + <kbd>⌘</kbd> + <kbd>G</kbd> and you will see this popup:

<img src="//dl.dropboxusercontent.com/s/vgdqusckbx3vbam/image1.png" alt="Go to Folder /Library">

Type `/Library` then click **Go**.

Now check each of the following locations for any files or folders that contain the name of the application or vendor name that matches the application you want fully remove:

* `/Library/`
* `/Library/Application Support`
* `/Library/Preferences`
* `/Library/LaunchAgents`
* `/Library/LaunchDaemons`
* `/Library/PreferencePanes`
* `/Library/StartupItems`

Once you locate a file or folder, just right click on the file or folder you want to remove and click *Move to Trash*.

**Note: If you have issues with any installed applications after removing a file you can always go into the Trash and restore.**

### Home Directory Library Folder
The second `Library` folder is found in the user directory and contains user specfic preferences and application support files. You can get to this directory using the *Go to Folder...* shortcut, just hold <kbd>⇧</kbd> + <kbd>⌘</kbd> + <kbd>G</kbd> and you will see this popup:

<img src="//dl.dropboxusercontent.com/s/2qnmcsvhnc9gatf/image2.png" alt="Go to Folder ~/Library">

Type `~/Library` then click **Go**.

Just like the other `Library` folder, look for any files or folders that contain the name of the application or vendor name that matches the application you want fully remove in the following locations:

* `~/Library`
* `~/Library/Application Support`
* `~/Library/Preferences`
* `~/Library/PreferencePanes`
* `~/Library/StartupItems`

**Note: If you have issues with any installed applications after removing a file you can always go into the Trash and restore.**

For the vast majority of applications that’s all you need to remove. After check the remaining applications run fine, Empty the Trash to complete the process. You may need to reboot macOS to remove everything.

## Kernel Extensions and Hidden Files

**Warning: Kernel Extensions are necessary for correct operation of your system. Do not move or delete any items unless you have the ability to undo changes using the macOS recovery partition.**

If you’ve deleted everything from the `Applications` and `Library` folders and some traces of old software still remain, you may be dealing with a kernel extension or hidden file. These items are not obvious to find, doing an internet search for removing the components for your specific software is highly recommended.

Kernel extensions are located in `/System/Library/Extensions` and end with the *.kext* extension. Looking for items with the name of the application or vendor in the name. 

It is also highly recommended to drag the *.kext* files you want to remove to the desktop, then rebooting macOS to see if you have any issues before moving the files to the Trash and emptying it. That way you can move the file back if there is a problem.