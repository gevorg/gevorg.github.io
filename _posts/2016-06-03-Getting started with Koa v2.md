---
layout: post
title: Getting started with Koa v2
tags:
 - javascript
 - node.js
 - koa
 - es2015
---
I just started using [Koa - next generation web framework for node.js][koa] 
and want to share few good things about it.
<!--more-->

## Hello World!

Basic server written using [koa] framework looks like this

<pre><code class="language-javascript">import Koa from 'koa';
const app = new Koa();

// Setup handler.
app.use(async ctx => {
    ctx.body = "Hello World!";
});

// Start server.
app.listen(3000);
</code></pre>

You might notice sample uses `async`, `import` and obviously those are 
not yet supported in current version of Node.js. 

Plan is to have full support of [next generation javascript][es2015] 
in future Node.js releases and for now modules like [babel] help us.

## Babel sample

To run sample first we need to install [babel] compiler

<pre><code class="language-bash">$ npm install babel-core --save
$ npm install babel-preset-es2015-node5 --save
$ npm install babel-preset-stage-3 --save
</code></pre>

Then we need to create start script for it

<pre><code class="language-javascript">// set babel in entry file
require('babel-core/register')({
    presets: ['es2015-node5', 'stage-3']
});

require('./app');
</code></pre>

After we need to include all [next gen js][es2015] into `app.js` file and run
`node index.js` to start server.

## Future steps

Just after Node.js will add support for [next gen js][es2015], the only thing 
that will be required is to remove `index.js` file and everything else
should work like a pie :)

## Related links
- [Koa - next generation web framework for node.js][koa]
- [Use next generation JavaScript, today][babel]
- [Learn ES2015][es2015]

[koa]: http://koajs.com
[babel]: http://babeljs.io/
[es2015]: https://babeljs.io/docs/learn-es2015/