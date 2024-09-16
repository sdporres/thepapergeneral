---
layout: post
title: Adjusting the Fealty game loop
tags: code design
comments: on
---

Well, I think I am finally over Total War: Three Kingdoms (phew). If you have been following it along you don't need me to tell you CA did an incredible job - and I am hoping to steal all their best ideas. I almost uninstalled it last night, feeling great satisfaction from my time with it, but I didn't actually do it. But at any rate, its pull on me is much weaker now that I've had my fill.

But besides that, and other life things, I have been working on the game. In fact, I have been knee-deep in the very core of the game which is the simulation itself. The fruits of that labor will soon bear fruit in a visual way, but if you played the game today it would all look about the same - which means all my work was a great success.

Let me explain...<!--more-->

## In the beginning there was time

Every game has a "core loop" which is like its heartbeat. How often that heartbeat happens can vary, and I'll talk more about that soon, but in general you want the game to update fast enough to make everything smooth - and there are different ways to achieve that.

Fealty runs at a time scale that is 1/365 real time so that a game year takes place in a real day. To achieve this, the simulation updated its internal clock 1 second every 1/365 of a real second (2.75 milliseconds). This was very simple logic and made the character movement appear smooth without any extra work. This was the implementation in 1.0.

## "Prepare to fast-forward"

## "Fast-forwarding, sir!"

One of the salient things to come from 1.0 was that waiting for the game to do things sucked, and it would be nice if the game progressed while you werent playing it. This was, of course, always the intention for the game but it wasn't vital to the core mechanics which is what I wanted to capture. The issue was most obvious on mobile devices which typically suspend an app when you switch to another.

"Live Mode" went out with 1.1, and it simulated the game running in real-time. This was fairly straightforward to implement by simply tracking the timestamp of when the game was paused or closed, and then calculating the amount of game time elapsed when the game is resumed. And everything worked fine until the game had to simulate a few real days worth of progress. This could take too many seconds and started to feel bad.

## One small step

The issue was that the game updated too frequently and was doing a lot of nothing most of the time. Though the implementation of the simulation update captured the timescale I wanted, most actions in the game do not need to update in that short frequency. I tried a few different things and found that the simulation could update every 500 milliseconds and still capture the granularity (from a game logic and design perspective) that I wanted.

Effectively, I kept the same stride but lengthened the step of that stride significantly. The fast-forward then ran supa smooth baby!

## Gotcha #1

The first casualty of this change was the character movement visuals. The visual elements that the players sees are updated when stuff happens in the simulation. Previously those events were firing very quickly, and now less quickly. The movement looked like the characters were skipping frames and was jarring.

As a budding gameplay/front-end wannabe, I admit I had to look into the proper way of handling this. And the answer is "Linear interpolation", or lerping.

## You go that way, I go home

The heart of the issue is that we want the simulation and the visuals to update when they need/want to independent of each other. In our case, the simulation updates every 500ms but we want the action to appear smooth so we need to update much more frequently than that. In the case of the graphics, we want to maintain 30 frames per second, which works out to updating every 33.333 milliseconds.

Simply put, linear interpolation is the mathematical concept for finding a particular point along within a range. Instead of updating the position of the character every 500 ms *step*, we want to be able to determine how far along that *step* the character moves every 33 ms. By knowing how long the simulation update step is, and how often the visuals update, we can break up the simulation step movement into a number of individual frames in order to visually represent the smooth progression over those 500 ms.

After some experimentation I got the lerping to look like the simulation update step had never changed.

## And the other thing

Once the character movement didnt make me throw up anymore, I started playing around with the fast-forwarding to make sure everything worked properly from a resumed state. I was feeling pretty good after figuring all that stuff out, I had to admit. I was feeling good about myself and optimistic about getting this thing done.

And then everything stopped working.

First I wasn't able to transfer resources to characters anymore, which was very weird because, of all the things, that command executes and resolves immediately since there is no on-going component to it. But soon it became evident that nothing was working at all.

This was a rather demoralizing event, as you might imagine. I had thought I had pulled of a tricky refactor of the inner core of the game, and everything looked good, and now nothing worked at all. I had leads on what was wrong, and that was the worst part.

## Molehills and Mountains

In times like this it is good to remember that you are probably the one that created the mess you are in. By extension, I think, you can most likely figure it out. And in this case, as so often it is, the problem turned out to be rather stupid.

In case you are not familiar with the [architecture for the game](architecture), the relevant thing here is that the the simulation actually runs in two places - your device and on the server. Since there is no server right now, the game creates a faked local server that gets the job done. This is important because every command from a player (human or AI) is validated and executed twice - once locally, and once by the authoritative server.

When a command is created it is timestamped with the *game* time for when the commands is to resolve. The client validates the command first, so we can shortcircuit the whole business and let the player know right away. If the command is valid on the client, then it gets sent to and processed by the server.

The distinction between the two is that the client only has to know about one game, but the server knows about many. The server, therefore, doesn't keep the game active unless it needs to, and once its done its work it puts the game data away to save resources. This means that the server data doesn't get updated in real time. Instead, when a command is received the server fast-forwards the game, validates and executes the command, and then lets the client know to execute the command locally. This means that with every command the server usually has to fast-forward its copy of the game data.

It turned out that I had not adjusted the frequency for the server, so it wasn't fast-forwarding properly. Commands were failing because the local and the server game state were out of synch. Once I fixed that then everything was back to normal.

## Now all that's left is to refactor everything

Well, not really. But I do have to make changes to the actions themselves to adjust how they resolve over time. This has given me the opportunity to improve the action system overall. The culmination of these changes is the new action system which most importantly makes the game more interactive, will help make understanding whats going on easier and overall make the game more engaging.

---

All of this good stuff is coming in 1.3. The game will stay at 1.x until the kingdom game feels good, and the character actions are fun. Then we will get into all the cool dynasty and character stuff.

I am planning to share more 1.3 details when I have some UI to show off and it all comes together. It is going to be a significant step for the game, and start to capture what I am after.

Thanks for reading!

---

[architecture]: {{ site.baseurl }}{% link _posts/2019-04-8-Fealty-Code-Architecture.md %}

