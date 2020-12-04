---
title: Reasons to use NodeJS for developing your backend systems
published: true
layout: post
date: 2020-12-04 21:00:00:00 +0700
tags:
- nodejs 
- programming
- web development
- promotion
- services
---
There are a lot of programming languages to choose from when it comes to writing server-side code.  What makes NodeJS a good choice for this task? Whether you are embarking on a new project or  extending an existing one, it’s a very relevant question. In this post I’m going to cover the main reasons for choosing NodeJS for your backend application.

Javascript the programming language runs in two main environments:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- The web browser which runs client-side javascript
- The server which runs server-side javascript
{: refdef}

When programmers talk about server-side javascript they call it NodeJS, and when they write a NodeJS application they are actually writing javascript code. NodeJS is more than just the language though, it’s a whole environment  (called a runtime) that, among other things, can execute javascript code., but it also provides a way for the code to access hardware like the storage and the network adapters. 

The NodeJS runtime achieves this using an architecture that is optimised for creating network applications. This architecture is called the event loop. 

The event loop looks very much like a collection of queues. As the code runs, anytime something has to happen asynchronously, i.e. that will take a while to complete, the code to be run on completion, called a callback, is placed in a queue, so that the remaining code to be run can continue executing without blocking.

Asynchronous tasks would be for example writing to storage or making an API call across the internet. The event loop architecture makes it possible for the NodeJS runtime to be single threaded, and we say it’s event driven because the data input/output (I/O) from the hardware doesn’t block the code. Instead of blocking, events are triggered once the result of the I/O operation is ready.

This means that NodeJS is particularly good for applications that operate over a network, because it can handle many simultaneous requests very easily.

That’s the big architectural advantage that NodeJS offers, but there are quite a few other reasons to build your backend using NodeJS. 

Here is a summary:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Runtime environment is particularly well suited and optimised to network applications, the event loop architecture makes it possible for single threaded code to execute in a non-blocking way, resulting in a high capacity for handling concurrent requests and realtime data
- The NodeJS foundation is particularly well organised with a very regular release cycle, including long term support (LTS) releases
- Npm hosts a vast collection of community built modules, with mostly open source licenses, greatly speeding up development
- Of all the interpreted languages it is one of the fastest. It uses v8, the javascript engine written in C++ by Google also used in the Chrome web browser, very regularly updated, always being improved
- There are a huge number of javascript developers worldwide since javascript also runs in the browser. This means finding developers is easier
- It’s possible to use javascript throughout the entire application stack, from the client-side code that runs in the browser, to the code running on the server, and also with NoSQL databases many of which use javascript as the query language. The elimination of context switching results in massive boost in developer productivity
- There is a vibrant tooling ecosystem with developers around the world continuously building and sharing the best development tools
- NodeJS is cross platform, running on Windows, Mac and Linux
- Using libraries like Electron it’s possible to write mobile and desktop apps using NodeJS so you can have a single code base across mobile, desktop and web applications
- Typically promotes fast development, robust testing and code refactoring
- All serverless hosting providers have NodeJS implementations, microservices are very often written in NodeJS
{: refdef}

It’s also worth reading the [nodejs website about page](https://nodejs.org/en/about) for more details.

Companies such as Netflix, PayPal, Trellio, LinkedIn, Uber, eBay, Groupon, NASA, Mozilla, Twitter and Walmart are examples of big tech organisations that run significant amounts of their infrastructure on NodeJS. More details [here](https://softwarebrothers.co/blog/companies-that-use-node-js) and [here](https://youteam.io/blog/top-companies-that-used-node-js-in-production).

NodeJS makes it possible to build extremely robust network applications quickly and at low cost, that are then easier and cheaper to refactor, extend and maintain.
