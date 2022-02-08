---
title: "Component and configuration based UIs"
description: How I modified my static site generator to start rendering component based websites
published: true
layout: post
date: 2022-02-09 09:00:00:00 +0700
tags:
- blogging
- web development
- linkblogging
- programming
- javascript
---
The past few days, following on from my investigations into the rendering process of modern javascript frameworks, I’ve had component and configuration based UIs on my mind. I’ve been wondering what the big deal is, why all the fuss, when it seems to just [boil down to co-locating your templates and code together]({{ site.baseurl }}/2022/02/08/whats-up-with-templating-in-modern-javascript-frameworks.html).

I kept thinking there must be more to it. But then I thought, what if that really is all there is to it, there are probably other reasons, but what if it is just about co-locating the templates and the code, would that be so bad?

One major annoyance with templating is making sure all the functions you are using in your templates are in the render context at render time. If any of them aren’t there, the rendering is going to bomb because the template library will do exactly as you have written in your template logic, except some of the functions you told the library to call just aren’t there, and when your template reaches one of those, it results in a runtime error. If you don’t use many functions in your templates, this is likely a non-issue. On the other hand if you do, then it is a pain you face.

The way it’s done with regular template rendering, is that you have to look down your entire template hierarchy, note down which functions get used, and pass these into the top level template, as part of the data object, and you have to make sure that each time you include a template/partial, to pass the right functions into the render method invocation for that template/partial. So again, if you don’t use many nested templates, it’s probably a non-issue. But if you do, then welcome to code bombsville.

For people that write highly nested, highly functioned templates, collocating code would perhaps be beneficial, just to make preparation of render contexts less error prone.

With all that in mind, I decided to just try adding component rendering to my ssg in a feature branch. Worst case is that it doesn’t work and I could just delete the feature branch.

I thought about it for a few hours, looking at my code, looking at javascript’s implementation of classes, which bundle functions, over and over again. It's still very new code, so I wasn’t totally sure about it, but I think I could see a way to modify the ssg that would result in component rendering.

It was simple enough, just add a renderComponent method to the renderer, and that method would grab all the functions from the passed component, merge them into the data object, and pass that into the regular render method. Could it be that simple?

In the javascript community such implementations are often referred to as syntactic sugar. Might be the same in other language communities, I don’t know. Essentially the underlying process remains the same, but a new structure is available which is useful in many situations. Examples of this approach are Classes, syntactic sugar on top of prototype based inheritance, and Async/Await which still uses traditional callbacks underneath, but via promises.

It’s pretty clear to me that if you can write your template alongside the functions it uses, and be sure that at render time, all the functions will be available, then that’s a net positive. And it might very well be that there are other, more frontend centric reasons to use components.

Anyway, guess what, it worked!

It seems sort of obvious now, but sometimes when you are in the fog of technology, mental models, implementations, buzzwords, build tools, peoples opinions, and just the complexities, mutilations, humiliations, thirsts, hungers, dirtyness and madness of life, it totally doesn’t seem obvious!

In the end I added about 10 lines of code, and a very simple Component class, and it worked, the component I included in my template rendered! And since my ssg has a way to define custom renderers, most libraries that support partials/includes should now be able to render components. It's early days and I havent done much testing, but it seems as though it is possible.

It was quite a moment, when I ran the code, I sort of knew it would work, but it was still a pretty big wow moment. I was like, "wow it worked". That doesn’t happen very often in programming, at least not at that scale.

Regular template rendering still works as before, and for templates that don’t use lots of functions, that’s probably going to be the better, simpler way to go. But if you do write templates that use lots of functions, using components is a neat way to bundle them with your template, so that at render time the functions are right there in the context, no need to do any special preparation.

The only current limitation is that your top level can’t be a component, it has to be a template. The ssg renders components inside templates. There might be a way to have top level components in the future, I haven’t figured out an easy way to do that yet.