---
layout: post
title: Javascript generator functions
tags:
 - javascript
 - node.js
---
I just discovered for myself relatively new thing and that is generator function in javascript.

<pre><code class="language-javascript">function* name([param[, param[, ... param]]]) {
   // statements
}</code></pre>

In this post I will share few nice usages and many good things about them.
<!--more-->

## Simple sample

There are few things that you must know about generator functions

 - These are functions that you can pause and resume
 - `function*` is used to declare one
 - `yield` is used to pause execution
 - `next()` function is used to resume execution

<pre><code class="language-javascript">function* idMaker(){
  var index = 0;
  while(index < 3)
    yield index++;
}

var gen = idMaker();

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // undefined</code></pre>

In sample above `yield` is used to pause execution and return current value of `index`.
Return value format for `next()` is following

<pre><code class="language-json">{ value: 'some value passed using yield', done: [true | false] }</code></pre>

## Sample with input

You can pass data to current execution step using `next()` function.

<pre><code class="language-javascript">function *foo(x) {
   var y = 2 * (yield (x + 1));
   var z = yield (y / 3);
   return (x + y + z);
}

var it = foo( 5 );

// note: not sending anything into `next()` here
console.log( it.next() );       // { value:6, done:false }
console.log( it.next( 12 ) );   // { value:8, done:false }
console.log( it.next( 13 ) );   // { value:42, done:true }
</code></pre>

## Jumping from one generator to another

You can jump from one generator to another using `yield*` inside generator

<pre><code class="language-javascript">function* anotherGenerator(i) {
  yield i + 1;
  yield i + 2;
  yield i + 3;
}

function* generator(i){
  yield i;
  yield* anotherGenerator(i);
  yield i + 10;
}

var gen = generator(10);

console.log(gen.next().value); // 10
console.log(gen.next().value); // 11
console.log(gen.next().value); // 12
console.log(gen.next().value); // 13
console.log(gen.next().value); // 20
</code></pre>

## Why should you use generator functions?

Every developer familiar with async model that [node.js](https://nodejs.org/) uses, knows that async
code becomes long list of nested callback functions. Let's look following sample

<pre><code class="language-javascript">...
login(username, password, function(user) {
    loadPosts(user.id, function(posts) {
        ...
    });
});
...
</code></pre>

using generator functions you can transform your nested callback functions into nice/readable statements

<pre><code class="language-javascript">...
var user = yield login(username, password);
var posts = yield loadPosts(user.id);
...
</code></pre>

You can check [co](https://github.com/tj/co) module for more information.

## Related links
- [function* - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function*)
- [ES6 Generators](https://davidwalsh.name/es6-generators)
- [The ultimate generator based flow-control goodness](https://github.com/tj/co)