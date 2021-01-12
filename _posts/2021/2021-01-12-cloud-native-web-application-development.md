---
title: "Cloud Native web application development: what's it all about?"
description: A look at Cloud Native web application development, what it is exactly and why it's likely to play a big part in the future of web development.
published: true
layout: post
date: 2021-01-12 07:28:00:00 +0700
tags:
- web development
- nodejs
- architecture
- infrastructure
- cloud
- programming
---
I've been reading and listening to a lot of content related to Cloud Native web applications recently, so I wanted to gather together some thoughts and links related to the topic.

I previously built a [robust NodeJS SaaS application](https://blog.markjgsmith.com/portfolio/#linkblogio), a [Serverless Books API](https://blog.markjgsmith.com/portfolio/#serverless-books-api) and some [Jamstack Architecture Content Sites](https://blog.markjgsmith.com/portfolio/#jamstack-architecture-content-sites), so I have experience in both conventional and cloud based web application programming. 

A lot of these technologies and paradigms are still somewhat in flux, but I think it’s worth adding my perspective to the conversation.
 
Here’s the general approach I'm going to take in this blog post:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- [The Cloud Native trend]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#the-cloud-native-trend)
  - [History]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#history)
  - [Benefits]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#benefits)
  - [Challenges]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#challenges)
- [Alternatives]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#alternatives)
  - [Infrastructure]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#infrastructure)
  - [Software Architectures]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#software-architectures)
- [Wrapping up]({{ site.baseurl }}/2021/01/12/cloud-native-web-application-development.html#wrapping-up)
{: refdef}

I'll also be adding in relevant posts from my [linkblog](https://links.markjgsmith.com). That's where I've been gathering links. There will be a link to that place in the linkblog so you can see the context around that link, in case you are interested, and also a link to the linked article. Those bits will appear as quotes and look like this:

From my linkblog [12-01-2021](https://links.markjgsmith.com/archives/html/2021/01/#11January2021):

> Lenovo unveils ThinkReality A3 smartglasses with Snapdragon XR1 - This makes me wonder is VFX artists are going to be really into AR tech, especially all the 3D folks [neowin.net](https://www.neowin.net/news/lenovo-unveils-thinkreality-a3-smartglasses-with-snapdragon-xr1?scrolla=5eb6d68b7fedc32c19ef33b4)

That's the very latest link on my linkblog as I write this, it doesn't have anything todo with this article, it's just an example to show you what those bits will look like.

Hopefully by the end you’ll have a better sense of where this trend is heading and thus a better idea of what the future of web applications could look like.

## The Cloud Native trend

### History

One of the big developer trends for 2021 is the move to Cloud Native applications. Historically applications have been built to run on standard Virtual Private Servers (VPS) hosting, often running a flavour of Linux. This was a step up from having to run applications on bare metal servers, adding flexibility and decreased costs. 

Over the past 10 years hosting providers have expanded their product catalogue from VPS hosting to offering a huge variety of services which can be integrated relatively easily into your application over the internet via [APIs](https://dzone.com/articles/an-api-is-a-promise-interacting-with-valuable-capa).

Another related trend in web development has been the resurgence of statically generated sites that make extensive use of APIs to carry out backend tasks. That trend is called the [Jamstack](https://jamstack.org), which is a broad term to describe websites that make use of javascript, APIs and markup to create sites that are performant, scalable and very secure. Providers like [Netlify](https://www.netlify.com) and [Vercel](https://vercel.com) offer file hosting packages bundled with [serverless](https://serverless.css-tricks.com/about) functions, making it possible to build websites without the need for classic VPS hosting.

Overall the move to the cloud has been gradual. When Amazon released S3 it’s simple file storage offering, [it wasn’t at all obvious](https://mobile.twitter.com/stevesi/status/1348041439603642368) to most where the industry was heading. At the time, [I was working in the visual effects industry](https://blog.markjgsmith.com/2020/11/24/what-its-like-working-in-tech-in-the-visual-effects-industry.html) at a company where all our tech was hosted on-premises. That was the norm, especially in post production. The idea that you would store files over the internet just didn’t seem realistic. There certainly wasn’t a general awareness of the explosion in APIs that was about to happen.

The technologies improved, and in recent years there has been broad adoption of cloud technologies across all industries, with application developers modifying their applications to offload certain tasks to these cloud based services. Amazon is the biggest player and has services such as [DynamoDB](https://en.m.wikipedia.org/wiki/Amazon_DynamoDB) (database), [S3](https://en.m.wikipedia.org/wiki/Amazon_S3) (file storage), [Route53](https://en.m.wikipedia.org/wiki/Amazon_Route_53) (DNS), [Lambda](https://en.m.wikipedia.org/wiki/AWS_Lambda) (event driven serverless compute), [SNS](https://en.m.wikipedia.org/wiki/Amazon_Simple_Notification_Service) (notifications) and [SQS](https://en.m.wikipedia.org/wiki/Amazon_SQS) (message queuing) to name a few. Other large hosting providers such as [Microsoft Azure](https://azure.microsoft.com/en-gb), [Google App Engine](https://cloud.google.com/appengine), aswell as smaller ones such as [Linode](https://www.linode.com/?r=42eb9f3079fe0eb52eb1bffdd39abf8c4eddb886) and [Digital Ocean](https://www.digitalocean.com) have similar offerings. These services provide highly available and effortlessly scalable solutions to common computing problems.

Cloud Native is the logical conclusion of this gradual move, with applications being designed and implemented to run completely on cloud services. 

From my linkblog [31/12/2020](https://links.markjgsmith.com/archives/html/2020/12/#31December2020):

> Software Engineering Podcast - Cloud-Native Applications with Cornelia Davis (Repeat) - Looks at applications architected and built to run exclusively in cloud environments, covers event driven architectures, functional programming, infrastructure as code, Kubernetes, immutability and workloads, cloud failure domains, statelessness, microservices vs monoliths, and the new cloud abstractions such as Lambda and Big Query [softwareengineeringdaily.com](https://softwareengineeringdaily.com/2020/12/30/cloud-native-applications-with-cornelia-davis-repeat/?utm_source=rss&utm_medium=rss&utm_campaign=cloud-native-applications-with-cornelia-davis-repeat)

### Benefits

There are several drivers of this move to Cloud Native applications.

A big one is cost. These hosting providers are running their operations at such scale that they can offer very competitive pricing. For example in 2019 Amazon AWS data centres covered [14 million square feet](https://www.geekwire.com/2019/big-amazons-global-real-estate-footprint-new-filing-reveals-tech-giants-astounding-presence/). They have continued to invest in both hardware and specialist virtualisation software lowering costs and increasing utilisation, and those cost savings have been passed in to customers.

Related to cost is the move to usage based billing. Whereas with VPS hosting you had to at least  pay for an entire server running 24/7, with cloud computing you can pay for exactly what you use. Each service is billed in slightly different ways depending on where the cost is associated. You can for example pay for exactly the storage in GBytes you are using, exactly the volume of inbound and outbound data in Gbits you are transferring, and exactly the number of requests you are making to a service. The services pricing are usually divided up into tiers, and often include a free tier for low volume usage.

It’s a model that has grown very popular with developers as it can accommodate for large variability in load. Whereas in the past it would have been necessary to manage a lot of infrastructure, all that complexity is handled by the hosting provider. And their infrastructure is the best in town, since they’ve been developing it for many years. It’s as if you had your own highly available, infinitely scalable, robust and flexible infrastructure. It’s possible to build Cloud Native applications very rapidly. You are quite literally building on the shoulders of giants in the industry.

Amazon is investing heavily this vision of the future of computing, recently announcing it plans [to train 29 million people for free on cloud computing](https://eminetra.com/amazon-wants-to-train-29-million-people-to-work-in-the-cloud/240296) over the next few years. 

### Challenges

With all this progress it’s important to step back every once and a while to assess the situation. How resilient and robust is Cloud Native really? Let’s look at some areas that should be considered.

Well from a technology perspective it is undoubtably very resilient and robust. Most of these platforms are at the stage where a lot of the technologies have been operational for many years, supporting customers from a wide range of industries. They have been fine tuned and battle tested, and as a result are some of the best technology stacks available.

One technology area that I feel still needs improvement is the developer experience. Since all the services that you are using are cloud based, it becomes a bit of a challenge setting up local developer environments. There are tools and libraries available to create local versions of the services that you are using. For example Amazon has the [Serverless Application Model](https://aws.amazon.com/serverless/sam/) and the [aws-sam-cli](https://github.com/aws/aws-sam-cli), similar developer tools exist for other providers, but there isn’t a whole lot of standardisation, so this area can be a bit confusing. I expect the tooling to improve over time.

Some libraries and frameworks I’ve found useful for serverless development:

[serverless-http](https://github.com/dougmoscrop/serverless-http) - Wraps your entire server framework so you can use it in a lambda function, supports a load of server frameworks including express, koa, hapi, fastify and restify. Useful for creating apps that can run locally and in a serverless function.

[netlify-cli](https://github.com/netlify/cli) - CLI tool for interacting with the Netlify API, great for deploying to Netlify when you aren't building your site on their infrastructure.

[netlify-lambda](https://github.com/netlify/netlify-lambda) - CLI tool for building and running your Netlify functions locally.

[serverless framework](https://github.com/serverless/serverless) - A CLI and web tool to build and deploy serverless architectures, includes supports for Amazon, Azure, Google among others. Makes it easy to configure and provision all the components of your Cloud Native application.

Another area to consider is long term costs. So far we have seen costs mostly getting cheaper, but that might not always be the case, it’s still relatively early days for the cloud industry as a whole. One example where costs suddenly went the other way is Google Maps. Back in 2018 [they raised prices by ~1,400% overnight](https://www.geoawesomeness.com/developers-up-in-arms-over-google-maps-api-insane-price-hike/). Application developers were not happy, but it still happened. Price hikes have happened in the past and will likely happen again somewhere in the future.

Also it’s worth noting that the pricing structure can have a direct effect on your business that isn’t always obvious. Engineers might start to carry out their duties in a different, non-expected, non-optimal way in order to avoid hitting different pricing tiers. These effects can be difficult to uncover.

From my linkblog [13/12/2020](https://links.markjgsmith.com/archives/html/2020/12/#13December2020):

> The author explores the landscape of buy vs build in detail, lots of food for thought, the arguments for building are generally much stronger when it’s a solution that solves something that is core to the business - I’m linking to the HN thread because there are some interesting comments about how vendor pricing models can effect growth in ways that aren’t immediately obvious [ycombinator.com](https://news.ycombinator.com/item?id=25399250).

As is always the case with the tech industry, there will be mergers and acquisitions, that is a certainty. When that happens there are large shifts in power dynamics throughout the industry. The next 10 years are going to see some big changes throughout the stack with activity already happening right at the hardware level with a move from x86 to ARM chip architectures, most notably with the recent announcement of Apple’s M1 chips.

From my linkblog [21/12/2020](https://links.markjgsmith.com/archives/html/2020/12/#21December2020):

> Apple M1 foreshadows Rise of RISC-V - Another piece about the future of chip architectures, it appears like a general move towards ARM cpus surrounded by specialised corprocessors running RISC-V with special extensions to the base instruction set, also discusses the possibility of using RISC-V for the cpu [medium.com](https://erik-engheim.medium.com/apple-m1-foreshadows-risc-v-dd63a62b2562)

That’s a massive change, and it’s not just for consumer hardware either. There are plans to have M1 chips running in data centres to take advantage of their much lower power to watt ratio, and their new architecture that is very well suited to AI compute tasks. Shifts such as [Nvidia attempting to buy Arm](https://www.ft.com/content/223b9b1c-5c99-4c39-bb80-54111f55e30e) are going to continue and their effect will be felt throughout the industry.

From my linkblog [02/12/2920](https://links.markjgsmith.com/archives/html/2020/12#2December2020):

> Amazon unveils 5 new EC2 instance types, the most interesting being the Amazon-made Graviton2 powered instances for compute heavy applications which uses the ARM chip architecture, can deliver a whopping 100 Gbps network speeds at 40% price performance over existing Intel x86 chip architectures - Lots of movement in the chip architecture space at the minute [zdnet.com](https://www.zdnet.com/article/aws-unveils-new-compute-instances-including-compute-heavy-c6gn-powered-by-graviton2).

Also worth considering: The forces of government have been stirred in recent years, with the introduction of new rules and regulations for technology companies, especially in the EU with legislation for [GDPR](https://en.m.wikipedia.org/wiki/General_Data_Protection_Regulation), [EU’s Article 11 & Article 13](https://www.theverge.com/2018/9/13/17854158/eu-copyright-directive-article-13-11-internet-censorship-google), and [Section 230](https://en.m.wikipedia.org/wiki/Section_230) to name but a few. Similar legislation is being drafted in countries all around the world. How these will play out is unknown at this time, but as some of these regulations get passed, there will be pressure on hosting providers to enforce new rules, and that could affect some hosting provider customers.

Cloud Native architectures are technologically robust, and will enable you to get up and running quickly, but there are aspects of the bigger picture that are worth being aware of. It will be crucial to be ready to pivot if necessary, know where your cost centres are, and perhaps consider building some infrastructure that would enable a move in a worst case scenario event.

## Alternatives

### Infrastructure

One of the biggest developments in the recent past when it comes to infrastructure is [Kubernetes](https://en.m.wikipedia.org/wiki/Kubernetes). It was originally written by Google for managing its data centres, and is now open source and maintained by the [Cloud Native Computing Foundation](https://www.cncf.io). It is a platform for automating deployment, scaling, and operations of application containers across clusters of hosts. 

Containers can be thought of as slimmed down versions of VPS hosts that instead of containing an entire operating system, only contain exactly the operating system pieces that your application requires. With Kubernetes it’s easy to create and configure the resources your application depends on, deploy the latest application code, and ensure that your application is distributed in such as way that it is always available. It automatically does a lot of the heavy lifting that is necessary when you are running on standard VPS hosting.

Relevant: [Software Engineering Podcast - Kubernetes vs. Serverless with Matt Ward (Repeat)](https://softwareengineeringdaily.com/2020/12/29/kubernetes-vs-serverless-with-matt-ward-repeat/?utm_source=rss&utm_medium=rss&utm_campaign=kubernetes-vs-serverless-with-matt-ward-repeat)

An interesting aspect is that since Kubernetes is open source and platform agnostic, we are starting to see offerings from all the major services providers. What this means is that if you do need to move between providers it’s a lot easier since the application will run on any Kubernetes cluster, regardless of provider.

As well as the ability to move, we are starting to see companies investing into building multi-cloud infrastructure. Software such as [Cloud Manager](https://thenewstack.io/cloud-manager-a-new-multicloud-paas-platform-built-on-kubernetes), makes it possible for your application to run seamlessly across hosting providers. There will likely be a lot of development in this area as more and more companies seek to build out resilient and robust infrastructure.

### Software Architectures

Whether you have opted for a classic VPS style infrastructure or the more modern Kubernetes based infrastructure, the question of how best to architect your application will come up. In the early days it’s often best to keep things simple, have minimal layers, use just enough code to get the task complete. You will be learning about the intricacies of your problem domain and having too much code can get in the way.

Once you start integrating a few cloud services though, and especially if you want the ability to easily switch providers you will want to architect your application in such a way that makes it easier to do that.

A popular way to do just that is to use [Domain Driven Design](https://en.m.wikipedia.org/wiki/Domain-driven_design) techniques, an example of this is  [Microservices Clean Architecture Patterns](https://m.youtube.com/watch?v=CnailTcJV_U&t=960s). This approach uses entities, controllers, adapters and frameworks/devices layers, resulting in an architecture where changing the elements in the outer layers is much easier because you mostly just need to create new adapters, while much of the core business logic will remain unchanged.

{:refdef: style="margin-top:14px; margin-bottom:14px;"}
![Node.js web development technologies]({{site.baseurl}}/assets/images/clean-architecture-pattern.JPG)
{: refdef}

I have had good results using some of these techniques in my [Serverless Books API](https://github.com/mjgs/serverless-books-api) application. In my case the layers are named slightly differently, with handlers, utilities and adapter layers, but the idea is the same. Each layer encapsulates some bits of information so that the core handler functions don’t need to know exactly how the storage has been implemented. 

The core layer handler functions use the addBook, getBook, getAllBooks, updateBook and deleteBook utility functions, passing in the query data, but don’t know any details about how and where the data is stored. 

The utility functions, which are the next level out, know only the name of a table passed in via an environment variable. They use the create, get, getAll, delete and update db adapter functions passing in the query data and the table name.

The db adapter functions connect to the backend cloud database to perform the operation, do any necessary post processing to the data and return it through the layers back to the core, which eventually sends the data back to the end user. 

Since the db adapter is generic it can be used by any utility function to read and write data to any database table, as long as the utility function passes in the table name.

Changing to a service hosted by another provider is then just a question of implementing a new adapter, the business logic in the core should remain unchanged, and only the storage identifier (i.e. the table name) might have to be updated to work with the new adapter.

Thinking about it logically, the most resilient way to develop applications in this way would be to always start by implementing a version of the service yourself, even if it’s paired down in functionality and scale, and only when you have a basic version running, write an adapter for the hosting provider’s version of the service. That way in the worst case you always have something to fall back on, though there would be some degradation to the performance.

Everyone’s situation is different though, and your circumstances  might be such that you don’t have time to go through ultra-cautious route, in which case build out cloud integrations first, and at a later date back track and build your own fallback version of the service. There might even be cases where that approach is quicker overall because you will likely learn a lot about how to build yours by using that of the cloud provider.

## Wrapping Up

Although it’s early days for cloud computing, even large companies such as the British Broadcasting Company (BBC) in the UK are building huge cloud native infrastructures. It’s interesting to read their high level goals and see how cloud technologies align very well with their mission. 

From my linkblog [03/01/2021](https://links.markjgsmith.com/archives/html/2021/01/#3January2021):

> Moving BBC Online to the cloud - The engineering team writeup of their recent move from on-premises infrastructure to mostly cloud based where they are using serverless technologies extensively - Very clear articulation of the project high level goals, a description of the layered approach that enables code re-use but also keeps the flexibility to create custom specialised solutions, the re-organisation into teams focussed on page types and common concerns such as development methodology and hosting, interspersed with lots of development principles and guidelines - I have worked on several big projects at the BBC, it’s a staggeringly large organisation, so I am aware of how massive an undertaking this re-architecting of their infrastructure must have been, kudos to all the teams that made it happen [medium.com](https://medium.com/bbc-design-engineering/moving-bbc-online-to-the-cloud-afdfb7c072ff)

However remember they are a very big company, so they will have high leverage with their hosting providers and it’s likely that they will have service level agreements giving them preferred access to the hosting provider’s support staff. And of course they might very well be busy building their own fallback services too. Just because large companies go full cloud doesn’t necessarily mean that it’s the right choice for every business, the trade-offs and peculiarities to consider in the decision making process are going to be different in each situation.

Cloud Native is a tremendous leap forward for building applications. You will be able to rapidly build out applications that are performant, robust and that can scale to handle any load. Keep in mind the risks, think about resiliency, try to have contingency plans for events that can affect your business.

The road to building successful web applications is long and windy, and many things can happen over the life of an organisation. You have to make compromises, strategic decisions and there will likely be times when you have to take some risks, but with some thought and planning it’s possible to make that risk more manageable.
