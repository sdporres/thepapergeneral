---
layout: post
title: Serfs, Yeomen and Tradesmen - Oh My!
tags: design
comments: on
---

This post is about a week late and I am putting the last bits of 0.1.5 together. Besides the impact of the holidays on things, the past two weeks have been tough and slow in progress. The game stuck in a weird place because I had started to make big changes to the settlement part of the game but the feature ended up about half of what I wanted. I saw three options before me:

* (1) Shoehorn what I could of the remaining half of the work as quickly as possible, knowing I would be redoing it again for 0.1.6
* (2) Delay 0.1.5 until next-year and do the remaining work properly
* (3) Leave the scope of 0.1.5 as-is and release before New Year

I really don't want to delay 0.1.5 because want to leave 0.1.x behind and do a big 0.2.0 release (targeting May) that would be revisions of existing plus multiplayer and meta progression with a fresh coat of paint.<!--more--> I think a post-mortem of the last year will be interesting and I plan to do that to kick off 2020.

Today I want to bring the focus to the core of 0.1.5 which is broad changes to the management and development of your settlements. Like all other things the system still has to mature and grow but I think the idea has serious potential. I need you to tell me if that is or isn't the case. (Seriously - help me to not waste my time.)

The numbers may be a little wonky as I go through this because the devil is in the details, but I hope that the broad strokes come through and the concept for the gameplay is clear. Without further ado...

## A brief review of resources in the game

Currently there are two primary resources in the game: Food and Coin. In the future there will be other resources tied to crafting and production, but Food and Coin are at the core of the strategic elements of the game.

Food is important in Fealty because without it your settlements cannot grow, your people suffer and you cannot keep your troops in the rank. Proper planning for the care and feeding of your troops is important since Food is only produced twice a year during Harvest time. To have Food you need farmers, who are the ones that plant the Crops the majority of the year that are harvested into Food at the Harvest.

>In 0.1.0 all of your population are farmers unless you give them a job by placing them in a building in your settlement. Farmers can also be conscripted into a Levy. A Levy is a unit of peasants who serve out of obligation to the lord of the settlement and they are free to recruit and maintain. However, levies cannot be kept around forever and eventually you have disband them or a settlement will have serious unrest problems. This means that Levies are good in the short-term to boost numbers, but there is little opportunity to train them into a powerful and potent unit.

Coin is important in the game because it increases your strategic options, and the design intent is that to really have a lot of it you have to first invest in creating/restoring economic activity within your realm. With Coin you can pay for professional troops - who will stick around as long as you pay and feed them. [They can also "pay themselves" from successful raids] You can therefore take the time to train them in preparation for your next campaign. Furthermore, paying for troops means that you minimize the impact to the vital farming economy.

>In 0.1.0 Coin is used for building construction and for troops. In the future Coin is also going to be used to recruit and pay the salaries of officers (characters that are not related to the family), to grease the wheels of negotiations, to trade for other resources, and other sorts of things.

## Design for 0.1.0, and some lessons

Settlement management has not changed since 0.1.0 (except for the addition of the Tavern). The basic idea for settlement management is that you have a limited number of buildings you can construct and that those buildings determine the economic activity of that settlement. So far your choice is between building Cottages, which boost pop growth - more farmers, more levies - and Markets which produce a small amount of Coin every day from the workers you assign to it. This is a small example of the underlying tension behind settlement development: do you want a population of Serfs that are in service to you directly, or a more active economy of Freemen that produces (and requires) Coin. I think this is analogous to the concept of going wide or tall in 4x/strategy games.

In 0.1.0 the main decisions you have to make are what buildings to construct (I tended toward 2 cottages, 2 market, and then swap a cottage to a tavern) and how to assign the population between them. This ended up being a painful game of micromanagement whenever you wanted to construct something:
Start construction
Assign maximum workers to accelerate construction
Wait for construction to finish
Adjust worker assignment once building is done
That was certainly tedious. But at least it did capture [perhaps only in my eyes, hahah] the fundamental choice I am trying to capture. So the goal for 0.1.5 was to make all of that less fiddly.

The other thing learned from 0.1.0 was that Coin was really powerful. Once you had enough population to have the Food production you need then going all-in on Coin was optimal and paid troops will stomp over levies. I started to address this in 0.1.5 as well.

## Design for 0.1.5

The biggest change in 0.1.5 is that settlement population can now be one of three types: Serfs, Yeomen and Tradesmen. Each type is different in how they take part in the local settlement economy. Each type also has their own Wealth rating - you could have poor serfs or prosperous serfs - that is impacted by the level of taxes you decide to collect. When you recruit troops from your settlements, their base equipment and quality will be higher if the population if wealthier.

You no longer assign workers to buildings either. Instead, the buildings you construct will determine the number of jobs available in the settlement. The available jobs will determine the natural immigration to your settlement of that type of population. Furthermore, new command allows you to direct a character to attract new population to a settlement.

### Serfs -

**Serfs** are close to indentured servants - these are people that serve you as their lord in exchange for the ability to live in the settlement and the security that entails. Serfs can be levied (like you can currently) into military service for 35 days. You can extend their service, but doing so reduces the morale of the unit and also starts to cause unrest back home.

You can distribute your Serfs between two jobs: Farming and Support. Farming is the same as it has been - the more farmers you have the more Crops that will be planted and the more Food you will harvest. Now that you no longer assign workers to buildings, the Support job is responsible for performing construction of new buildings. The number of Support serfs is also used to calculate the population growth and wealth growth of the settlement - the less farmers you have the faster your population and economy grows as your serfs "do their own thing".

### Yeomen -

**Yeomen** are similar to Serfs except that they own the little land they live on and they do not owe the lord the same kind of service as Serfs - specifically this means that you cannot levy them. Furthermore Yeomen do not immigrate to the settlement, but instead you have to sell your existing cottages to them. Though you cannot allocate Yeomen to the Farmer and Support roles they do pay taxes monthly - in addition to the immediate Coin you gain from the sale of the cottage. You can also buy cottages back, in which case you regain the cottage to have more Serfs but the Yeomen will depart. The price of buying/selling cottages is determined by the wealth of your Serfs.

### Tradesmen -

**Tradesmen** are the third type of commoner and they need jobs from Workshops. Tradesmen operate the same as the Market workers previously in that they produce Coin per day. You have the ability to tax this activity depending on if you need Coin now, or want to lighten the yoke so that your Tradesmen become wealthier.

In the case of Yeomen and Tradesmen their wealthy growth is primarily impacted by the tax rate that you set. And furthermore, you cannot recruit either of them into levies. To supplement your troops, the Tavern will attract mercenaries you can recruit. Wealthier settlements will attract better mercenaries - but, of course, they also cost more.

### Classification -

I added two classifications to the game: Hamlet and Village. Once your settlement population increases to 60 it becomes a "Village" and "brambles" are removed from the settlement to allow more construction.

## The things that didn't quite make it

You will notice that settlement management isn't just a menu anymore and that I added some dressing to it. You will however still recognize the grid. I want to improve the aesthetic here with a nice fog effect around the periphery of the available area, and allow you to place buildings anywhere per standard RTS conventions. By extension you will see your people shuttling around doing things and everything should feel much more alive. Added to this you will see your characters come and go as they depart on business.

Part of moving away from the grid is the introduction of Fields as a "building" rather than an abstract concept. Therefore you will need to consider how much of your limited land you need to allow for Food production.

Settlements that develop economically will demand more and broader political freedoms than perhaps you, as the ruler of the realm, want to give. These demands are the result of a growing middle class that naturally becomes less dependent on the ruler as trade goods start to flow. I am still figuring out the implications here, but restrictions around taxing, population limits and ratios, and one-off events is the likely first iteration.

## Tell me what you think

Like I wrote a year ago when I started this whole thing: one of the main reasons for sharing these details in the rough is to get your feedback on where I am going with things. Please let me know 1) if you could even understand what I am shooting for and 2) am I wearing crazy pants?

Your feedback matters! Thanks for reading
