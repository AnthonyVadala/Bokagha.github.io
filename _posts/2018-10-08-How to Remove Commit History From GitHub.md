---
title: How to Remove Commit History From GitHub
layout: post
permalink: /:year/:month/:day/:title/
excerpt_separator: <!--more-->
---

To begin, open your terminal and `cd` to your project's directory.

## Steps
**Check out to a temporary branch**

`git checkout --orphan TEMP_BRANCH`

**Add all files**
`git add -A`

**Commit changes**

`git commit -am "Your commit message here"`

**Delete old master branch**

`git branch -D master`

**Rename temporary branch to master**

`git branch -m master`

**Force update to repository**

`git push -f origin master`