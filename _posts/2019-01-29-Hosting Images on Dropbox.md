---
title: Hosting Images on Dropbox
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

## Introduction
When I started this blog several months ago, I was still deciding on how best to host images. My first thought was to use GitHub itself, since that is where this website is hosted. But that wouldn't be a long-term solution considering that [GitHub strongly recommends keeping repositories under 1GB](https://help.github.com/articles/what-is-my-disk-quota/) and has restrictions.

Then I considered using Google Photos, but I have been trying to cut back on the amount of Google services I use because [I don't trust Google to keep services running long term](https://en.wikipedia.org/wiki/List_of_Google_products#Discontinued_products_and_services).

OneDrive would have been my pick if it wasn't for the fact that Microsoft **STILL** has not released a native OneDrive client for Linux.

That left me with Dropbox. A company whose primary offering is cloud file storage. Dropbox has a lot going for it: free 2GB of storage with the ability to get up to 16 GB of free space by inviting your friends, great permissions/sharing control, and even a [native client for Linux](https://www.dropbox.com/install-linux)!

<!--more-->

## Getting Started
First thing you need to do is create a Dropbox account, if you use my [referral link](https://db.tt/lB0uCSJKEB) you'll get a free 500MB extra storage!

### Folder Organization
I like to keep my images organized in folders that are named after the title of the post the images are used in.

<img src="//dl.dropboxusercontent.com/s/539sjdkxgntp0mb/image1.png" alt="Dropbox folder organization">

Go ahead and upload an image to Dropbox, using either the Dropbox client or the Dropbox website.

### Obtaining the Image URL
If you hover over the image you uploaded there should be a button labeled *Share*.

After you click that button you will see the following:

<img src="//dl.dropboxusercontent.com/s/q9wp9mb2thq5aqc/image2.png" alt="Dropbox create shared link">

Click on the *Create a link* text and you will see Dropbox generate a link for your image (this will take a few seconds).

You will now have two options, *Link settings* and *Copy link*. Click on *Copy link* and <kbd>CTRL</kbd> + <kbd>V</kbd> the URL into the text editor of your choice.

<img src="//dl.dropboxusercontent.com/s/3y3azs280ypkbgo/image3.png" alt="Dropbox shared link options">

Now that you have the URL for your image, you might think you can just use that URL in a HTML img tag and display your image. Unfortunately, Dropbox requires you to modify the URL you created in order to actually display the image.

### Modifying the Image URL for Hosting
We are going to be using `https://www.dropbox.com/s/539sjdkxgntp0mb/image1.png?dl=0` as the example URL that you would have copied.

What you need to do now is copy the unique image code from the link you created, in the example URL this would be `539sjdkxgntp0mb/image1.png`

Then you want to use `//dl.dropboxusercontent.com/s/` as your base URL and append the unique image code to the end of it. Your complete URL should now look like this: `//dl.dropboxusercontent.com/s/539sjdkxgntp0mb/image1.png`

Finally, you can take that new URL you crafted and use it in the src field of an img tag to display your image hosted on Dropbox.

```
<img src="//dl.dropboxusercontent.com/s/539sjdkxgntp0mb/image1.png">
```

That's it! Just repeat the process above for any new images that you want to display on your website.