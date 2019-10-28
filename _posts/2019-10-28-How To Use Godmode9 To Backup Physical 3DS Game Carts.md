---
title: How To Use Godmode9 To Backup Physical 3DS Game Carts
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
In order to follow the steps below, you will need to have CFW installed on your 3DS/2DS console. Just follow the easy guide step by step guide [here](https://3ds.hacks.guide/) to get everything setup and configured.

<!--more-->

## Godmode9
### Dumping a 3DS Gamecart
- Turn off the 3DS/2DS
- Turn on the device **WHILE** holding the <kbd>START</kbd> button
- Use the <kbd>D-PAD</kbd> to scroll down to `[C:] GAMECART` and press <kbd>A</kbd>
- Use the <kbd>D-PAD</kbd> to scroll down to the line ending in the extension `.trim.3ds` and press <kbd>A</kbd>
- Press <kbd>A</kbd> on `NCSD image options...`
- Use the <kbd>D-PAD</kbd> to scroll down to `Build CIA from file` and press <kbd>A</kbd>

**It will take 10-20 minutes to dump the 3DS cart**

- Once backup is complete, press <kbd>A</kbd> to continue

**If dumping multiple 3DS carts, eject the 3DS cart, insert the next one, and repeat the above steps until complete**

- Once done dumping the 3DS cart(s), press the <kbd>START</kbd> button to reboot the system
- You can now shutoff your console, remove the SD card, and plug it into a computer. You can find the dumped game files under `/gm9/out/` on the SD card file system. 
- Copy the `.cia` files that you want to backup to a safe location on your computers, cloud service, etc.


## Optional
### Installing Dumped .CIA file
- Open the `FBI` homebrew app
- Press <kbd>A</kbd> to select `SD`
- Use the <kbd>D-PAD</kbd> to scroll down and press <kbd>A</kbd> to select `gm9`
- Use the <kbd>D-PAD</kbd> to scroll down and press <kbd>A</kbd> to select `out`
- Use the <kbd>D-PAD</kbd> to scroll down and press <kbd>A</kbd> to select the file ending in `.trim.cia` 

**If installing multiple carts, there will be muliple files, when the file is selected it will show the game that it is on the top screen**

- Select `Install and delete CIA` (to save on SD card space)
- Confirm the installation using <kbd>A</kbd>

**It will take 10-20 minutes to install the file game**