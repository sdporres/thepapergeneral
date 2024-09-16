---
layout: post
title: Fealty Code Architecture
tags: code
comments: on
---

Welcome back #FealtyFaithful.

In today's post I am going to give a brief overview of the technical architecture behind Fealty and then share some implementation details for the game's core tech. Programming is challenging for many reasons, but I think the two most common issues budding programmers run into are syntactical (e.g. what are the things I need to type to make this work) and architectural. The former is usually a problem of knowledge - like learning the interface for a new object type - whereas the latter is a result of lack of planning. In both cases (as it often is) experience is the best teacher.
<!--more-->
## Leaky Abstractions

Architectural deficiencies become clear when you are attempting to add some new feature or functionality and have to compromise on the integrity of your abstractions (by exposing member data, or a private method, publically) - in other words, you have to expose the guts of your abstraction to another part of the code. This sort of 'hack' can not only make code difficult to modify later, but more importantly introduce hard to find bugs. Ideally, each of your code objects presents a clean and well defined interface that makes it usage simple and protects the internal data.

## Code Libraries

Code architecture is also vital to packaging your code into discreet assemblies that can be reused and shared. The Fealty code runs in two contexts 1) the application (or client) that the user interacts with and 2) the server that validates, synchronizes and persists the game data. The good news is that both of these contexts can reuse a lot of the same code - if we do organize things properly. This post is going to focus on the client context, but I will make reference to the server bits when it makes sense.

### FPG.Common Library

**FPG.Common** contains code that is needed, or useful, regardless of context. In fact, the code in this library has nothing to do with Fealty specifically. Instead, FPG.Common defines interfaces and abstract implementations that the Fealty application and server both need to do simple (or 'common'!) things.

Some examples of whats in here:

> **FPGLogging** -
>In-house logging wrapper. This interface is platform agnostic and acts as a wrapper that can be called from any of the FPG code libraries. This class allows code to log from anywhere, without knowing the details about how logging is handled contextually.
>
> **FPGRandom** -
>This object helps us to create predictable "random" numbers. Everyone knows random numbers are fake, right?
>
> **FPGLocalization**
>
> **FPGMath**

### FPG.Unity

**FPG.Unity** is a small library containing interfaces and behaviors I tend to need for every project. Like **FPG.Common**, nothing in here is Fealty specific.

> **FPGApp** -
>This is the core of the Unity application. FPGApp provides platform-specific access to system resources (i.e. Networking, Audio, Filesystem) in an abstracted way to the FealtySDK.
>
> **FPGInput** -
>A robust state-based Input system which translates user interactions into Application-level commands.

```comment
You might be wondering - doesnt Unity provide a lot of stuff already?

Yes, Unity is great in many ways. However, we explicitly do not use Unity functionality (outside of the UI stuff) anywhere on purpose. If we did, then we would have to 1) deploy the UnityEngine DLL everywhere, 2) would be tied to Unity (as it is, we could easily rebuild the UI in a browser, or Godot, or Monogame, etc). That has technical (as well as licensing) implications we want to avoid.
```

### FPG.Unity.Fealty

**FPG.Unity.Fealty** this is the actual Fealty UI implemented as Unity scenes and GameObjects.

> **FealtyClient** -
>This is the heart of the game. The FealtyClient receives input from the FPGApp and converts it into a meaningful Fealty **Commands**. Commands are validated and then excuted, resulting in some change to the game state. The game UI is updated by the FealtyClient (below) through events and callbacks.

### FPG.FealtySDK

**FPG.FealtySDK** is the game "business logic". This library contains all the objects and rules that define how the game works.

The key components in this library are:

> **PlayerMeta** -
> The PlayerMeta is the game context in which the FealtyClient is operating.
>
> **KingdomGame** -
> This is the logic for the Kingom Game mode.
>
> **ProtoData** Definitions-
>There are two sorts of data in the game. ProtoData, which defines the entities in the game, and EntityData, which is a record of an instance of an entity. An example of ProtoData would be a list of the different buildings a player can make, including their costs and in-game effects. An EntityData record would be the data of an actual building that exists in the game.

## In Review

If you have followed the above somewhat, hopefully the picture in your head looks like this:

![Unity Application Architecture diagram][unity-app]

It seems pretty simple, right? Now let me share with you the cool part.

## IPlayerMeta

IPlayerMeta is an interface that the FealtySDK uses to send and receive game related messages (**FPGMessage**). The FealtySDK doesn't know how these messages will be handled, and it doesn't care. All that it cares about is the response it will receive.

This is what the interface looks like:

```c#
public interface IPlayerMeta
{
    Action<FPGMessage> OnMessageReceived { get; set; }
    void Send(FPGMessage message, Action<FPGResponseMessage> responseCallback);
    void Shutdown();
}
```

When the FealtySDK is instantiated by the Unity app it determines if the user has internet and if there is a Fealty server. If both of those conditions are true then the SDK creates a RemotePlayerMeta object. If either is false, then a LocalPlayerMeta is used. The type of PlayerMeta determines how (by-whom) application actions are validated and also how data is persisted. This very small interface belies how important and powerful this abstraction is.

As you may have guessed, there are two concrete implementations of the IPlayerMeta interface. First I will go over LocalPlayerMeta, which is the harder working of these siblings.

### LocalPlayerMeta and RemotePlayerMeta

**LocalPlayerMeta** is effectively a fake server running in the client - it has to run the full functionality of the game. LocalPlayerMeta uses the apps file system to store EntityData and persist player progress. By comparison, **RemotePlayerMeta** does very little - it sends and receives messages to the server. This is the perfect example of code reuse. The game logic that the LocalPlayerMeta and the full server use to validate messages and execute commands is exactly the same. If the game logic was part of (or tightly tied to) Unity application it would not be able to share it like this.

These two diagrams showcase how the Local and Remote implementations differ.

![PlayerMeta Message Handling diagram][playermeta-1]
![PlayerMeta Message Shutdown diagram][playermeta-2]

## FPGMessages and Logic Units

PlayerMeta handles messages which represent any sort of client interaction. Messages tend to fall along specific domain lines - messages related to player account stuff, messages for Dynasty stuff, etc. These messages are handled by static and stateless "Logic Units" (as per the diagram). These logic units need to know the type of operation (e.g. the type of message in question) and also access to game data. Because how game data is stored is different for local and the remote metas (the former keeps it on disk, while the latter uses databases), the business logic calls take two parameters:

```c#
public static class DynastyDomainLogic
{
    public static FPGResponseMessage HandleRequest(FPGMessage request, IFPGDataContext context)
    {
        switch (request)
        {
            case GetDynastiesRequest getDynastiesRequest:
            {
                ... elided ...

                return response;
            }
```

The **IFPGDataContext** interface is implemented by LocalPlayerMeta, which acts as its own contest. On the Fealty server a datalayer object for SQL and document databases provides the context implementation.

## KGCommands and KGStateChanges

The FPGMessages discussed above are high-level messages between the FealtyClient and the PlayerMeta. One of these messages is **AttemptKGCommandRequest**, which contains within it data specified to something a player is trying to do within a Kingdom Game.

Command are logic objects that implement the IKGCommand interface:

```c#
public interface IKGCommand
{
    bool Validate(KGInstance kgInstance);
    List<KGStateChange> GenerateStateChange(KGInstance kgInstance);
}
```

Commands receive a reference to the running Kindgom Game instance for validation, and generate a list of changes. These changes are stored as part of the game instance, so that we can apply and unapply them later - effectively rewinding and fast forwarding the game.

```c#
public interface IKGStateChange
{
    void Apply(KGInstance kgInstance);
    void UnApply(KGInstance kgInstance);
}
```

Here is an example of a concrete IKGCommand implementation:

```c#
public class TransferResourcesFromCharacterToSettlement : IKGCommand
{
    ...

    public bool Validate(KGInstance kgInstance)
    {
        ... elided ...
        return (character.GetResource(ResourceType) >= DeltaValue);
    }

    public List<KGStateChange> GenerateStateChange(KGInstance kgInstance)
    {
        var changes = new List<KGStateChange>();
        changes.Add(new ChangeCharacterResourceValue(... elided ...));
        changes.Add(new ChangeSettlementResourceValue(... elided ...));
        return changes;
    }
}
```

What is particularly cool about KGCommands and KGStateChanges is that the Kingdom Game can be simulated/recreated very quickly and is totally deterministic. The game can use the collected information from state changes to know a lot about what is going, which is useful in many applications: to teach and develop nuanced AI, to commemorate critical moments in Kingdom Game history and allow anyone to watch them unfold.

With this architecture in place it has been very easy for me to add new pieces of functionality (new commands and state changes) very quickly - building the UI and gameplay feel is something else!

---

I hope this post was useful or interesting. It took longer than expected, and changed much in between drafts, but I think it ultimately provides a decent overview of the interaction between the system components. Next time I want to share with you the roadmap for Fealty as we progress through Alpha and start adding in features.

Thanks for reading!

---

[unity-app]: /public/images/posts/unity-app-architecture.png
[playermeta-1]: /public/images/posts/player-meta-message-handling.png
[playermeta-2]: /public/images/posts/player-meta-shutdown.png
