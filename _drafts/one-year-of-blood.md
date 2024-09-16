---
layout: post
title: One Year of Blood

---

The *Fealty* codebase turns one year old today. Estimating that I put in between 2 to 4 hours into this a day, this comes out to 136.8 "work days" (e.g. eight hour days), which is roughly 5 months. Looking at it this way, I feel pretty good about where the project sits. 

The arrival of *Fealty*'s birthday is fortuitous because ever since launching this site I have been unable to decide on which of the 39 different topics my head to make a post about [Analysis Paralysis!]. Now this has all been taken out of my hands by fate.

To kick this thing off, I want to review how the project has progressed over the past year. That should be fun, right? Without further ado...

# Milestone 0  [01/09/2018 - 01/16/2018]

To begin with, I must admit that at this point I was not starting from scratch. The previous year I had completed a prototype of the multiplayer and networked aspects of the game so I already had a decent codebase from an architectural perspective. (I'll that more about that in the future) 

At this point I had a good sense of how to divide the codebase to reuse the simulation bits on both the client and the server, and how to expose the game abstractions in order to make the game code consumable by any sort of client.

The main effort in this milestone was to generate a tile map for the game world, get some basic camera functionality for panning and zooming, and get the game characters to appear in the world. One of the lessons I learned early on is that working with DLLs in Unity (Unity treats them as Plugins) is a pain in the ass. Recompilation was a necessity when any changes were made, and I was forced to do a lot of changes. In other cases, code analysis tools would fail or give false errors in the IDE. Although ultimately the code will be distributed as DLLs, I abandoned doing that *for now* because iteration time was much higher.

[shows images of game]

[show gif of camera functionality]

At this point nothing in the game did anything, but the camera was working nicely.

# Milestone 1 [01/17/2018 - 02/07/2018]

# Milestone 2 [02/07/2018 - 03/11/2018]

# Milestone 3 [06/11/2018 - 07/31/2018]

# Milestone 4 [08/01/2018 - 08/31/2018]

# Milestone 5 [09/01/2018 - 09/27/2018]

# Milestone 6 [09/28/2018 - 10/17/2018]

# Milestone 7 [10/18/2018 - 10/30/2018]

# Milestone 8 [10/31/2018 - 11/06/2018]

# Milestone 9 [11/07/2018 - 11/25/2018]

# Milestone 10 [11/26/2018 - 12/01/2018]

# Milestone 11 [12/02/2018 - 12/14/2018]

# Milestone 12 [12/15/2018 - 01/06/2019]







