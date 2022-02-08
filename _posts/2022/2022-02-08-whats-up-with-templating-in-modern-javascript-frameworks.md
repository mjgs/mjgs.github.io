---
title: "What’s up with templating in modern javascript frameworks?"
description: Revelations from a mostly backend developer about the rendering process of modern javascript frameworks
published: true
layout: post
date: 2022-02-08 13:30:00:00 +0700
tags:
- blogging
- web development
- linkblogging
- programming
- javascript
---
I’ve been [writing a static site generator recently]({{ site.baseurl }}/2022/01/01/static-site-generator-developnent-continues.html). It’s a rewrite of a utility that I use to build my [statically generated linkblog](https://links.markjgsmith.com). That utility has been working well, but it’s implementation isn’t exactly very elegant. It was, after all, my first attempt at building the linkblog statically, which had previously been a typical MongoDB backed Express app.

I’ve been really delighted using many of the latest javascript features. Specifically [Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes), [Array functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods) (especially map and reduce) and [Async/Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function). That combination IMO has dramatically improved the development experience. The code is massively easier to reason about, and just looks so much better.

```
class Dispatcher {
  constructor(app, cfg, renderers, collections, srcDir, outputDir) {
    this.app = app;
    this.cfg = cfg;
    this.renderers = renderers;
    this.collections = collections;
    this.srcDir = srcDir;
    this.outputDir = outputDir;
    
    this.renderersByName = undefined;
    this.renderersByExt = undefined;
    this.outputPaths = [];
  }
  
  async init(templatePaths) {
    debug(`Initialising dispatcher with templatePaths: [${templatePaths}]`);

    // Arrange things for easy selection
    this.renderersByName = this.getRenderersByName();
    this.renderersByExt = this.getRenderersByExt();
    
    for (var i = 0; i < templatePaths.length; i++) {
    // ... do some rendering ...
    }
  }
  
  getRenderersByName() {
    const renderersByNameReducer = function(acc, current) {
      acc[current.name] = current;
      return acc;
    }

    return this.renderers.reduce(renderersByNameReducer, {});
  }
  ...
}
```

The latest ssg tool now has all the basic features I need to rebuild my linkblog. It uses what I call "old school templates" to render all the pages. In my case it’s [EJS](https://github.com/mde/ejs), but it could work equally well using any of the many other template libraries like [handlebars](https://handlebarsjs.com), [liquid](https://liquidjs.com), [mustache](https://mustache.github.io) etc. I wanted to get that working before venturing into rendering pages using some of the more "modern" component based javascript frameworks like [React](https://reactjs.org), [View](https://vuejs.org) and [Svelte](https://svelte.dev).

This past week, I’ve been looking at these frameworks more closely, trying to figure out how the rendering works. I’m trying to get a sense of what modifications I’ll need to make to my ssg so that it can generate component based websites. I’ve read so much about these frameworks over the years, it all sounds so wonderful, but also quite mysterious.

With old school templating rendered server-side, though there are lots of peripheral features, it essentially boils down to passing a template string together with an object containing data to the templating library. The library takes the data and the template string and gives you back an HTML string, a.k.a the rendered page. You write that to a file. Rinse and repeat, upload all the files to your CDN / hosting provider, and that’s your site live.

```
  debug('Renderer fn - ejs: rendering template');
  
  const renderedContent = ejs.render(
    templateBody,
    context,
    options
  );
    
  return renderedContent;
```

The template libraries have lots of neat features to make it easier to create your pages. One such feature is the ability to include templates inside templates. You create templates for small pieces that you can reuse across all your pages. On my Jekyll based blog for example, I have among others, includes for the Google analytics snippet, as well as messages [promoting my development services]({{ site.baseurl }}/2022/01/01/hi-its-me-im-still-alive.html) that appear on each page. I can update the included templates and the messages update across all the pages that use those templates. The feature is sometimes called partials, it’s been a standard feature of ssg’s for many years. Each library has a syntax for describing the include that you insert directly into the template HTML, and you often additionally pass the include a data object which is used by the library to render the included template. 

```
<h1>Hello World!</h1>

<h2>Some included content:</h2>

<%- render(includes.helloIncludes, locals) %>

<h2>Some regular content:</h2>

<p><%= locals.loremipsum.content1 %></p>
```

It’s worth noting that in most implementations you can pass functions in the data object, and use those functions directly in your templates. The libraries execute these functions as part of the rendering of the page.

The templates contain the logic for creating the HTML files, your javascript code which you use to fetch and prepare template data is in separate files. What about the modern frameworks, what are they doing?

Well there’s a lot of buzzwords and fancy sounding terminology, but after reviewing several component based projects, it seems to me they are doing essentially the same thing, except the template code has been moved into the javascript files inside a return statement, components are essentially the same thing as includes, and even props, which is one of the key concepts are really just the same as the data object that you pass to includes. All this mystery, and really it’s just another template library. I’m probably missing some crucial detail, but after a few days of digging, that’s what I’m seeing. 

```
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```

There must be something else that’s useful over and above collocating related code together. At the present moment I personally find that sloping everything together causes me more confusion, because it’s difficult to conceptualise where the boundaries of the app are located. It’s just this vast amorphous everything code, instead of code that’s divided into rendering logic and data preparation logic.

I’m aware that I’m coming at this from a very server-side way of thinking about things, and probably component based websites make a lot more sense once they are running in a browser environment, with event handlers and the like, but nonetheless, I find these observations interesting, even if no one else does.

What’s the major advantage that you get from sticking the template into the javascript?