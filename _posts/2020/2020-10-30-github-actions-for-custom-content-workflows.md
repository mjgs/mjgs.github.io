---
title: GitHub Actions for custom content workflows
published: true
layout: post
date: 2020-10-30 19:24:00:00 +0700
tags:
- github
- workflows
- automation
- content
- linkblog
- nodejs
- jamstack
- programming
---
I’ve spent the past few weeks making some updates to the build system of the latest incarnation of my long running [linkblog](https://links.markjgsmith.com), now a statically generated website. In doing so I had my first chance to try out [GitHub Actions](https://github.com/features/actions) and what I discovered is an extremely versatile tool that makes it possible to create a very wide variety of software developer workflows, centering predominantly around coding activities.

I believe another area where Github Actions might be very effective is in modern collaborative workflows for content creators. And this is happening now because of the recent resurgence of building static websites in a way refered to as the [Jamstack](https://jamstack.org). 

In this post I’m going to describe the pieces of the puzzle, and the types of workflows that are possible, but without a lot of the complicated jargon.

[Github](https://github.com) is most well known for hosting repositories, places where developers can collaborate on code. It’s really a web interface for the open source git command line tool, which can be used completely separately, but their interface has become very popular over the past few years, and they are a big reason why there has been a renaissance in open source software.

Github Actions is their workflow automation tool, and it has a focus on automating tasks in and around repositories. It makes it possible to trigger custom actions when various repository events happen, such as adding new content, or when users have reviewed content, or when discussions mention a certain keyword, and lots more. It’s really very versatile.

The Jamstack movement is a way to build websites that has become popular recently. It focusses on pre-rendering all the pages of a website so that they are static files, rather than have a server running an application that dynamically renders the pages when they are requested. There is a lot of variations and nuance to what it encompasses but that’s the general idea. A lot of the technology isn’t actually new but it’s the first time this way of thinking about and building sites has had a name, and it’s resulted in some very interesting forward motion in how websites are built.

There are a lot of benefits to Jamstack sites including:

- Security because there’s no server to hack
- Speed because all the pages are pre-rendered 
- Being a naturally a good fit for automation 

And it's this last point that opens up new possibilites for collaborating.

I’ve been running my [linkblog](https://links.markjgsmith.com) for close to 10 years, there is a lot of content, but it’s possible to render out all the site pages in just a few seconds. I’ve built my own static site generator (SSG) tool in NodeJS because I’ve been able to optimise for that use case specifically, but there are many open source [SSG](https://jamstack.org/generators) tools out there.

One of the major benefits of creating a content workflow that uses git, is that you gain all the safety that makes it a great code collaboration tool. By using similar, all be it simpler, workflows to developers you can be quite confident that you won’t loose any work. It’s all just text files, and everything is versioned. As well as safety you get a considerable amount of future proofing because in the end it’s all just text files, so much less danger of software update breakages, and since it’s based on standard git tools you can move to another hosting provider relatively easily. Most of the providers have their own workflow tools but there is some interoperability, [Bitbucket](https://bitbucket.org) for instance can run Github workflows, and making platform specific tweaks isn’t that difficult in a lot of cases.

As an example, for my linkblog I have some HTML forms built using [serverless](https://css-tricks.com/serverless) cloud functions, that I use to easily add new content to a Github repo throughout the day. I have a scheduled workflow that runs at the end of every day and merges in the new content in a safe way using what is called a ‘Pull Request’, often referred to as a PR. This makes it easy to revert the merge if that’s ever necessary. There is then another workflow that detects newly merged content and triggers a site re-build, and then a deploy to the website hosting provider, and the site is live with the new content.

It’s also possible to use some of the other tools that Github provides as part of the workflow, for example the Issues and Pull-Request pages, to create places where you can discuss new additions with collaborators, as well as setup notifications, and to only publish content that has been approved by a certain number of reviewers.

It’s not strictly text based content either, as part of my updates I added a [podcast](https://podcasts.markjgsmith.com) to my website. The files are hosted outside of Github, but the GitHub action renders all the podcast pages and creates the RSS feed. 

If you want to listen to some very experimental audio, the [show is in iTunes!](https://podcasts.apple.com/gb/podcast/mark-smiths-podcasts/id1537049970)

Also if this type of content workflow is interesting to you, feel free to get in touch with me to let me know. I might post more details, tips and tricks about the workflows I am using.

I’m also available for hire on projects you have. Check out my [Github profile](https://github.com/mjgs).
