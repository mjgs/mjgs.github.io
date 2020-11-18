---
title: 'New Linkblog feature: rss, atom and json feeds'
published: true
layout: post
date: '2020-01-17 15:21:00 +0000'
tags:
- linkblog
- feature
- protocols
---

The latest linkblog feature is feeds. These are a versions of your linkblog that are easily readable by a computer. This makes it easier for people to read your linkblog but also enables you to do neat things like auto post your links to social media such as Twitter and Facebook. Each time a day finishes where you posted links, the hash link of that day gets added to your feed.

{:refdef: style="text-align: center;"}
![Linkblog rss, atom and json feeds]({{site.baseurl}}/assets/images/linkblog-rss-atom-and-json-feeds.png)
{: refdef}

To access your feed, right click on the icon in the toolbar (it looks a bit like the Wifi symbol rotated by 45 degrees) and select copy link address. This should copy the url of your feed to your computer's clipboard. 

If you then paste it into some form of text editor you will see what the feed url looks like. Here are my feeds for my regular linkblog and for my custom domain linkblog:

```
https://linkblog.io/users/mark/feeds/daily/rss
https://links.markjgsmith.com/feeds/daily/rss
```

The advantge of using your custom domain url is that theorectically if you ever needed to move your linkblog to another provider, then as long as you still own the custom domain, that could be done without the people already using your feed having to update to a new url.

If you try to load these pages in a browser you'll see lots of strange looking text with HTML tags, but you will also notice that your daily posts are within \<item\> elements. Computers can read these feeds easily. The vaste majority of the time though you never need to read the actual feed, you only really have to copy and paste the urls of the feed.

The most common type of feed is RSS so that's what is used in your navbar. Atom and JSON versions of the feed are also available by replacing 'rss' in the url with 'atom' or 'json'.

A very typical thing people do with feeds is add them to their feed reader, which makes it possible to read many sites from 1 place rather than have to remember to visit all the sites individually. Seen like this, feeds are very similar to the follow feature in many social media sites, they have the advantage of working across many different sites, though they are a bit more complicated.

Feeds also make it possible to do things automatically with your posts, like posting them to sites like Twitter or Facebook. For example I have setup my linkblog so days are posted to my Twitter account [@markjgsmith](https://twitter.com/markjgsmith). There are lots of 3rd party online sites that offer rss-to-[insert favorite social media site] type services.

For a more detailed description about feeds check out the [You Need Feeds](https://www.youneedfeeds.com) site. Also useful is this [list of rss feeds for social media sites](https://www.labnol.org/internet/rss-feeds-directory/21242/) which might give you some ideas about what is possible.

If you want to try out running a linkblog then signup for the 14 day [free trial](https://linkblog.io/signup), after the trial it's just a few dollars per year.
