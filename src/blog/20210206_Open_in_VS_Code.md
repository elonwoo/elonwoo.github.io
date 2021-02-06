---
title: Open anything in VS Code using a MacOS quick action
layout: blog.njk
date: 2021-02-06
tags: blog
categories:
  - mac
---

## Launch Automator
Create a new Quick Action


## Configure the workflow:
- Set it to receive current "files and folders" from Finder.
- Set and image if you want one - I used the icons from this GitHub repo.
- Add a new Run Shell Script action to the workflow.
- Set the Pass Input to be "as arguments"
- Set the shell script to be:
  > open -n -b "com.microsoft.VSCode" --args "$*" 

## Save the action using a name like Open In VS Code.
This will register the quick action with Finder, and you will now be able to right-click on a file or folder in Finder and select Quick Actions->Open In VS Code