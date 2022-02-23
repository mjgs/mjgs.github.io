---
title: "Next generation tools and workflows for the creator economy"
description: Reviewing an interesting Smashing Magazine article all about markdown and the future of content writing, editing and automation
published: true
layout: post
date: 2022-02-23 10:45:00:00 +0700
tags:
- blogging
- writing
- web development
- programming
- javascript
---
There was an Interesting Smashing Magazine piece earlier in the week, [Thoughts On Markdown](https://www.smashingmagazine.com/2022/02/thoughts-on-markdown). It does a really good review of the transformative effect Markdown has had in tech, especially by developers, but also by creators. 

Markdown unlocked a whole ecosystem of workflows, that have been generally centered around git version control platforms such as Github. Reason being that they now all offer CI/CD tools, i.e ways to run shell programs that can do things to and with the files in your repository when you do different actions like push/commit/merge files.

I wrote about this trend a little over a year ago in my piece about [Github Actions for custom content workflows](). I later wrote about [Mozilla MDN Docs are going full Jamstack](), which was a high profile example of the trend. I was seeing in my own work how the combination of automation, git version control and a simple authoring format were transformative in what I was able to do. I think the fact that Mozilla went all in on such a workflow is a big sign of things to come.

Along with the praise about the impact, the Smashing piece’s thesis is that although good things have come about because of markdown, that it isn’t well suited for editors, writers and creators. They go into [a lot of depth in their article](https://www.smashingmagazine.com/2022/02/thoughts-on-markdown), it’s really worth the read.

I’m sympathetic to their point of view because although it’s fantastic for quickly writing documentation for coding projects, I have found it a bit tedious for writing, but especially editing essay style pieces. 

I love how easy it is in Markdown to add URLs, lists, for boldening/italicising text, and for adding titles and sub headings. Guess what you can also just add HTML directly in the file for those situations where the syntax falls short. All that is great, and it doesn’t bother me that you end up with some slightly ugly syntax scattered through the text. I’m fine with that, in fact for URLs you get used to it very quickly, and it’s actually, in my opinion, argusbly better to be able to see the full URL text, so you can easily spot mistakes before publishing, and it encourages you to favour well written URLs. It’s often overlooked because it’s somewhat subtle, but structured and nicely formatted URLs make browsing and sharing on the web a much nicer experience.

The biggest annoyance for me is in the editing, because the way corrections are displayed in a Github PR are sort of close to unreadable. Each paragraph is one line in a markdown file, and if you change 1 word, the entire paragraph is highlighted in a way that you lose the flow of the whole document. I’m constantly having to preview, commit, review. It’s that feeling where you can’t see the woods for the trees, and it makes writing prose much more difficult than it should be.

The topic came up in a [recent Shop Talk Show](). Dave is keen on exploring Markdown editors and Chris is bullish on block editors from his mostly very positive experience with Wordpress’s newish Gutenberg editor. He’s always going on about it, so there must be something to it.

And that’s were the Smashing piece ends up, talking about the concept of block editors, which I am totally unfamiliar with. It sounds interesting, though I wonder how much of the automation and collaboration features of a Github+Markdown workflow you would lose by moving to block editors. Also, and this is a big one: portability. I personally am willing to put up with some of the annoyances of Markdown because, I know it works everywhere that supports git repos. Where is the portability in block editors?

There are signs that some of the benefits of modern webdev blocks and components are making their way into Markdown, with for example (Mdx)[https://mdxjs.com], which is a markdown variant that makes it possible to embed React and Vue components directly in your markdown files. So maybe we will get both markdown and block editing in the new embedable web that the folks at Smashing envision.

It’s a topic that I’m watching closely because it will have a big effect on what I like doing: [building websites and workflows]().

I’ll finish with a Markdown Pro/Cons list as I currently see it:

Markdown Pros:

- Portability
- Collaboration
- Git friendly
- Compatibility
- Huge ecosystem of tools
- Being able to stick it in a PR, then stick it into a workflow

Markdown Cons:

- Not the best writing experience
- Lousy editing experience 