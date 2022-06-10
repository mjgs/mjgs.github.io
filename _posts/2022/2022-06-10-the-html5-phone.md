---
title: "The HTML5 Phone"
description: "Imagine a world where everything on your phone was rocking HTML5"
published: true
layout: post
date: 2022-06-10 20:01:00:00 +0700
tags:
- blogging
- writing
---
I’ve been having this re-occurring thought. I don’t know how feasible it is, but I wanted to write about it just in case. Wouldn’t it be awesome if there was an HTML5 phone?

The HTML5 phone would have all it’s UI built from HTML, CSS & Javascript, would likely run on a minimal Linux distro. Native apps would run in a custom NodeJS runtime, perhaps using something like Electron. It would be great for web developers, with the possibility to develop for the phone, on the phone. It could also leverage the web platform via PWAs. There’s a lot of variation possible, but the focus would be on HTML5 everywhere.

I think there are a lot of current trends that could make this crazy pipe-dream a reality that could gain traction:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Recent big push towards open web standards
- Move to privacy, phone OSs like Purism, the e/OS phone
- More alternative custom javascript runtimes
- Phone hardware is fast
- There are a lot of web developers out in the world at this stage
{: refdef}

Wouldn’t a [progressively enhanced OS]({{ site.baseurl }}/2022/06/10/os-progressive-enhancement.html) be cool? Always know, that the basic apps you need will always work, no matter what phone you have

It might not even be that difficult to start. Initially just create a bare minimum suite of apps, progressive enhancement style, that just do the very basics of the following apps:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Browser
- Email
- Camera
- Music
- Video
- Notes
- File Explorer
- Contacts
- Messaging
- Calling
{: refdef}

Build them as super simple web apps first. Once there’s something functional, enhance as needed, port to native apps etc.

The most difficult app is probably the web browser. I had initially thought that you could just have a browser and do everything with PWAs, but I think it’s sensible to have native apps to make sure you’re not forced to wait for web platform features. 

Anyhow some interesting posts about creating browsers that I found, just to get a sense of what’s involved:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- [How to get started building a web browser?](https://stackoverflow.com/questions/598841/how-to-get-started-building-a-web-browser)
- [How to build a web browser -- Part 1: Specifications](https://cheesecakelabs.com/blog/how-to-build-a-browser-pt-1)
- [Building a Web Browser Using Electron](https://blog.jscrambler.com/building-a-web-browser-using-electron)
{: refdef}

Yeah I know it’s a sort of crazy half baked idea, but I just keep thinking how awesome it would be, even if it was quite rough around the edges initially.

As a web developer, I’d like to have more control around my phone / mobile / tablet experience, so why not just do it all in HTML5?