---
layout: post
title: Rave Thru Dawn
published: true
made-with: HTML5 and impact.js
worked-with: <a href="http://ewjordan.com">Eric Jordan</a>, <a href="http://www.linkedin.com/pub/andrew-dolce/19/7aa/3a8">Andrew Dolce</a>, <a href="http://devpurkayastha.com/">Dev Purkayastha</a>, <a href="http://kadamwhite.com">K. Adam White</a>, <a href="http://theoneknownsoldier.weebly.com/">Greg Kinneman</a>, <a href="http://www.arshangailus.com/">Arshan Gailus</a>
game-url: http://ravegame.herokuapp.com
categories: [games, projects]
screenshot: ravegame.png
permalink: /games/rave-thru-dawn
---

## [Play {{page.title}}]({{page.game-url}})

## The Jam

Last weekend, my brother [Eric][eric] and I went to the [HTML5 game jam][jam] held at the MIT-[GAMBIT][gambit] game lab at 5 Cambridge Center. It was fun to be back around Kendall Square, the site of [my first tech internship][olpc]. I had a chance to see the newly minted [entrepreneur's walk of fame][wof], good stuff!

## The Idea and Team

After the 20+ attendees arrived (and, of course, caffeinated themselves), the organizers announced the Game Jam's theme: **Dawn**.

We spent some time brainstorming Dawn-themed game ideas and gave 30-second game pitches. I mumbled something about a 2D multiplayer version of the party game [Mafia][mafia].

One person pitched a **club DJ game**, where you play music and try to keep a crowd dancing *'till dawn*. Eric and I both liked it, so we joined up and our newly assembled team set up our hacking space for the weekend.

![Rave Thru Dawn mockup](/images/ravemock.jpg)

## Getting Started

Our first few hours consisted of:

1. defining our core game mechanic
1. deciding which parts to tackle first
1. strategically choosing a game engine
1. peeking at music sample APIs

Andrew and I were tasked with choosing a game engine. Because HTML5 game development is still in its beautiful infancy, there were no clear cut answers as to which engine (if any) would be worth using. On top of that, neither of us had done any significant javascript development or canvas work prior to this event, so we were eager to find something with good documentation.

[impact.js][impact] fit the bill well enough. It appeared to have out of the box support for animated sprites, class prototyping based on John Resig's [inheritance tutorial][inherit], and *damn* those are some [well-styled docs][docs]. Though it is a commercial game engine ($99!), impact's developer offered a free license to jam attendees. Oh, the seductive siren call of free things that *normally cost money*.

## Collaborating

Most of us had experience with git, so we went with it. Unfortunately, impact.js' source code is a super-duper-triple secret, so sharing our *entire* codebase publicly is big no-no. We decided to put up a temporary private repository.

Since we had 5 or so collaborators, github's free accounts would not fit the bill. We fiddled with [bitbucket][bitbucket] a bit but found that one of our team members had just enough room for private collaborators to host us on [github][github].

We did a good job of keeping our tasks separated by class and file, so our merge conflicts were minimal.

## Deploying

Early on, I set up a simple static file serving Heroku app ([ravegame.herokuapp.com]({{page.game-url}})) and continually pushed our game to it. This was very handy come presentation time, as we could hack on last-minute features knowing we had at least one good copy of the game ready-to-present from any computer.

## Game Developing

We ended up finding impact.js to be geared a bit too much towards one style of game development. At the time of the jam, it lacked a number of features that many HTML5 game developers would consider crucial:

* **Canvas text rendering** - the game supports writing text to the screen using [font sprite sheets][font] like this one:
<center><div style="background: blue; width:400px; align: center"><img src="http://impactjs.com/files/font.png"/></div></center>

>Unfortunately, that meant generating a font sprite sheet for each different font we needed. Were we not in a rush, that would have been doable, but for this jam, we needed to prototype by resizing and playing with font sizes and colors on the fly. Fortunately impact makes accessing the canvas element easy, so inserting text was a simple matter of adding a call to <code>ctx.fillText</code> and accounting for camera position. Dominic explains the lack of canvas text:

>> ([from dominic][dommsg]) *ig.Text uses bitmap fonts for two reasons: 1) at the time I wrote this class some browsers (Opera) didn't support the canvas text API and 2) I like pixel fonts :) [...] I'll probably add a mode for ig.Text that uses the native text rendering methods instead of bitmap fonts.*

* **Image motion tweening** - Eric ended up writing some beautifully hack-y code to make our club visitors move place to place.

* **Layering** - layering ended up being a bit hacky. Sprites could be given a z-location, and that let us do some sorting to show certain sprites in front of others. For the canvas elements we hacked on, we had to make sure we drew to the canvas after rendering the sprites.

Impact's class system and sprite-based animation capabilities were very useful, though. We also saw other teams using impact's out-of-the-box physics and mapmaking functionality. You can get a platformer prototyped in a couple of hours using impact.

## [Play Our Game: {{page.title}}]({{page.game-url}})

[![Rave Thru Dawn screenshot](/images/ravegame.png "Rave Thru Dawn screenshot")]({{page.game-url}})

**Instructions**: You are DJing. Play popular songs to make your club's visitors happy. Click "Record Bin" or **press Tab or Space to select a song**. You can queue up two songs at a time. Collect CDs to make money to play more hits!

## User Feedback

Though there was little wiggle room in terms of time for niceties during the 2-day jam, I made sure to show the game to a couple of people and see how they interacted with it.

* **Switching contexts** - I was initially against the context-switch between the floor view (where you see visitors dancing and dropping CDs) and the record bin. Once we had a chance to play-test a bit, I warmed up to it a bit. The player's awareness of the game state while context switching becomes an element of the gameplay, and interestingly feels a bit like DJing.

> One of our first players tried using spacebar and tab to switch between the record bin and the game view. Clicking the small tab to enter the record bin is a challenge in itself. I added those key bindings just before we did our presentation. In later play trials, a number of users spontaneously came across these keys.

> My school's game development course professor was confused by this and said "I think something's wrong with the game, you have to scroll down to see the songs".

* **What do I do?** - When you show someone a game, they want to know how to win. What constitutes success? What do I do now? *Don't neglect the instructions.* Even adding a line below your game à la [Kongregate][kongregate] can get you from "your game is unplayable" to "your game is boring" for free.

## Awesome Team

My team was awesome. Thanks {{page.worked-with}} and the Boston HTML5 Game Jam organizers!

[eric]: http://ewjordan.com
[gambit]: http://gambit.mit.edu/
[olpc]: http://wiki.laptop.org
[wof]: http://entwof.org/
[jam]: http://bostongamejams.com/2011/11/15/html5-game-jam-this-weekend-mocospace-sponsorship-and-impactjs-license/
[impact]: http://impactjs.com
[docs]: http://impactjs.com/documentation/class-reference/game
[inherit]: http://ejohn.org/blog/simple-javascript-inheritance/
[bitbucket]: https://bitbucket.org/
[github]: http://github.com
[font]: http://impactjs.com/documentation/class-reference/font
[dommsg]: http://impactjs.com/forums/help/canvas-text-vs-impact-font
[kongregate]: http://kongregate.com
[mafia]: http://en.wikipedia.org/wiki/Mafia_(party_game)