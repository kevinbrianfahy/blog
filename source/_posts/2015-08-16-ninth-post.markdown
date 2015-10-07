---
layout: post
title: "Week 9"
date: 2015-08-16 22:26:28 -0500
comments: true
categories: 
---

We had a great time with jQuery!! I learned how to hide elements in my html that I can later show with jQuery. And not just that, but I can animate those elements when I decide to show them. Sorry, CSS selectors, I now have a new most-fun project. The more fun, the longer it takes, as this project definitely took longer than arranging selectors with triple gradients and 45 degree angles. By the time I was done with this project, I was using pure JavaScript in addition to jQuery.

I had the idea to try and get people interested in watching the video on my home page, rather than just clicking the navigation links at the top of the page right away (our capstone project is to build our own portfolio website). After some tedious cropping away at an image of a stage with red curtains, I attempted to have curtains slowly move in from the side of the screen when someone simply put the mouse over the video. That in itself was extraordinary fun, but the real surprise to me was how the project kept evolving. That's what I love about learning programming, once you have an idea, you can constantly improve upon that idea to truly make something fun, interactive, and special to both user and creator.

I also knew I could create a class in CSS to make the background black, like a theatre, and then add that class in jQuery. I added a drape, above the video, dropping in from the top, and delayed the curtains from the side. It wasn't until then that I decided to do some research on my own, going beyond our class curriculum, and look up what could be done to initiate the effect on video play, not just mouseover. Turns out there is an event handler for the video element in html 5 that will allow not only to initiate the jQuery sequence at video play, but also allow it to cease at video end! This was perfect! I could have the curtains pull back immediately when the video ended.

And you know what? In the process I even learned how to create my own play and stop buttons using pure JavaScript! Although jQuery had an event handler for playing, it does not make use of the .play() method used to create the play button. By the time I was finished, I had learned the workaround for this (to pull a native DOM element) in jQuery using .get(0), and the JavaScript alternative of document.getElementById(). Needless to say, I am very happy with this last week's project. :-) 