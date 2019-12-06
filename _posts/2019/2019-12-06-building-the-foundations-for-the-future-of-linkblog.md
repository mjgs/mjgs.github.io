---
title: Building the foundations for the future of linkblog
published: true
layout: post
date: '2019-12-06 11:50:00 +0700'
tags:
- linkblog
- development
---

Earlier in the year I did a [pretty big redesign]({{site.baseurl}}/2019/12/04/linkblog-new-look.html) of the site which lead to upgrading the style framework which ended up being rather a lot of work, but the site looks great now and still minimalist. The redesign resulted in me building and introducing 3 new core components:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Redesigned billing system  - Compliance with EU Regulation
- Scheduler - Periodically runs jobs completely separate from handling website requests
- Queues - Mechanism to co-ordinate scheduled jobs in a fault tolerant way
{: refdef}

This post gives a bit of description around these components, because although they are not directly visible in the linkblog UI, you might find it interesting to know some of the details of how the site operates under the hood, and maybe give you a bit of an idea of the possible directions for the future.

If you’ve been following the news you might have noticed that there has been a wave of introductions of new internet regulations all around the world. In the EU they have introduced [Strong Customer Authentication (SCA)](https://en.wikipedia.org/wiki/Strong_customer_authentication) which affects linkblog because the servers on which the site runs are hosted in the UK. The new rules meant a complete redesign of the billing system and with only 60 days notice. The previous integration with the payment processor [Stripe](https://stripe.com) was using their Checkout product, which was simple to setup but doesn't meet the new EU regulations. The re-architected integration is more complex and uses a combination of Stripe Elements  for the UI and the new Stripe Intents API which complies with the latest EU regulations.

The billing system is now active and whereas previously it could only handle 1 type of subscription, it’s now ready to handle multiple subscription types, the first addition to the Linkblog Basic subscription is likely going to be SSL for Custom Domains, the plan is to slowly add new services to compliment the basic functionality.

As part of the billing system redesign, it became apparent that I needed a way to receive status updates from Stripe called [webhooks](https://en.wikipedia.org/wiki/Webhook). Handling the webhooks is non-trivial because an acknowledgment has to be returned immediately, the same webhooks sometimes get sent multiple times, the order isn't always guarantied, the task necessary to process the webhook differs depending on the type of webhook received and processing tasks take varying lengths of time to complete.

The strategy I settled on was to record the incoming webhooks in the database, respond to Stripe, and have a scheduler component  run jobs to periodically process the recorded webhooks. I had to restructure the app quite a bit to be able to handle regular website requests and also separately run scheduled jobs. This is a good strategy but problems occurred because when a cluster node was rebooted, there was the possibility of jobs failing midway through and not completing.

To make the setup fault tolerant I had to build a queuing system to help orchestrate the scheduled jobs. The queues are hosted on a separate machine to the website cluster nodes, and the scheduled jobs which periodically run on these read and write messages to the queues during execution. Queues are useful because if a website node goes down midway through a job, another node can automatically pick up the job and finish the processing when it sees the item in the queue didn’t complete within a certain timeout period.

So a webhook arrives, is recorded in the database, and scheduled jobs run and add messages to the appropriate processing queue. These queues are monitored by more specific scheduled jobs running on the nodes which take new items off the queues and carry out the appropriate processing tasks, for example sending out email notifications.

The cool thing about queues is that they can be used for lots of tasks that don't need to be part of handling website requests. I’m hoping to migrate a bunch of tasks like data exports and generating custom domain certificates to use the queuing system in the near future. Being able to off-load tasks to the queues will keep the site performing well.

The new billing system, the scheduler and queues are 3 core components that are fundamental going forward.

*For project development enquiries feel free to [contact me via email]({{site.baseurl}}/about).*
