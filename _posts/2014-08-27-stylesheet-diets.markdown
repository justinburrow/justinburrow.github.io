---
layout: post
title:  "Stylesheet Diets"
date:   2014-08-27 12:00:00
categories: rambling
tags: Development
---
We've been on a performance enhancement kick lately, really trying to reclaim some of the page speed performance loss due to the inherent Magento bloat. A lot of this is happening server-side, by incorporating Akamai caching and Varnish to make sure that pages are immediately available to users in a broad geographic region.

On the front end side of things, I've been pushing forward initiatives based around a talk that Paul Irish gave at An Event Apart Boston 2014\. It was generally geared towards improving performance for mobile devices by decreasing round trip responses and factoring in 3/4G latency, but many of his points were applicable to the desktop experience as well. Concatenating JS and moving it to be non-blocking, working in critical CSS into the first 14kb packet, optimizing images, looking at the holdup for first paint in webpagetest.org, etc.

<!--break-->

After working through a lot of these big wins, one looming area of improvement was purging out unused CSS from one of our site's stylesheets that had a redesign which resulted in the new styles simply being appended below the old ones. It was hard to discern what was still being inherited and what wasn't being referenced anymore.

Addy Osmani wrote a great Grunt tool called "UnCSS", but you can't really run this in a Magento repo.

After racking my brain for a few days over how we could utilize something like this for the immediate need as well as moving forward, here's what I came up with:

*   List out each "page type" for your site - Home Page, Category Page, Product Page, Search Results, Account Pages, CMS Page, Landing Page, Cart, Checkout...
*   Visit one example of each of these types and save the HTML into a directory
*   Copy over the main stylesheet for the site into this directory as well
*   Initialize Grunt, create the Gruntfile.js and register UnCSS per the documentation with the filenames for the saved pages
*   Run UnCSS, add the new stylesheet with a unique name into the repo, and update page.xml to reflect this new stylesheet
*   Manually hand-crawl your site looking for any pages with broken styles and add these into your UnCSS directory/Gruntfile.js, re-run as needed

It's not the prettiest, but it worked. I managed to trim nearly 100kb out of the stylesheet for the offending site. Not a huge performance gain when it's being cached so heavily, but definitely impacts browser rendering speed.