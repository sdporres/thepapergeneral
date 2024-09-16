---
layout: post
title: Alpha 1 Post Mortem
tags: postmortem
comments: on
---

My overall take on Alpha 1 was that it went well until I began to outrun the design. Things got shaky as I lost some confidence on how to proceed. This first version has enabled me to validate some design questions, iterate on the core gameplay, and improve parts of the workflow for how this game is going to actually get done.

Here are the Good, the Bad and the Ugly.
<!--more-->
## The Good

### It exists

The most important thing about Alpha 1 is that it exists. It was important for me to put something together as soon as possible and to adopt an iterative production process

The second part of this is that, though much of the gameplay implementation has to change, the simulation engine is coming along quite well - it is powerful, robust and easy to extend.

### People played it

Alpha 1 was played by over 90 people and the website saw over 150 hits in aggregate for all Alpha 1 releases (1.0, 1.1, 1.2). I think that means the Twitter and reddit stuff is working. Some people played it for 3+ days

> My threshold was that at least 10 people would download it. That's motivating

### Got some feedback

The feedback channels are working. Between the in-game reporting stuff and direct messages from people I received great feedback on what was confusing, what felt good, and the impression that people got from the game

## The Bad

### Some breaking bugs still made it through testing

Despite all the bugs found in playtest, 2 severe crash bugs still made it to live. Sorry about that :C

> Most of these uncaught because they were platform specific and UI related

### No iOS release because of platform specific bugs

iOS specific issues are some-what of a bane to me because I don't have an iOS device. Fixing and finding bugs is a lot of trial and error and reading logs. I decided to let the iOS build sit broken while I focused on improving the PC UI instead

> I have a Mac now thanks to a friend!

### The UI tries to serve three masters (PC, Portrait, and Landscape) and in the end does none of them well

As an "always-on" game, Fealty caters directly to mobile devices - but most of the testers were PC users. This is a tough split between crowds, and I struggled to find a balance between building UI for them.

> In the end I ditched portrait mode to simplify UI development

## The Ugly

### The game is fairly boring and obtuse

This didn't surprise me - I have the advantage (or disadvantage?) of having the entire model of the game in my head. So I have an idea of how small things will impact big things. I am finding communicating this sort of information, and relationships between information, to be one of the more challenging aspects of gamedev

> I had not considered "gameplay" in my design, I had instead focused on systems. Alpha 2 does it the other way around

## We Have The Codes!

Alpha 1 was certainly a growing process. I entered Alpha 1 with a clear plan for the features and only a few ended up getting cut. The focus in Alpha 1 was putting together the core of the simulation engine which will power the game.

The simulation engine code has turned out quite well and Alpha 1 has laid a foundation for what is to come. Alpha 1 also enabled me to proof core aspects of the design, such as the world economy, and revealed valuable lessons about what works and what doesn't regarding the character agency model at the heart of the game.

There is more work than ever to be done, but I think the project is in the best shape it has been in yet.

---

I have created a Roadmap on trello and added the link to the navigation on this site for folks that want to see what my planning looks like. I fiddled with Butler, an automation tool for Trello, and came up with a way to synchronize high level roadmap tasks with lower level development tasks.

Furthemore, following some common advice, I created a Discord channel that I am going to start promoting. It was recommended to use the Discord channel as the nexus of the game community. Once development on Alpha 2 picks up I intend to start driving the channel more.

The design of Alpha 2 is nearing completion and I look forward to sharing that with you.

Thanks for reading!

---
