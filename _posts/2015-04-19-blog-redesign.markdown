---
layout: post
title:  "Blog/Portfolio Redesign"
date:   2015-04-19 12:00:00
categories: portfolio
tags: Design Development UX
---

Last year, I had set up a quick-and-dirty blog/portfolio using a new static site generator call Ghost.  It was functional, but had some deployment issues that I wasn't completely comfortable with - I just didn't invest the time to sort these out.

Static site generators, like Ghost, had really intrigued me.  I've had plenty of experience building a variety of types of Wordpress-based sites, and in general, unless you're handing the site off to a non-technical business user, they feel exponentially bloated.  I liked the flexibility of editing content via a CMS and having templated layout files, but frankly, setting up a MAMP stack for each website built on Wordpress was becoming tedious.  I've been getting used to having Grunt set up a local server and live-reloading pages - these days, setting up a new Wordpress install feels like a step in the wrong direction.

*Note: I'm not saying Wordpress is dead, or is useless.  It has its place.*

These are the criteria I wanted to hit with my blog relaunch:

* Hosted on GitHub Pages (I really don't see the point in paying for hosting unnecessarily)
* No DB required if possible
* Grunt task-running for easy deployment
* Git version control
* Responsive
* Performant

I went back to the basics of static site generators: Jekyll.  When I started exploring static site generators, Jekyll seemed a little daunting, but after working with a bare-bones install, I started to understand how it worked and how to hook up the other functionality I needed from it.

The responsive criteria was met by dropping in Bootstrap CSS.  To do this, I used Bower to manage my package dependencies.  Bootstrap came with jQuery, which is great.  However, I didn't want to deploy the entire "bower_compenents" folder to GitHub Pages.

The solution to this end of things came about in the solving of a separate, unrelated issue.  There are a lot of great Ruby generators for Jekyll that allow you to do things like generate categories and posts associated to them on the fly at compile.  GitHub Pages will compile Jekyll for you, but disables the usage of these plugins for security and safety reasons.

By creating a subdirectory to contain the compiled HTML files for deployment, you can run the compilation locally and simply deploy HTML to GitHub Pages to get around this.

For the "bower_components" directory issue, I have "grunt-contrib-copy" running at compiliation which takes the minified files for Bootstrap .css/.js and jQuery .js, and copies them to my distribution site folder, which my templates then reference.

*Can't really take credit for this - some other genius came up with this solution.  I just appropriated it.*

So now I have two separate directories to version control.  Easy - set up the dist folder to the master branch, and create a source branch for the source files.

It creates a little complexity as the process requires two separate commit and push steps since things are contained in two different branches, but it's a small sacrifice for the larger flexibility of this approach.

By nature, Jekyll doesn't require a DB and is highly performant as the compiled files are straight-up HTML/CSS.

So far, I'm pretty happy with this new rollout.  I'll continue to tweak and add to it as it evolves, but it's a great starting point featuring some pretty modern approaches.