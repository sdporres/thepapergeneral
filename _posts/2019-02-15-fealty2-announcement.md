---
layout: post
title: Fealty 2 Announcement
tags: general
comments: on
---

## **I am excited to announce Fealty 2!**

"But FealtyDev", I hear you say. "What happened to Fealty (1)?"

![Inigo's Wisdom][inigo]

## The Origin of Fealty

The concept for Fealty has been floating around my head for almost a decade. Many years ago, when I was knee-deep in Crusader Kings 2 and Dwarf Fortress (hard to believe it has been so long!), I wanted to bring those two together. I wanted to<!--more--> create a low-level simulation (ala DF) of a defined geographical space inhabited by characters that represented emotion, interests, and personal possessions. The game would play sort of like a CEO simulator, where your main actions were managing your 'human' resources indirectly to achieve things in the world: everything from resource production/refinement, to trade, and diplomacy would be driven by the character system. The idea was further bolstered when I stumbled accross a pen & paper RPG called Pendragon, which contains a system that captures personality and character choices through a Virtue/Vice system. The characters in Pendragon have tendencies to be Pious, or Brave, etc, and that determines how they react to situations. (Players can attempt to 'override' these actions, but that comes down to dice rolls - but if you succeed, that could permanently change the tendencies of that character; become more/less Brave, etc.)

The example that I used often to demonstrate the concept was to imagine that you had two characters - Brung the meaty warrior and Clarence the squirrely merchant. If Brung and Clarence had an interaction, a number of things could happen, including:

* Brung doesn't respect the "puny" Clarence and doesn't take him seriously
* Brung fails to express himself clearly (low Speech, INT, or the equivalent stat), and Clarence misunderstands him or is offended
* Brung is horribly cheated by the smarter Clarence in their negotiations

Any of these results would be valid as long as it resulted from their personalities interacting (and could be understood as such).

I called the low-level simulation the Village Simulator because it represented the manor of the Lord that owned the village, the village itself, and the surrounding areas (fields, woods and such).

On top of that, I wanted another layer of strategy that would be composed of a number of those simulations stitched together. This was inspired from CK2, and the political intriguing that arises organically in that game. The game world would be created by stitching together any number of village simulations to create regions, realms, and countries made up of independent actors. The interactions between the characters in those villages would bubble up to create events and challenges at the strategic level. This would result in an entirely dynamic world where the player could trace the cause-and-effect of the smallest action and see its impact ripple accross the game.

Going back to our example characters, imagine that while conducting some unimportant task in the village next door Brung meets the beautiful wife of the Lord. She is so beautiful that Brung is immediately overcome with passion for her (his high Lust score combined with her high Appearance score, for example) - this might lead Brung to try to carry her off in the night, or to initiate a secret affair. Things could be even more interesting if Brung's interests went unreciprocated. In the worst case, someone might get killed out of jealously or rage. Then maybe the two villages would enter into conflict. That tiny conflict could lead two regions to war, similar to how the assasination of Arch-Duke Ferdinand was the first domino to lead Europe into WW1.

Oh, and of course the whole thing had to be multiplayer and it would be real-time. Which probably meant it would play best on a mobile device.

This is my dream for Fealty.

## Pain and Rebirth

Over the years, the Fealty codebase has seen multiple incarnations and fits and starts. Initially I was working in Python and C++, then I moved over to XNA and C#. Today most of the Fealty game-code is in a C# library with Unity as a thing wrapper for UI and input commands, events, etc. The changes in tech came mostly out of a realization that I could work much faster in C# than in C++, and prototype quicker in Unity's Editor.

Besides the change of technology, I also continously ran into technical problems that were overwhelming and scary. Looking back, engaging with those challenges was a huge part in me growing as a developer and learning new things which helpe to drive my career. (This is a common theme in my life - my side projects are the ones that get me jobs and interviews!)

At this point in my career, I am happy to say that from a technical perspective I feel confident that I can implement any idea I come up with. One of the biggest stumbling blocks early on was figuring out all the networking nessary for a game like this. (If you have tried your hand at this, you know that there are limited resources on this; you can find a million tutorials for user-facing gameplay development, but far less for networking - and theres a reason for that!) I was fortunate to get a job in the games industry doing specifically server and backend system design which finally rounded out the knowledge that I needed.

The point here is that over the last ten years, the journey of working on Fealty has mostly been getting my technical skills where they needed to be. When I forked the most recent codebase (about a year ago now), I had clean architectural plans and designs for all the systems that needed to integrate to deliver the experience I was dreaming of.

## Great Strides

The last year has been the most productive by far, and I am very happy with the simulation tech that has been my focus. I figured, from the start, that the simulation needs to be broad and robust in order to capture the detailed interactions between characters and characters, characters and the world, and then generate the village to village interactions at the heart of the concept. Towards November 2018 it was becoming clear that there was something here that was WORKING. The little sim people would walk around, ask you for things that they needed, and harvest resources and build out the village all on their own. It was the most incredible feeling. And as soon as I had that feeling, I started worrying that I was operating in a black-hole and that no one besides me had seen the game.

## Stepping Out Into the World

So I created some social media accounts, threw together a web page, and resolved myself that moving forward into 2019 I was going to share as much as possible in order to get as much feedback as possible. Furthermore, I resolved to release some kind of playable demo by March 2019. Then a few things happened that I had not expected.

Firstly, primarily through Twitter, I ran headfirst into the indie/game dev communities. I had never used Twitter before, and frankly didn't understand it. But my eyes were opened as I saw how much people shared ideas, feedback, and encouragement. The past few months have easily been my favorite just because I do not feel like I am working in a blackhole. Sharing the pressures and challenges of indiedev with other people made them more bearable, and I made some new friends too! (If you haven't done this, you should - right now)

Besides Twitter, I also wanted to write devblogs as I progressed through milestones. As I embarked on the journey towards the March demo, it all made perfect sense that this was the time to turn the spotlight on the project.

## The Most Common Mistake

You may have noticed that 1) I have previously not share a whole lot of information about the game 2) there haven't been any updates in some time. And this is because I have been dealing with the most common mistake in gamedev: Lack of planning/proper scoping.

Any time I thought of how to share parts of the game, I ran into the same roadblock: I didn't have very much up-to-date documentation. Most of the design has lived in my head, and whatever specs and drawings I had were old or in my journal. Which meant that share the game, or even write about, required a massive effort of explainining what the hell was going on. Anytime I thought I had a good topic, I would think of a dozen other things I thought I needed to explain beforehand for it to make any sense.

As I began in earnest to prepare Fealty for the public, I started to realize that although the tech worked it was very difficult to understand what was going on in the simulation. So I started adding tooltips here, and info bubbles there, and other UI elements to surface the interactions that were taking place. And once I had progressed enough in that area that the game was more legible, then I realized that the design behind the game was incoherent.

I had been writing code as fast as possible and slamming features into the simulation engine that were needed for it to work. I had created great complexity and a level of detail in the simulation that I thought was necessary for the character interactions I wanted, but little thought had been given to what the player would actually be doing or how. Effectively, I had created a wonderful little sim where the actors know how to feed themselves, defend themselves, find things they need, go shopping, and so on - but there wasn't much to do except WATCH. The few gameplay actions the player could take, like tax policy, or decisions about what crops to grow, took a long time to see mature (I created the farming cycle exactly, you see? So, 6-8 months of exposure to enough heat from the sun before crops were ready to be harvested). In other words, the game has serious playability and usability issues arising from the lack of guiding design about the player experience.  

And that was what I have been focused on for the last month. And while pouring over these shortcomings  I realized that I have some fundemental design problems that I need to address which were caused by my lack of up-front planning. As I attempted to tackle those design issues, it became very difficult to test gameplay ideas that had to run through the complicated simulation I had built. Suddenly, it seemed that progress was going to be very slow. And then I was demoralized at the prospect of spending another ten years without a game to show for it.

I learned that even though I now possess the technical expertise to make this game, I had barely focused on the other type of expertise (even more important, really) required: knowing how to design the damn thing.

I knew what I wanted the game to DO, but I hadn't really thought about the PLAYER.

Another way to put it: I had been working on a historical simulator all along and not a game. Boyued by the techincal success I was experiencing, I didn't stop to look around or smell the roses.

## Round Two

I don't think I can get away from the original Fealty concept that has assaulted my imagination over the last ten years. I still really want to play that game, and I think it would be revolutionary as a multiplayer experience where players are drawn into conflict and competition naturally and dramatically rather than over arbitrary goals.

But I have come to grips that I need to let the tech rest for a while until I can do a decent job of putting together the design which it needs to serve. I need to put together the GAME. So, with all those words and thoughts shared with you, I have decided that my original concept for Fealty will come at a later date.

So what is Fealty going to be then?

We will find out together. I am about halfway through v1 of the new Fealty GDD which will describe the game at a high level, and I will share that here as soon as it is finished. Once the structure of the game is in place, we will continue to build out the GDD in perpetuity. It will be the tome that documents everything.

What I know for certain is going to be at the heart of the design is the character driven world and the relationships between those characters (thats where the name comes from, after all). Everything else needs to support that, with whatever compromises have to be made along the way. The biggest obstacle to this is actually the low level simulation I spent all this time building. It is beautiful and exciting thing but one that adds a great deal of complexity orthogonal to the strategic aspects of the game. Can you imagine how impossible it is to test the outcome of some of these interactions dynamically? Can you imagine balancing? I had pretty much given up on the later and just accepted that as price to be paid.

Instead I will replace the low level sim with an abstraction ala most strategy games, and create a design that emphasises the gameplay resulting from the character interactions at the strategic layer. This will allow us to streamline the resource production and economic aspects of the game while fleshing out and discovering the player interactions.

When I have v1 of the GDD ready I will share it here, and then I want to iterate over it with you. Rebooting this project like this is going to give me the tabula rasa I need to involve the community in the production of this baby the way I want to - from start to finish. You will see all the ugliness, and hopefully help me beautify it. And I would love that we have something playable in a few months that we can continue to talk about and get excited about together.

---

[inigo]: /public/images/posts/inigo.jpg
