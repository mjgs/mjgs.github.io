---
title: Deciding when to build a custom solution in web development
description: A high level way to think about web development that should make it easier to decide when to build and when to buy
published: true
layout: post
date: 2020-12-11 13:53:00:00 +0700
tags:
- web development
- programming
- services
---
The web has been around for just over 3 decades now, with the capabilities of the sites we build increasing every year. With that forward movement there’s a corresponding rise in complexity. For website builders this presents somewhat of a dilemma. When you start out, you don’t have the experience to build things for yourself, but you still want to have an online presence. Luckily it’s easier than ever to get started quickly with many website builder tools available. But how do you know when building something custom is appropriate?

Answering that question when you are deep in the weeds of designing and building a site, can be challenging. I think it’s useful to have a mental model that enables you to step back and see the woods for the trees.

Building a website is a bit like building a shed. Right off the bat you can choose to buy a prefab shed, and that’s a perfectly good solution. The suppliers of these often have several models to choose from, so if one of them meets your needs, it’s going to be quick to get up and running. There is of course also the option to customise your prefab shed, make it look a bit more like your favourite style. However you might have some very specialist requirements, because of where the shed will be located, or maybe you need some electrical wiring for your home office which you plan to have in your new shed. In those situations it might make sense to build a complete custom shed that fits your requirements exactly.

It’s similar with software. There are many off-the-shelf solutions that might fit your needs. There are hosted services and also open source frameworks like [Wordpress](https://wordpress.com) that will make it easy to get a site up and running, and enable tweaks using themes and plugins. In situations where this meets your needs, that’s probably going to be the best route.

Of course the web isn’t just sheds. The analogy scales up too. There are houses, hotels, community centres, sky scrapers, towns, cities and we can continue scaling up. As your infrastructure grows, your requirements will evolve. You’ll want to create resiliency, by splitting your backend into several components. To some extent you might be able to modify your Wordpress sites to fill these needs. But don’t assume that Wordpress will solve all your problems, it’s totally possible to build a custom Wordpress monstrosity, same goes for any custom software.

One of the downsides of the prefab solutions that large frameworks offer is complexity. Along with all the useful heavy lifting that the frameworks offer, comes a big increase in the amount of code. If you ever need to get into the code yourself, rather than have a developer modify it for you, it might be a challenge.

Having a custom solution that is very focussed on solving exactly the problem you are trying to solve, has the possibility to be much much more streamlined, less code, easier to understand if you ever need to get into it yourself. Starting small and growing progressively as your needs change can ensure that you don’t suddenly find yourself in a sea of complexity, overwhelming your efforts to get a site live.

If you are considering a custom solution, you might want to look at [NodeJS](https://nodejs.org/en). It’s designed specifically for network based applications, and it’s possible to build very focussed low code applications that are extremely performant and easy to maintain. I recently wrote about the [reasons for using NodeJS for building your backend systems](https://blog.markjgsmith.com/2020/12/04/reasons-to-use-nodejs-for-developing-your-backend-systems.html), you might find that interesting.

The analogy in this post was inspired by a [recent Shop Talk episode](https://shoptalkshow.com/442). Great podcast that covers frontend and increasingly backend web development topics.

Hopefully this gives you a bit of a better idea of the software development landscape, and a neat macro way to think about your web development projects.

*This post is part the [choosing your web development stack]({{ site.baseurl}}/2020/12/13/choosing-your-web-development-stack.html) series.*
