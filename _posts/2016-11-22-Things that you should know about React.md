---
layout: post
title: Things that you should know about React
tags:
 - javascript
 - react
 - flux
---
I just started using [Facebook's React library][1] and want to share the most important things that one should always
keep in mind when using library.

<!--more-->

I will list below some things starting from the most important ones.

## Flux

Facebook suggests its own architecture for building UI called [Flux][2] and as they claim this architecture is better
scalable and testable compared to [MVC][3] architecture.

I suggest you watch the video below about it:

<div class="hs-responsive-embed-youtube wrap">
    <iframe width="768" height="432" src="https://www.youtube.com/embed/nYkdrAPrdcw?vq=hd720&rel=0" frameborder="0" allowfullscreen></iframe>
</div>

## My points

Few important things that you always should keep in mind are:

 - `render()` method is always called when state of component is changed
 
 - `render()` method does not completely re-render DOM node every time, instead it uses virtual DOM mechanism to detect changes
   and then apply only them
 
 - You should keep `render()` as flat as it is possible and should never use `setState()` there as it may cause infinite loops
 
 - You can access sub components using `ref` attribute
 
 - You definitely may want to add [JSX][4] sugar to your react app, but **remember** that it is not part of react library itself

## Quick start project

You might want to check quick start project that [I published here][5].

**Installation**

Via git (or downloaded tarball):

<pre><code class="language-bash">$ git clone git://github.com/gevorg/react-quick-start.git
</code></pre>

**Running**

<pre><code class="language-bash">$ cd react-quick-start
$ npm install
$ npm start

> node app.js

Listening on 5000
...
</code></pre>


## Related links

- [A Javascript Library for building UI][1]
- [Application Architecture for building UI][2]
- [Model–view–controller][3]
- [JSX In Depth][4]
- [Quick start project for react library][5]


[1]:https://facebook.github.io/react/
[2]:https://facebook.github.io/flux/
[3]:https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller
[4]:https://facebook.github.io/react/docs/jsx-in-depth.html
[5]:https://github.com/gevorg/react-quick-start