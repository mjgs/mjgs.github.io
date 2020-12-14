---
title: Robust NodeJS Deployment Architecture
published: true
layout: post
date: 2020-11-13 19:17:00:00 +0700
tags:
- nodejs
- architecture
- infrastructure
- cloud
---
The aim of this post is to succinctly describe an effective and robust architecture for self hosting your NodeJS web applications. I’m going to stay relatively high level, describing the technologies, and components, by the end of it you will have a good idea of what such a system looks like. There is a focus on standard well tested pieces rather than the latest shiny cloud / containerisation offerings. It is well suited for running small to medium size applications.

{:refdef: style="text-align:center;margin-top:50px;"}
![Node.js web development technologies]({{site.baseurl}}/assets/images/nodejs-web-development-technologies.png)
{: refdef}

## Features of the architecture

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Runs on standard VPS hosts 
- Possibility to scale
- Secure
- Easy to maintain
- Fault tolerant
- Low cost
- Backed up and easy to restore
- Easy machine provisioning
- Easy to deploy code
- Support multiple databases
{: refdef}

## 3 main components

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Load balancer
- Web and API application servers
- Datastore
{: refdef}

During it’s life cycle, a client web request travels over the internet and eventually arrives at the load balancer where any SSL/TLS connections are terminated, then re-encrypted using self-signed certs and sent to an available application server. That application server performs the tasks it needs to do, persisting information on a shared datastore. Responses are sent directly from the application servers to the client.

The SSL/TLS termination happens on the load balancer because it makes managing the certificates much easier, with only a single place to renew, create, update and backup certificates.

Having a load balancer ensures that you can have several application servers running in parallel, which means you can scale by just adding more application servers, but it also means you can reboot servers without impacting site uptime.

As for the application servers, you can separate out web servers from API servers, but for ease of maintenance you can also just run both on the same machine on different ports, with a reverse proxy on the machine directing the requests to the right application. In this way you have one discrete unit which makes it much easier to add capacity. In the vaste majority of cases this setup is good enough, though could be optimised later.

Having a shared datastore is key to being able to run the application servers in parallel. This is a single machine that has a large storage volume mounted. It runs all the databases which write their data to the storage volume. The datastore can also run on a clustered set of machines for high availability, though this adds quite a lot of complexity, so initially it’s probably best to run one machine with good backups, so if anything goes wrong you can be restored and running with a minimum of downtime.

## Technologies

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- [Nginx](https://www.nginx.com) - Load balancer and reverse proxy
- [Redis](https://redis.io) - Key/value very fast database often used for storing sessions and caching
- [Mongodb](https://www.mongodb.com) - NoSQL database
- [Postgres](https://www.postgresql.org) - SQL database
- [Letsencrypt](https://letsencrypt.org/getting-started/ ) certbot - for generating and maintaining certificates
- [Linux Ubuntu](https://ubuntu.com) - Operating system for all 3 components
- [Pm2](https://pm2.keymetrics.io) - NodeJS process manager, runs the applications, handles logging and a variety of other runtime activities
- [RabbitMQ](https://www.rabbitmq.com) - Message queue software very important for fault tolerant backend systems
- [Mongodb-queue](https://github.com/chilts/mongodb-queue) - Message queue implemented via a NodeJS library backed by MongoDB
{: refdef}

## Provisioning infrastructure

You can keep things quite simple in this regard, using a [Bash](https://en.m.wikipedia.org/wiki/Bash_(Unix_shell)) script for each of the 3 main components. The script would need to do the following:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Install latest OS updates
- Install necessary software
- Configure users and groups
- Write/update software configuration files
- Start and stop various services
{: refdef}

These are some of the important Linux items you would need to know about:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- [sshd](https://en.m.wikipedia.org/wiki/OpenSSH) - server for ssh connections
- [stunnel](https://www.stunnel.org) - creates secure connections, used on datastore for applications without built in SSL - e.g. Redis
- [ufw](https://en.m.wikipedia.org/wiki/Uncomplicated_Firewall) / [iptables](https://en.m.wikipedia.org/wiki/Iptables) - firewalls
- [PKI](https://smallstep.com/blog/everything-pki.html) and creating self-signed certificates
- [logrotate](https://www.tecmint.com/install-logrotate-to-manage-log-rotation-in-linux/) - manage rotating and backing up application log files
- [cron](https://en.m.wikipedia.org/wiki/Cron) - schedule the running of maintenance scripts like backups
- [certbot](https://certbot.eff.org/docs/) - generate and renew certs
- [rsync](https://en.m.wikipedia.org/wiki/Rsync) - securely synchronize files between machines
{: refdef}

It’s likely that your [VPS](https://en.m.wikipedia.org/wiki/Virtual_private_server) hosting provider has an API and / or command line tools, making it possible to create a provisioning script that creates a VPS server, rsyncs the bash install script to the machine and runs it. So with a minimum of fuss you can provision fresh servers by running a script, so it’s completely repeatable.

It’s worth noting that there are modern tools that use containerisation like [Kubernetes](https://en.m.wikipedia.org/wiki/Kubernetes), which are very powerful but can get quite complex.

## Deploying code

This is another place where a simple bash script can be very effective. 

It would need to do the following:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Build your application to a deploy directory
- Backup currently running app
- Rsync the files to the application servers
- Restart the application server
{: refdef}

There is a lot of variety in this area. Many modern workflows that use [CI/CD systems](https://en.m.wikipedia.org/wiki/CI/CD) use git to clone your entire application 
repository to the server, rather than rsyncing just the built files. Requirements vary a lot from project to project.

The bash script route is great for simplicity, but there are often more manual steps involved, especially if your application has complex configuration. In the early days of a project it’s often good enough.

## Backups

Backups are super important. You need to have all the important files backed up and ideally scripts to restore the backups in the event that a component fails and needs to be restored.

Consider backing up:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Each deployed application version, along with configuration
- Log files for databases, firewalls
- Certificates
- Contents of all databases
- Configurations for every 3rd party application you are using
{: refdef}

It’s a good idea to use storage from big cloud providers, they are low cost and have good scripting tools.

## Security

It’s important to configure your machines securely, set firewalls (local and cloud) appropriately. Always use TLS/SSL for inter machine communication. Follow the security advice from the various pieces of software you install, for example creating different users for specific purposes e.g. application access vs access for backups. Only give the minimum of access rights necessary to perform a given task.

## Staging and production environments

Once the application is running in production, you will benefit a lot from having a staging environment. It’s a replica of the production environment where you can try out new code without being worried to break the live system. Never deploy directly to production, always test it out in staging first.

## Wrapping up

The infrastructure side of running applications can get quite complex, but there are a lot of advantages to knowing how to construct these setups yourself:

{:refdef: style="list-style-type:disc; margin-bottom: 14px;"}
- Keep costs at a minimum
- Be in full control of the infrastructure
- Be able to deploy anywhere
{: refdef}

It’s also worth experimenting with integrating [serverless](https://serverless.css-tricks.com/about/ ) technologies for aspects that are very high load, the low cost and high performance might be worth the portability trade-off, but be aware that a move might require rewriting parts of your application should you need to change providers.

*This post is part the [choosing your web development stack]({{ site.baseurl}}/2020/12/13/choosing-your-web-development-stack.html) series.*
