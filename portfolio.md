---
title: Portfolio
layout: page
permalink: "/portfolio/"
---
## Web Development

### Eleventy Agile Blog

[eleventy-agile-blog](https://github.com/mjgs/eleventy-agile-blog) - Blog template that implements a simple agile development workflow, so you can manage a backlog of stories, getting them done over the course of sprints

### Serverless books API

[serverless-books-api](https://github.com/mjgs/serverless-books-api) - Implements a Books API for a Library, intended to be run on AWS Lambda/DynamoDB using serverless

- Functions run on AWS Lambda
- Data is stored in AWS DynamoDB
- Uses domain driven design techniques with handlers/utilities/adapters layers

### Internet of Things App

[internet-of-things-app](https://github.com/mjgs/internet-of-things-app) - System to collect and process realtime data of devices in an iot fleet

This project is an MVP of an Internet of Things (IOT) application. The scenario is one where there are devices that are geographically distributed and are moving, so could be delivery or perhaps passenger vehicles. The application receives data updates from devices, proceses the data and then displays the data. In this specific example the device speed is calculated. Generally speaking it is a way to collect and process realtime data.

### Freelancer

[freelancer](https://github.com/mjgs/freelancer) - Website for freelancers with homepage and payments pages to securely receive payments for services

Website for freelancers that runs sites. Each site can be static and/or dynamic, you can easily associate domain names to each site and adding a site is as simple as creating an express app and adding it to the apps folder. Payments are handled by Stripe and email notifications are via Mailgun

### Linkblog.io

Linkblog.io was the minimalist link curation tool, a cloud/SAAS NodeJS web application for managing your daily links. I created the infrastructure, the automated server provisioning system, the code build and deployment system, developed the website and REST API, and the fault tolerant backend that processed jobs using a scheduler, message queues and webhooks. There were robust unit and integration test suites for all the NodeJS code.

<iframe src="{{ site.baseurl }}/assets/images/Linkblog.io Portfolio - 2020-02-27.pdf"
        width="100%"
        height="500px">
</iframe>

[Direct link to pdf file]({{ site.baseurl }}/assets/images/Linkblog.io Portfolio - 2020-02-27.pdf)

<br>

More information in these blog posts:

- [Robust NodeJS Deployment Architecture](https://blog.markjgsmith.com/2020/11/13/robust-nodejs-deployment-architecture.html) - A writeup of the tech stack
- [Looking back at linkblog.io](https://blog.markjgsmith.com/2020/11/26/looking-back-at-linkblogdotio.html) - A look back at the project goals, application level features and automation systems
- [Building the foundations for the future of linkblog](https://blog.markjgsmith.com/2019/12/06/building-the-foundations-for-the-future-of-linkblog.html) - Describes the redesigned billing system that I implemented

### Minimals

These are minimal apps created for the purpose of learning a specific feature.

- [minimal-express-typescript](https://github.com/mjgs/minimal-express-typescript) - Minimal express app written in typescript with npm scripts to run the app in the vscode debugger
- [ejs-layouts-using-includes](https://github.com/mjgs/ejs-layouts-using-includes) - Minimal express app implementing layouts using ejs includes
- [nockback-test](https://github.com/mjgs/nockback-test) - Minimal test suite demonstrating nock's nockback feature that records 3rd party api test fixtures into separate files
- [passport-tests](https://github.com/mjgs/passport-tests) - Minimal express app and api that implement website authentication
- [vanilla-mvc](https://github.com/mjgs/vanilla-mvc) - Minimal examples of client-side mvc patterns using plain old boring vanilla javascript
- [react-webpack-project-template](https://github.com/mjgs/react-webpack-project-template) - Boilerplate for React projects
- [erm-flow](https://github.com/mjgs/erm-flow) - Minimal restify app using express-restify-mongoose module
- [restify-tdd-template](https://github.com/mjgs/restify-tdd-template) - Template for building apis using restify and tdd
- [react-tdd-project-template](https://github.com/mjgs/react-tdd-project-template) - Boilerplate/template for building React apps with TDD
- [fluxxor-flux-comparison-app](https://github.com/mjgs/fluxxor-flux-comparison-app) - Working example of the Fluxxor flux-comparison app that uses webpack, webpack-dev-server and has a mocha test environment configured
- [app-server-demo](https://github.com/mjgs/app-server-demo) - An express app for running express apps - drop express apps in the lib folder and start the server
- [app-server](https://github.com/mjgs/app-server) - Node.js module for building servers that run express apps

## Workflows and Automation

<iframe src="{{ site.baseurl }}/assets/images/Workflow Portfolio - 2011.pdf"
        width="100%"
        height="500px">
</iframe>

[Direct link to pdf file]({{ site.baseurl }}/assets/images/Workflow Portfolio - 2011.pdf)

<br>

I architected and/or built the following workflow solutions from the above portfolio document:

- ProsiebenSat – Ingest via Mx/Agent/Smartjog/Ftp, automated validation then manual validation, checking into MAM, export via Mx/Agent/Smartjog/Ftp
- Canal Plus - Ingest via FTP Pull/MX, media check, Agility transcoding, import into Sonaps and Avid editors
- Chellomedia - Ingest via Agent, movement of file bundles, Antivirus check, splitting of bundle on arrive in Lan, delivery of each piece to the right place
- TPC – Swiss Television - Avid export, transcoding, Sound recording, manual steps offered via Mx GUI, delivery to Playout
- Media City UK - Avid Gateway - easy ingest and outgest of avid projects
- Discovery UK - VOD preparation with automatic adding of bumpers, logos and subtitles, and automated quality assurance check

## Devops & Sysadmin

### Digital Intermediate

- Development of Arriscanner automated ingest pipeline for scanning reels of motion picture film, scan tracking, automated digital IR map dust bust and scratch removal using Pixel Farm’s PFClean
- D-Cinema KDM generation
- File ingest and processing solutions using Shake, edit decision lists (EDLs), FTP, Linux, for films including Children of Men, Happy Feet, Charlie and the Chocolate Factory, The Golden Compass

### Render farm optimisation

Optimisation of a render farm, operational logistics, liaising with producers, artists and software developers to troubleshoot problems and implement improvements in the render pipeline (RenderMan, Maya, Shake, Houdini).

<iframe src="{{ site.baseurl }}/assets/images/Render Farm Portfolio - 2005.pdf"
        width="100%"
        height="500px">
</iframe>

[Direct link to pdf file]({{ site.baseurl }}/assets/images/Render Farm Portfolio - 2005.pdf)
