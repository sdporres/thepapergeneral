---
layout: post
title: Tech Debt Tuesday - Game Strings - Part I
tags: tech
comments: on
---


Hello, my dear people. It has been almost a month since I wrote to you last and it has been a busy time. There is always a lot to do, of course, and the first casualty becomes writing.

But the good news is that lots of progress has been done in a few areas. Today I want to focus on what I was working on yesterday, which was addressing a tech debt issue with how I had implemented the handling of game strings.

When I say "game string" I am referring to the text content that players see as they play the game. The most direct way to work with game strings is to create them where you need them.<!--more--> Something like:

MyLabel.text = "Do you really want to do that?";
This contrived example is quick and easy when you are in the heat of the moment. Eventually, you might discover that you need the same piece of text in multiple places and maybe move it to a class where anybody can have access to it. That might look like this:

```c#
MyLabel.text = StringManager.GetConfirmationString();

// elsewhere in the code ...
public string GetConfirmationString()
{
    return "Do you really want to do that?";
}
```

This is better, and will get you by until one of two things inevitably happens:

1. You want to change the string without having to recompile the source code
2. You want to localize your game

The two issues are related that achieving #1 makes #2 much easier. If you can change your game strings (e.g. modify them, or localize them) by simply editing a text file then its possible for a non-programmer to do that - someone like a writer who might be gooder at the grammars.

Your grown up game string implementation then might look very similar on the surface, except that you make your string-fetching method take a look up key:

```c#
MyLabel.text = StringManager.GetGameString("Player.InputCommand.Confirm");

// elsewhere in the code ...
public string GetGameString(string lookupKey)
{
    // currentUserLanguage tells us which language of strings to index (implemented elsewhere)
    return _collectionOfStrings[currentUserLanguage][lookupKey];
}
```

An important part is how the _collectionOfStrings gets its data - which could be from the local file system, or remote overly the Internet.

At this point we have a data-driven game string system that empowers non-programmers to improve the game and that supports localization.

Our next consideration is that some game strings need to use contextual data. A good example of this are the military related game strings, which often have to refer to size of the unit, the captain, or the type of unit (serf levy or freemen company).

A first stab at that might use the great string interpolation features of C# like this:

```c#
var rawString = StringManager.GetGameString("Action.RecruitCompany.Details");
MyLabel.text = string.Format(rawString, company.Size, company.Name);

// elsewhere in the code ...
public string GetGameString(string lookupKey)
{
    // currentUserLanguage tells us which language of strings to index (implemented elsewhere)
    // in Fealty, each language has its own data file
    return _collectionOfStrings[currentUserLanguage][lookupKey];
}
```

... and your string data might look something like ...

```c#
{ "Action.RecruitCompany.Details", "I will recruit {0} troops for the {1}!"}
```

Now your game strings are friggin' sick, and full of contextual meaning. And easily changed by non-programmers!

The day after all these awesome changes are deployed, just as the game strings are getting some love, the game starts crashing. It starts crashing in places where it had never crashed before, so its mystifying.

When you look at the logs, you might see something like:

Exception: Index (zero based) must be greater than or equal to zero and less than the size of the argument list.
Exception: Input string was not in a correct format.
These errors are the result of trying to interpolate the wrong number of arguments into a string. For example, if someone (could be you!) decided that having the unit name in the recruit game string was overkill, you might change your string to:

```c#
{ "Action.RecruitCompany.Details", "I will recruit {0} troops!"}
```

And now the game crashes just trying to parse a silly game string. (You could make your game resilient to crashing, of course - but I learned that crashing as soon as something goes wrong is often better; otherwise you end up investigating "fake" bugs that are only symptomatic of the initial error)

Your "easy to change" game string system is also a terrible and dangerous weapon - a fragile Achilles's heel. There is also another issue that we have not talked about which is that if you want to change the contextual data available for a string to interpolate then you have to change code (e.g. to add a new variable to the interpolation). The game string implementation is fragile and limited in what a designer can properly change.

Lastly, each action in the game also had to implement this:

```c#
public abstract string GetNameString();
public abstract string GetIntroString();
public abstract string GetStartString();
public abstract string GetConfirmString();
public abstract string GetRunningString();
public abstract string GetGoalString();
public abstract string GetCompletedString();
public abstract string GetHistoryTitle();
public abstract string GetHistoryDetail();
```

Yuk.

This situation was tracked on my Trello board as a card in the Tech Debt column, where it has been sitting for a few months. Fortunately, I finally had enough idle brain cells to passively come up with a solution to this problem.

Check back for Part II of this - sometime soon.
