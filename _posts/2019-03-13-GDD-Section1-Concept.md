---
layout: post
title: GDD Section 1 - Concept
tags: design
comments: on
---

A few weeks ago I announced that Fealty was in need of some dire loving. We embraced the challenge, knowing that it meant we had to revisit a lot what we were doing. I share some of the pain/fruits last time, and today I am happy to be able to share the first section of our in-progress design doc. I am going to reproduce it below, and share some thoughts at the end.

What I am sharing today is the Concept section of our design, and we have tweaked and revised it to the point where we think it captures the *"WHAT"* of Fealty. As I share the rest of the document in the near future, we will also go over the *"WHY"* and *"HOW"*.<!--more-->

Without further ado, here is the Fealty Concept. I will share some additional thoughts at the end.

>## Concept
>
>## 1. Overview
>
>*Fealty* is a strategy game inspired by medieval feudalism where players lead noble families seeking to accumulate **Power** and **Prestige**. These noble families are represented by a **Dynasty** that the player creates, customizes and develops. **Dynasties** will change over time as its members learn skills and abilities, new children are born into the family and characters meet their end from old age, combat or treachery in a **Kingdom Game**.
>
>The **Kingdom Game** is *Fealty's* core game mode, a real-time strategy game in which players compete to claim the throne of a randomly generated kingdom. In order win the kingdom players use the characters in their **Dynasty** to gain **Power** through negotiation, trade, or military conquest. **Power** allows players to perform game-changing actions, and can also be traded to other players to negotiate for their support. Most importantly, unspent **Power** at the end of the **Kingdom Game** becomes **Prestige**. Using **Power** wisely is a vital skill for both short and long term success.
>
>As you play **Kingdom Games**, you will decide how to upgrade and develop your **Dynasty** characters to complement your strategy. Your **Dynasty** will gain **Prestige** based on your achievements and successes, with the goal of accumulating as much as possible before your **Dynasty** ends - when your family has died out. The most prestigious of **Dynasties** will be recorded in the **Hall of Honor**, a leaderboard that shows the greatest **Dynasties** of all time. In addition to the **Hall of Honor**, there will be additional leaderboards to track active **Dynaties** and their relative rankings.
>
>## 2. Player Dynasty
>
>The Dynasty is a player’s representation in the game. Players use the members of their Dynasty to performs actions in the Kingdom Game, like attacking Settlements, trading resources, and performing diplomacy. Dynasty members age during the Kingdom Game, and will eventually die (of something).
>
>### 2.1 Family
>
>The nucleus of the Dynasty is the Family. When creating a new Dynasty, players also create their first Leader. Family members can be married and have children, from which the player can select an heir. Family members are more effective at gaining Power, are always loyal, and do not have upkeep costs.
>
>### 2.2 Household
>
>Household members are characters that support your Dynasty, but are not permanent members of it. These characters only belong to a player’s Dynasty for the extent of a Kingdom Game. Players can Adopt noteworthy Household characters to permanently add them to their Dynasty.
>
>### 2.3 Prestige
>
>Prestige is the measure of a Dynasty's power and success. Prestige increases at the end of Kingdom Games, when a player’s unspent power is converted into prestige. Prestige does not decrease in anyway - it is a Dynasty's all-time high score. Prestige is used to determine a player’s rank in multiplayer. High scores of retired Dynasties are memorialized, and high-performing active Dynasties are highlighted.
>
>## 3. Kingdom Game
>
>The Kingdom Game is where players meet and interact. Each Kingdom Game is randomly generated and lasts until a player Claims the Throne. Players are then free to matchmake/join a new Kingdom Game against players or the AI. Players can also create private Kingdom Games with their friends, which have no effect on their Dynasty’s Prestige.
>
>### 3.1 Time Scale
>
>The Kingdom Game resolves in real-time at a rate of 1 Real minute to 8 Game hours.
>
>| Game          | Real          |
>| :-----------: |:-------------:|
>| 1 hour        | 7.5 sec       |
>| 1 day         | 3 min         |
>| 1 week        | 21 min        |
>| 1 month       | ~2 hours      |
>| 1 year        | ~1 day        |
>
>During the Winter months players are unable to attack each other. This allows 8 hours of sleep time for players. During the rest of the game Year, players will send their Dynasty characters out from their starting Settlement to take control of other Settlements in the kingdom.Through the actions of their characters, players will gain Power.
>
>### 3.2 Power
>
>The Kingdom Game is about gaining Power, in the short-term to win the game and in the long-term when it is converted into Prestige. Players can gain power passively by holding Titles, and actively by trading, warring, or diplomacy. Power has different uses: it can either be spent to perform special actions, traded with other players for some gain or benefit, or left unspent and added to your Dynasty’s Prestige at the end of the Kingdom Game..
>
>## 4. Features
>
>### 4.1 General
>
>* Windows PC and mobile clients
>* Long-term strategy and short-term action hooks
>* Real-time, high-stakes strategy - see your plans evolve, unfold, and crush your friends
>* No two kingdoms are the same, no two dynasties are the same
>* Defeats and setbacks are only temporary
>
>### 4.2 Gameplay
>
>* Create and mold your Dynasty as you see fit
>* Dynasty persistence adds meaning and weight to isolated Kingdom Game decisions
>* Engrossing and tense Kingdom Game mode with rewarding opportunities for cleverness and strategy
>* Characters gain Traits as a result of their actions, which can be good or bad
>* Random Events, related to season and time, disasters, but also good things force players to make decisions
>
>### 4.3 Single Player
>
>* Hall of Honor, Leaderboard of the best, strongest, longest-lasting Dynasties
>* Customize the game you want to play - difficulty, number of opponents, size of map
>* Varying AI opponents to play with
>* Experiment and learn new strategies, tactics, and character trait synergies
>* Control the speed of the game
>
>### 4.4 Multi Player
>
>* Matchmake into Kingdom Games, or create a private game
>* Protection for allowing players to sleep during matches - the Winter Season
>* Global lobby for community and sharing strategies and replays
>* Social features geared towards community-building and engagement

---

## Lastly

The heart of the concept is the dynamic between gaining and using Power in the (so far only 1) game mode and maximizing Prestige gain. We think that idea is interesting and is strongly supported by the long-term Dynasty management gameplay. Most importantly, we think its going to provide gameplay that maximises player collaboration (and maybe treachery).

The previous concept for Fealty described an always-on persistent world with two difficult challenges. One was giving people the opportunity to step away from the game. No matter how great, with every game there is a time when getting a little break is nice. Some games try Vacation Modes, or proxy play (one player filling in for another), but there are significant tradeoffs with any solution. The other challenge was that a setback in a world that is always on and always progressing was very painful. However, "loss" is an emotion that we think is important for the "gains" to be meaningful. Combining the persisten of the player Dynasty with instanced Kingdom Games allows for the games to be more tense and dramatic - and loss should not feel as bad.

We are excited about the Power/Prestige mechanic and already have a long list of ways we can extend gameplay both vertically and horizontally. In order for all of this to work, however, the Kingdom Game needs to be an excellent strategy game on its own.

The Kingdom Game design is well along, mostly needing some T's dotted and some I's crossed, but that will be the thing we talk about - in some way - soon.

Thank you for keeping up with us!

---

