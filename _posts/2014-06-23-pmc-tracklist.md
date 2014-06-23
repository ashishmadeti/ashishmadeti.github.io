---
layout: post
title: Tracklist interface for Plasma Media Center
categories: [gsoc, kde]
tags: [gsoc14, kde, pmc]
fullview: true
---

Hello World!

I have completed the [MPRIS specifications](http://specifications.freedesktop.org/mpris-spec/latest/) **[Tracklist interface](http://specifications.freedesktop.org/mpris-spec/latest/Track_List_Interface.html)** for [PMC](http://community.kde.org/Plasma/Plasma_Media_Center). Now other applications can view and control the current playlist in PMC over DBus. This was a part of [my GSoC project](https://www.google-melange.com/gsoc/project/details/google/gsoc2014/ashishmadeti/5717271485874176). This interface will allow me to send commands to PMC, asking it to play a particular song in the playlist. After some changes to the [Simon](http://simon.kde.org/) **[MPRIS plug-in](http://ashishmadeti.github.io/gsoc/kde/2014/06/13/simon-mpris-plugin.html)**, a user will be able to play a song in the current playlist by naming it. As the Simon plug-in is itself based on MPRIS specifications, it will be able to interact with any media player following the MPRIS specs.

With this, PMC is now MPRIS enabled.(Well it was complete even without the Tracklist interface, as it is optional, but I closed the [bug](https://bugs.kde.org/show_bug.cgi?id=329143) after merging the tracklist work :P)