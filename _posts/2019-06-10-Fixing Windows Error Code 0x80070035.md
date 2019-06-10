---
title: Fixing Windows Error Code 0x80070035
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
I was recently imaging two new desktop computers that did not match my companies standard Dell OptiPlex 3060 rollout. During the usual setup process, I install printers from a network share that contains all of the office printers. Except I couldn't connect to the network share on these two new PCs! I was getting the dreaded Windows Error Code: 0x80070035.

<img src="//dl.dropboxusercontent.com/s/3ux3506gjiwq0xr/image1.PNG" alt="Windows Access Error">

I tried the typical troubleshooting steps for this error:
- Made sure the VM and desktops could ping each other
- Temporarily disabled the Windows Defender Firewall
- Reinstalled Network Adapter drivers
- Temporarily enabled "NetBIOS over TCP/IP"
- Made sure the "Function Discovery Provider Host" and "Function Discovery Resource Publication" Services were both enabled and running

While none of the above helped me correct the error (they may help you!), I did eventually figure out a fix to this error!

<!--more-->

## Fixing the Error

Open up the classic Windows Control Panel by clicking on the Start Menu and typing "Control Panel".

Once you have the Control Panel open, click on *User Accounts* → *Credential Manager*, and then on *Windows Credentials*.

<img src="//dl.dropboxusercontent.com/s/ed8osob2jj06p9g/image2.PNG" alt="Windows Credential Manager">

Click *Add a Windows credential*

<img src="//dl.dropboxusercontent.com/s/xtrvw7toj6fv8of/image3.PNG" alt="Add a Windows Credential">

Enter the following information
- Internet or network address (I use the Hostname of the VM)
- User Name
- Password

Then click *Ok* to save.

<img src="//dl.dropboxusercontent.com/s/gfxwua0xt5rdc6i/image4.PNG" alt="Windows Credentials">

Make sure that you can access the shared printer(s) or folder being shared from the File Explorer. If you can, great you have resolved the error!

<img src="//dl.dropboxusercontent.com/s/ccde3ygf5ntgsy2/image5.PNG" alt="Print-Server Share">

**NOTE: On one PC I tested removing the Windows credentials after accessing the network share and I was able to connect to the printers without issue, but on the second PC I tried to do the same and was not able to connect without leaving the credentials in place. Your results may vary!**