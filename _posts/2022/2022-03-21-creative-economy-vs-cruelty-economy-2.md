---
title: "Typescript makes function declarations difficult to read"
description: "How I currently feel about some of Typescript's festures"
published: true
layout: post
date: 2022-03-21 19:31:00:00 +0700
tags:
- programming
- javascript
---
I’m not a massive user of Typescript, though I see it could be very useful in some situations. 

The main issue is that I think the additional cognitive load isn’t trivial, and so code that you could easily skim through to get a good idea of what’s going on becomes full of little hurdles. Perhaps it’s something you get used to, but I fear it would seriously impact my ability to read and understand code. It decreases visibility.

Having said that, I really like that you can specify the definitions in JSDoc. That’s cool because the code remains regular, fast to read javascript code. If you are wondering about types, just look at the JSDoc, which is always right next to the function declarations anyway. 

Though you don’t get the full power of Typescript using it that way, only the type checking. I’d also like to be able to use interfaces and other object oriented features that come with Typescript.

Which brings me to the point of this post. If you are using full fat Typescript, IMO the way to define the types in the function arguments sucks. Reason being that it uses the colon (:) character. 

```javascript
function equals(x: number, y: number): boolean {
    return x === y;
}
```

I don’t like that because the colon character is for objects declarations. Following years of writing javascript objects, my brain’s muscle memory visually associates that character with objects, so when I’m scanning a page I can easily jump to places on the page without having to fully read the code. Using : in function arg type definitions breaks that for me. I find it’s much more difficult to quickly get my bearings in Typescript code.

I’m also not a fan of long function argument lists and Typescript doubles or triples the length of function argument lists. I feel that function declarations need to be short and to the point. It makes reading code much easier. I don’t find that having the return type is very useful in the function definition. It just feels like clutter to me. 

Some people say they like to know the types before they get into the function. Personally I find that once you start reading the code inside a function, it’s usually very obvious to differentiate between objects, arrays, strings, numbers etc. If I want to know the type, it’s preferable to glance at the JSDoc for the function. 

There’s a [proposal to bring some Typescript syntax to javascript](https://devblogs.microsoft.com/typescript/a-proposal-for-type-syntax-in-javascript/). Personally I’d like it if the type definitions were kept separate, keep function declarations readable!  But I would like javascript to have interfaces and additional OO features.