---
layout: post
title: Writing modules with pure javascript
social: true
tags:
 - javascript
---
Recently I was working on javascript project called [FooFiles](http://foofiles.com) and want to write about pattern
that I used there.

I will explain pattern and write a bit about positive and negative things that I found.
<!--more-->

## What I needed?

I needed modular pattern to use it in my application and certainly there are many libraries or
external tools that I can use to achieve that.

Good option could be to use [CoffeeScript](http://coffeescript.org/) or [require.js](http://requirejs.org/) that are
perfectly doing that.

However I had specific rule for my project to have no external dependencies for core part of it, so it runs fast and
smooth.

## My pattern

Below is what I decided to use:

<pre><code class="language-javascript">// New FooFiles unit.
ff.newUnit = (function(dependency1, dependency2, undefined) {
    'use strict';

    // Private data/functions go here.
    var privateString = "Very Private";
    function privateFunc(param1, param2) {
        ...
    }
    ...

    // Public data/functions go here.
    var self = {
        publicString: "Hello Unit!",
        publicFunc: function (param1) {
            ...
        }
        ...
    };

    // Return unit instance.
    return self;
})(dependency1, dependency2);
</code></pre>

## Good things

Good things about this pattern are:

- To expose things you just need to wire them to `self` object or they will remain private
- Usage parameters are listed as input parameters for anonymous function call, so you must define input for each `module`
- If someone will change `undefined` in external scope that will not affect your module, because it has its own version inside.

## Bad things

I had problems with this pattern in case of module interdependency.
Instead of managing load cycles I decided to use [observer pattern](https://en.wikipedia.org/wiki/Observer_pattern) to
detach modules that are interdependent.

So if `module1` and `module2` were interdependent, I removed one side dependency and replaced it with following:

<pre><code class="language-javascript">// From module1
on('EVENT_FROM_MODULE', function(data) {
...
});

...
// From module2
fire('EVENT_FROM_MODULE', {data: 'some important data'});
...
</code></pre>

## Related links

- [FooFiles is your very own personal file space on web](https://github.com/gevorg/foofiles)
- [Observer pattern](https://en.wikipedia.org/wiki/Observer_pattern)
- [Immediately-invoked function expression](https://en.wikipedia.org/wiki/Immediately-invoked_function_expression)
