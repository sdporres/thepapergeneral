---
layout: post
title: GDD Section 1 - Concept
---

If you have been following along, then you know that I finally admitted [I had a scoping problem]. Since then, I have committed to rebooting the project and document a proper design up front. I am looking forward to sharing the conceptual part of the design next week and reveal to you what I have been wrestling with over the past few weeks.

Today I want to talk about a few things that I noted over the past few weeks.

## Better pain now, than pain later

Completing the design was surprisingly challenging. While in your head your ideas synthesize perfectly and deliver the exact experience you want, I found that every one of them requires a lot of pounding before they turn into something valuable. It is much better to do as much of this violence to your ideas ***now*** while things are less complex.

The effort you spend now will save you invaluable time later on - when things are more complicated and you have even less time. In a year or two you want to have confidence in what you have been investing yourself into.

## Plan your planning

Figure out how you are gonna lay out your document before investing much time into presentation. The only thing worse than changing 10 headers is changing 20 headers. I found the [Dirty Bomb GDD] and [this template from Chris Taylor] useful in thinking about how to categorize content.

One particular challenge I ran into is that often times design elements rest on each other, and so you end up sprinklings little bits of explanation here and there. Beyond comprehension challenges that creates for the reader, it is also a maintenance nightmare.

## Gameplay first

Design decisions, similar to tech decisions, are about understanding how concepts interact and the trade-offs in those interfaces. One of my realizations was that, originally, I was not making a game - I was making a ***boring*** simulation.

It can be risky to design a game around a shiny piece of tech or mechanic and miss creating an actual game that players can have fun with. Ultimately no one will care about the independent components of your game if they dont have fun with it.

## Iterate as much as possible

In order to pound the crap out of your ideas, you need to really get into their nooks and crannies. You need to know ***how the sausage is made***. The only way to do this properly is to step through your game as much as possible.

This could take the form of paper or digital prototypes, but at the very least  you need to carefully think through the changes in game state in your systems to understand side effects that may be lurking just below the surface.

The more you can do this the better, again, because ***large changes are much more difficult and expensive later***.

## Don't get mired in implementation details

Another challenge I experienced was that as an idea matured and took shape I would start thinking about technical implementation details - and the design changed unintentionally in response.

This problem actually derailed me for a few days when thinking about resources in the game. Once I perceived what I was doing then solving the design was simpler. Ofcourse, you want to keep in mind what is possible for you technically and skillwise - but don't get stuck in yet.

## But do do the game details

But you do need to get into some detail otherwise!

Delving into details, specially when you feel like there is so many more things to go over still, will slow you down and force you to really think about what you are doing. It is precisely during these times that the design improved the most - fleshing out the details forces you to really understand how things will interact and change.

Judgement is essential here, but remember that any gaps and holes you leave now still have to be filled in later.

## Balance is key to finishing

There were some days that my brain simply could not afford to think about the game, much less make any significant breakthroughs. These times are particularly frustrating when there are so many things to do and limited time to do them. However, those sorts of moments are great opportunities to do *anything else*.

We are probably all familiar with the wax and wanes of motivation, and many are looking for that key to persistent motivation. At the beginning of a project it can be particularly easy to do a lot quickly - there is high momentum and low inertia. Momentum can swing wildly and may be hard to control, but inertia is directly tied to the quality of the things you craft.

When the project is small and there is little code, or little art, changing and adding stuff is easy - its perpetually fun. The experience is one of frequently creating new things. Then those features start to get a bit old - perhaps we dash on some lipstick here and there. And when you find yourself redoing the UI for the eight time you are ready to be doing anything else.

So take breaks often as you need to in order to refresh your momentum, and shoot for high quality early in order to mitigate inertia.

If you are looking to embark on a new project, or just think you have the killer idea, I would encourage you to start purposefully designing and documenting it. In a way, its like writing a program for humans :p

-FealtyDev

![FealtyDevPortrait](/public/images/fealtydevportrait.jpeg){: .portrait }

[I had a scoping problem]: {{ site.baseurl }}{% link _posts/2019-02-15-fealty2-announcement.md %}
[Dirty Bomb GDD]: https://bit.ly/2NJ5tcU
[this template from Chris Taylor]: http://bit.ly/2tz2fAW
