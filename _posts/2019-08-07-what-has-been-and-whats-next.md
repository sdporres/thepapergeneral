---
layout: post
title: What has been and what is next
tags: general
comments: on
---

Hello everybody. It has been an effort to get some kind of update out because 1) there is a lot going on and 2) I couldn't decide on what to post about from all that is going on. So I will summarize here what has been going on since the end of June, what is happening now, and what will happen next.<!--more-->

## Feature Creep

The focus of the would-have-been Alpha 1.3 release was improving the action system by adding interaction to it. I hadn't thought about how much interaction I was going to add and ended up end in a place where I have to implement a lot of new UI to make the new actions work. However, while building out the action system I repeatedly ran into a situation where I was rubbing up against other systems that had not been fleshed out enough. I started to have doubt wether doing the work now was worth it, rather than stopping to expand and revise the design to incorporate them.

If I just winged it then most likely I would end up having to redo the gameplay on the UI, which is one of the more time consuming parts of the project. Rewriting the rules and logic itself is rather straightforward.

So I decided to stop programming and go back to design.

## The Face of Battle

One of the stickier parts of the design challenges was combat. Fealty is a ***strategy*** game where the player is more like a CEO than a general. Your decisions are about who to send to do what and managing logistics.

I have been tempted more than once to make combat abstract, which is the common way to handle this problem. There is nothing wrong with this approach, but battles are dramatic and important events inherently and I want the player to be able to see the drama unfold. What we have ended up with is a design that is simple to implement and understand and fun to play. Watching a battle is going to be an important way to learn about your characters (and the enemies!) and about what works and what doesn't.

While thinking about combat last month I read one of my favorite books, *The Face of Battle* by John Keegan. It can be dry and academic in portions, perhaps almost pedantic, and the author tends to write long sentences, but the coverage of the battles offer interesting insights into what a human person is thinking about during battle. In particular the chapter on Agincourt was most relevant to this game, but in my opinion the best part of the book.

## Extra hands

In the midst of the above, I also started to engage with a couple of UI folks who have offered to help me layout things better. It is very hard to work with other people! It is not possible to simply hand-off a task, the person needs to gain familiarity with many parts of the system to be able to work effectively. Sketching designs, documenting mechanics and having conversations all takes time.

So that has taken time as well, but it has two consequences which are very good. It has forced me to document more, and really think about what I am documenting so that it can stand on its own. (Organizing and laying out what is effectively a rule book is HARD!)

Documenting more has forced me to fill in the gaps that are easy to gloss over when you are only thinking about something. Our brains have an incredible trick of managing complexity by abstraction. But when you are righting the code you need to think about and understand every process in detail so that you can implement it.

In the end the team is stronger and the project is stronger for this ongoing investment of time rather than skimping on protecting the foundation of the project in a rush.

## Alpha 2

Originally 1.3 was going to be the beefed up action system, and 1.4 would be characters. But that plan was going to outstrip design and lead to a bunch of rework. Instead I am axing 1.3 and 1.4 and calling Alpha 1 done.

Alpha 2 is focused around the UX and player immersion, improvements to the existing settlement/economy model, and extensions to the character and family systems. My goal for 2.0 is first to improve whats there, and then do point releases as I extend existing systems and add new ones.

Each point release will introduce a new module to the game that extends it. We will continue with point releases until the entire Kingdom Game design done. Alpha 2 will end when the kingdom game is feature-complete.

## What's next

Alpha 3 will add multiplayer to the kingdom game.

Alpha 4 will add more player meta and progression stuff.

---

Now that Alpha 1 is dead, I will prepare a post mortem for next time.

Thanks for reading!

---
