---
layout: post
title: WIP - One Year Ago
tags: general
comments: on
---

Today is a special day because today the Fealty codebase is one year old!

![alt text][first_commit]

I always enjoy looking back at my projects and taking notice of how far they have come. At the same time, it feels like just yesterday that I started.
<!--more-->
This is the earliest screenshot of Fealty.
<button id="spoiler_btn" class="accordion btn" style="width: 200px; text-align: center;">Show</button>
![Earliest screenshot][black]{: .post-image .panel}

And this is the second earliest screenshot =D
<button class="accordion btn" style="width: 200px; text-align: center;">Show</button>
![Second earliest screenshot][beginning]{: .post-image .panel}

At this point in time there was no behavior yet. The first things I got working was camera panning and zooming, and the loading of the sprites. The sprites came from the [Toen's Medieval Strategy](https://toen.itch.io/toens-medieval-strategy) package by André Marí Coppola. I have a hard time with sticking "dev art", but I did not want to get sidetracked by looking for art at this point of the project. André's sprites were varied enough to cover most of what I needed (we are actually STILL using them in places), which I found to be unusual. There is a lot of open source art out there, but it can be very difficult to find sprites from different artists that match well together. The Toen sprites were great for letting me focus on what was most important.

After a week or so, the camera was working as I wanted and I had begun to add some preliminary UI.
<button class="accordion btn" style="width: 200px; text-align: center;">Show</button>
![Camera functionality][gif]{: .post-image .panel}

One of the original concepts was the idea that buildings had a "Area of Command" which would limit where you could build and interact with the world. Ultimately this proved to be not-so-great and didn't add much to the game so it is no longer a thing. As a Unity noob I also tried my hand at my first scrolling rect panel, used for showing building blueprints - and you can see in the GIf how poorly that turned out.

By the end of January, I had the character goal-based AI in place and building construction was functional. You can also see a resource bar along the top, which is something else that is no longer in the game. I had also added Saving and Loading to the game (or at least the UI buttons - I am not sure if they were actually functional at the time!)

And here is some actual action on the screen!

<button class="accordion btn" style="width: 200px; text-align: center;">Show</button>
![A little more game][gif2]{: .post-image .panel}

Looking back at it now, it's funny to realize both how much is the same and how much has changed. If I showed you the game today you would certainly recognize it, but its almost unreal to see what it looked like just a year ago. Among other things, the goal-driven AI has changed a lot - the architecture is mostly the same, but the implementation details for the discreet tasks is much more robust and "world-aware". The UI is slicker and predictable, without bugs like the weird scrolling glitches you see in the first GIF. You can learn a lot in a year!

In the next WIP I want to talk about the code architecture for the game, and go into [some] details on how the *Fealty* simulation engine is able to support thousands of players at the same time.

Thanks for reading!

---

[first_commit]: /public/images/posts/first_commit.png
[black]: /public/images/posts/the_beginning.png
[beginning]: /public/images/posts/beginning.png
[gif]:/public/images/posts/ui_gif_warts_and_all.gif
[gif2]:/public/images/posts/functional.gif

<script>
var acc = document.getElementsByClassName("accordion");
var i;

for (i = 0; i < acc.length; i++) {
  acc[i].addEventListener("click", function() {
    if(this.id === "spoiler_btn") {
        if (this.firstChild.data === "Show") {
            this.firstChild.data = "Ha Ha!";
        } else {
            this.firstChild.data = "Show";
        }
    }
    else{
        if (this.firstChild.data === "Show") {
            this.firstChild.data = "Hide";
        } else {
            this.firstChild.data = "Show";
        }
    }

    this.classList.toggle("active");
    var panel = this.nextElementSibling;
    if (panel.style.display === "block") {
      panel.style.display = "none";
    } else {
      panel.style.display = "block";
    }
  });
}
</script>