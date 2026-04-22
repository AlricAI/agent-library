# Dictator

> +++
date = "2016-03-28T23:45:48+01:00"
title = "Project 5: Dictator"

+++


Google have just released their speech API. One really cool feature is the

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
+++
date = "2016-03-28T23:45:48+01:00"
title = "Project 5: Dictator"

+++


Google have just released their speech API. One really cool feature is the ability to transcribe voice in real time.
Two years ago I built an app with this idea in mind. At that at the time I could no make it work. Now it is time to resurrect that app.
This post will cover the recording section of that application.

<!--more-->

This is a very long post so I will split it into sections

+[introduction](#Introduction)
+[icon](#Icon)
+[record](#Record Service)
+[main](#Main Fragment)
+[app](#Application)
+[play](#Player)
+[playfragment](#Player GUI)
+[calendar](#Calendar)
+[manage](#Manage Recordings)

## Introduction


This is a lot more complex that the previous application in may ways. Also there is a much larger amount of code.
This first post will introduce the app and will cover the GUI, in the next post I will integrate the Google speech back end
and later launch the final application. 

I have been made aware that these posts are kind of boring... I will do something about that .
For now lets get into the code. 

I will skim over the easy stuff and go into some details on parts of the application.



Essentially this app allows you to organize you voice notes or dictations. 
I will also convert these dictations into text using the new Google speech api.
The applications of this are literally endless....


This application uses some familiar code 

1. compile 'de.greenrobot:eventbus:2.4.0'
2. compile 'de.greenrobot:greendao:1.3.7'

And a few new ones.

3. compile 'com.squareup:android-times-square:1.6.5@aar'
4. compile 'io.reactivex:rxandroid:1.1.0'


Lets get started.


## Icon

First things first the Icon: 

I used this inkscape tutorial to build the icon.
[http://www.designmarkgraphics.co.uk/blog/articles/2013/11/26/create-long-shadow-icons-for-flat-designs-in-inkscape.html](Create long shadow icons for flat designs in inkscape)

This is a great Inkscape tutorial.


## Record Service

*[truncated — see source for full prompt]*