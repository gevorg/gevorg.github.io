---
layout: post
title: Template literals in javascript
tags:
 - javascript
 - es2015
---
I want to write about another new thing that I found in javascript.
Those are called [Template literals] and look like this:

<pre><code class="language-javascript">`string text`

`string text line 1
 string text line 2`

`string text ${expression} string text`

tag `string text ${expression} string text`
</code></pre>

Let's see where we can use them.
<!--more-->

## Syntax

From sample above you case see that [Template literals] look like regular
strings, but with some extra features and instead of double quotes you
need to use back-ticks to declare them.

As a bonus you can define multi-line strings and embed any valid
 javascript expression in it. Let's see few usages below.
 
## Usages

Basic sample below uses template literal to pass name: 
 
<pre><code class="language-javascript">// Simple string substitution
var name = "Gevorg";
console.log(`Yo, ${name}!`);

// => "Yo, Gevorg!"
</code></pre>
 
you can embed function calls:
 
<pre><code class="language-javascript">function fn() { return "I am a result. Rarr"; }
console.log(`foo ${fn()} bar`);

//=> foo I am a result. Rarr bar.
</code></pre>

or just any valid javascript expression:

<pre><code class="language-javascript">var user = {name: 'Caitlin Potter'};
console.log(`Thanks for getting this into V8, ${user.name.toUpperCase()}.`);

// => "Thanks for getting this into V8, CAITLIN POTTER";
</code></pre>

## Tagged Templates

You can modify templates by placing function calls in front of them:

<pre><code class="language-javascript">var a = 5;
var b = 10;

function tag(strings, ...values) {
  console.log(strings[0]); // "Hello "
  console.log(strings[1]); // " world "
  console.log(strings[2]); // ""
  console.log(values[0]);  // 15
  console.log(values[1]);  // 50

  return "Boom-boom chacka-chaka!";
}

tag`Hello ${ a + b } world ${ a * b }`;
// => "Boom-boom chacka-chaka!"
</code></pre>


## Related links
- [Template literals]
- [Getting Literal With ES6 Template Strings](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

[Template literals]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals
