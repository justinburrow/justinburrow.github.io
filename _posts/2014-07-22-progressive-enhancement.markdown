---
layout: post
title:  "Progressive Enhancement"
date:   2014-07-22 12:00:00
categories: writing
tags: Development
---
Working on corporate sites means supporting a lot of antiquated browsers. In an ideal world, it'd be great to put up a **"Stop using this crap browser!"** modal dialog with a link to Chrome for any IE version less than 11, but when you're dealing with potential business users sitting behind a network administered by IT guys who don't want to deal with having to figure out how their Java based CRMs are going to play nice with browsers that have evolved since that software was developed, you just can't develop in a way that doesn't involve a decent user experience for these archaic environments.

<!--break-->

To this end, it's easy to read all the hip design blogs that spotlight great new HTML features (like the new ['dialog'](http://www.w3schools.com/tags/tag_dialog.asp) element I was just reading about that is only supported by WebKit browsers) and breathe your exasperated sigh, knowing that you'll just have to settle for some baked-in jQuery solution (like the [Vex](https://github.com/HubSpot/vex) library, which we've been using for about a year).

I can't begin to describe how many times I've written inline Javascript on an input field for placeholder text, even though the HTML5 spec includes a 'placeholder' attribute. Lower than IE10, and the user just doesn't see anything. We **just** stopped supporting IE7, so we're still quite a bit away from ignoring those users on 8 and 9.

At An Event Apart Boston this year, [Jeremy Keith](http://adactio.com/) discussed progressive enhancement in great detail. It's a concept I've been familiar with - making sure that any new tech utilized includes graceful degradation for older browsers - but his ethos was that progressive enhancement should be the strategy, not a stop-gap when you really, _really_ want to utilize a new feature.

There are a few great features that gracefully degrade to a usable extent, that can be implemented right now.

*   **Input types** - HTML5 introduces new input type attributes, like number, date, and tel, which have great UX benefits on mobile devices. Desktop browsers simply behave the same, which means UX improvement for some users, with no net loss for others.

*   **[Modernizr](http://modernizr.com/)** gives you the ability to utilize a number of new HTML5/CSS3 feature sets, and also a custom build option to slim down the JS needed.

I'm done with the days of letting old browser support dictate the feature sets implemented. Designing this way essentially ensures that the minute the product is shipped, it's already obsolete. Moving forward, we should all hold ourselves accountable to designing for the future, while making sure that those who haven't quite caught up yet still get a usable experience across the board.