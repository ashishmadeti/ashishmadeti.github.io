---
layout: post
title: GSoC'14 Project Summary
categories: [gsoc, kde]
tags: [gsoc14, kde, pmc, simon]
fullview: false
--- 

Like all good things, GSoC'14 had to come to an end. Thanks to my mentors, [Shantanu](http://blog.shantanutushar.com/) and [Peter](http://www.grasch.net/), I was able to complete all the things I promised in my proposal. In this post I will try to summarize my whole work during the GSoC.

My [project](https://www.google-melange.com/gsoc/project/details/google/gsoc2014/ashishmadeti/5717271485874176) was to "*Integrate [Plasma Media Center](https://community.kde.org/Plasma/Plasma_Media_Center) with [Simon](https://simon.kde.org/)*". The goal was to allow a user to control PMC through voice commands (using Simon). This required PMC to expose a [D-Bus](http://en.wikipedia.org/wiki/D-Bus) interface through which other programs (including but not limited to Simon) could communicate with it. On the other end, Simon required a plug-in to be able to communicate with PMC.

The interface for PMC and the Simon plug-in, both were based on **[MPRIS](http://specifications.freedesktop.org/mpris-spec/latest/)** specifications which allows them to communicate with other applications based on those specs. For example: any MPRIS based controller like "Now Playing" plasmoid can control PMC. Similarly, the Simon plug-in can be used to control other MPRIS compatible media players like VLC, Dragon, Amarok etc.

Following was my course of action to complete the project:

1. Added [Root](http://specifications.freedesktop.org/mpris-spec/latest/Media_Player.html) and [Player](http://specifications.freedesktop.org/mpris-spec/latest/Player_Interface.html) MPRIS interfaces to PMC. This made PMC MPRIS compatible. Below is a snapshot of the "Now Playing" plasmoid  and the taskbar preview exploiting the D-Bus interfaces of PMC. <center><img src="/images/pmcNowPlaying.png"></center>

2. Created a [command plug-in](http://ashishmadeti.github.io/gsoc/kde/2014/06/13/simon-mpris-plugin.html) for Simon based on MPRIS specs. It allowed a user to control any MPRIS compatible media player through voice commands. It could control the playback of media and change volume. This plug-in was to be improved later so that a user can play a song in his playlist by saying its name. <center><img src="/images/simonBasicMpris2.png"></center>

3. Added [Tracklist MPRIS interface to PMC](http://ashishmadeti.github.io/gsoc/kde/2014/06/23/pmc-tracklist.html). This allowed other applications to keep track of PMC's playlist and play a particular song from it. The Simon plug-in was to interact with this interface to let a user play a song from the current playlist just by saying its name.

4. Improved the plug-in mentioned in (2) so that a user can play a song by saying its name. This works in the following manner:
   - Simon plug-in keeps track of MPRIS compatible media players registered on D-Bus
   - It maintains a list of tracks in a media player by listening for signals of Tracklist interface
   - For each track a new command is created (or deleted when the track is removed) with the track's title as trigger (as shown in the snapshot)
   - When a user says the name of a track, a command with that name is triggered and a [GoTo method call](http://specifications.freedesktop.org/mpris-spec/latest/Track_List_Interface.html#Method:GoTo) is used to play that particular song
   
    This feature can be used with any MPRIS compatible media player which has completely implemented the [Tracklist interface](http://specifications.freedesktop.org/mpris-spec/latest/Track_List_Interface.html). <center><img src="/images/advancedSimonPlugin.png"></center>
    
5. Created a [Simon scenario](https://userbase.kde.org/Simon/Scenarios) based on English HUB4 SPHINX model using the plug-in mentioned in (4) so that the user need not setup the commands manually. [Download](http://opendesktop.org/content/show.php/%5BEN%2BH4W%5D+Media+Player+Control?content=166763) the scenario, import it in Simon and you can control your favourite MPRIS media player (read PMC ;) ).

Now that the project is complete, I request you to test it and please report bugs. You can ping me on [IRC](http://en.wikipedia.org/wiki/Internet_Relay_Chat) for any help. My IRC nickname is *madeti* and you can find me in channels [#plasma](http://webchat.freenode.net?channels=%23plasma&uio=d4) or [#kde-speech](http://webchat.freenode.net?channels=%23kde-speech&uio=d4).