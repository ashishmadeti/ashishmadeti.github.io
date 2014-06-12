---
layout: post
title: MPRIS Command Plug-in for Simon
categories: [gsoc, kde]
tags: [gsoc14, kde, pmc, simon]
fullview: true
---

Hello folks!

This blog post is a week late (forgot I had a blog :P). This is an update on the status of my GSOC project. Last week, I [added a command plug-in](https://git.reviewboard.kde.org/r/118311/) to Simon. This plug-in (called **Media Player Control**) allows Simon to send commands to any media player which follows **[MPRIS specifications](http://specifications.freedesktop.org/mpris-spec/latest/)**, and most of the popular players do follow these specifications including (but not limited to) **[PMC](http://community.kde.org/Plasma/Plasma_Media_Center)**, [Amarok](http://amarok.kde.org/), [VLC](http://www.videolan.org/vlc/index.html), [Dragon](http://www.kde.org/applications/multimedia/dragonplayer/).

The plug-in currently supports the commands:

- Play / Pause
- Stop
- Next / Previous
- Volume Up/Down
- Seek Ahead/Back

Some of you may be wondering that Simon already had a DBus plug-in, so why was this one needed? The existing DBus plug-in was only capable of calling methods over DBus (which is enough for most of the above mentioned commands) but the commands Volume Up/Down need to first get the value of volume and then increase/decrease it by some value. Also, we planned to add a feature to the plug-in through which a user can play any song in the playlist just by calling out it's name (which will require the media player to expose **[MPRIS Tracklist interface](http://specifications.freedesktop.org/mpris-spec/latest/Track_List_Interface.html)**). This was not possible using the plain DBus plugin.

The next steps in my project are:

- Add MPRIS Tracklist interface to PMC
- Improve the command plug-in to enable playing a media from the playlist by its name

Stay tuned for further updates (I hope I won't be late again ;-)