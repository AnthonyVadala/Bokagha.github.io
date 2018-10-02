---
title: Hosting Your Website on OneDrive
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## What You Need to Begin
* Custom Domain
* [Cloudflare](https://www.cloudflare.com/) Account
* Microsoft Account ([OneDrive](https://onedrive.live.com/))

## Steps
1. You are going to want to point your custom domain's Name Servers to the ones that Cloudflare provides, this may take several hours for Cloudflare to confirm
2. In OneDrive create a folder at the top level directory using your custom domain name, this can be either *customdomain.com* or *subdomain.customdomain.com*
3. Select the folder and give it the "Anyone with this link can view this item" permission, uncheck "Allow editing", Set expiration date", and "Set password"
4. Place your HTML/CSS/JS files in the newly created folder
5. Sign into [DriveToWeb](https://drv.tw/) using your Microsoft Account and accept the required permissions
6. Under "Your web pages", you will see your folder's URL. If you click on the link you will be able to see your webpage
7. Copy the [STRING] (*https://[STRING].tw/customdomain.com/*) from the DriveToWeb URL, you will need this to create Cloudflare records
8. Sign into [Cloudflare](https://www.cloudflare.com/) and click on the DNS section
9. Create the following DNS Records

    `CNAME @ [STRING].drv.tw`

    `TXT @ DRVTW=[STRING].drv.tw`

10. You can confirm the DNS changes using [G Suite Toolbox](https://toolbox.googleapps.com/apps/dig), check the CNAME and TXT records to confirm your changes propagated