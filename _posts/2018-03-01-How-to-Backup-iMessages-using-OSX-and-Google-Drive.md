---
title: 'How to: Backup iMessages using OSX and Google Drive'
layout: post
date: 2018-03-01 12:57:45
tags:  howto
---


This is pretty short but I wanted to leave it here for posterity. The process is to just add the archive folder to Google Drive. You don't have to move it to your Google Drive folder or hard link, as other tutorials have suggested, just add it to the list of extra folders synced by Google Drive.

First, find the folder iMessages uses to store all its data. Mine is in `/Users/soph/Library/Messages`. If you aren't able to see the Library folder, use `cmd-shift-.` to make hidden items viewable.

Select the Google  Backup and Sync icon in your menu bar at the top of your screen. Go to ...->Preferences->Choose Folder and select that folder.

And, there, you're done!
