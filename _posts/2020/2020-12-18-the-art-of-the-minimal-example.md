---
title: The art of the minimal example
published: true
layout: post
date: 2020-12-18 15:00:00:00 +0700
tags:
- web development
- programming
- nodejs
---
I’ve been putting together a [Portfolio]({{ site.baseurl }}/portfolio) of my work this past week. It’s been really interesting re-visiting the web development, workflow/automation and devops/sysadmin projects I’ve been involved with over the years. One thing that stood out was all the minimal examples I’ve built in order to either learn a technology or debug a feature.

Creating minimal examples is particularly enlightening, it’s actually quite a skill to be able to extract just the code you need to demonstrate a problem you are experiencing. It’s useful because you get rid of much of the complexity of the code you are working on and can focus in on discovering the root cause of an  issue.

Stackoverfkow even has a special  [minimal reproducible example](https://stackoverflow.com/help/minimal-reproducible-example)  page which has guidelines on how to create one. For stackoverflow questions you would likely have just a few small snippets of code to demonstrate an issue

I’ve included a [Minimals]({{ site.baseurl }}/portfolio#minimals) section in my portfolio, that links to many of the repos I’ve created over the years when I was looking to learn a particular feature or troubleshooting an issue I was experiencing. These aren’t strictly speaking minimal examples in the stackoverflow sense of the term, they tend to be a little bit more involved. In my case they are often small apps that implement just the feature I was exploring or debugging. They get rid of the complexity of the surrounding code, making it easier to reason about. I find myself often revisiting these minimals when I need to implement similar functionality somewhere else.

The ability to easily create runnable minimal examples I feel is one place [NodeJS](https://nodejs.org) really shines, especially when you are building [Express](https://expressjs.com) based web applications. This makes it easier to debug complex problems and communicate your findings to others you are working with. 

Related post: [Reasons to use NodeJS for developing your backend systems](https://blog.markjgsmith.com/2020/12/04/reasons-to-use-nodejs-for-developing-your-backend-systems.html)
