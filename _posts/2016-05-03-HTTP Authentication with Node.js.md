---
layout: post
title: HTTP Authentication with Node.js
social: true
tags:
 - node.js
---
Everyone familiar with [Apache HTTP Server](https://httpd.apache.org/) knows the most popular way of setting up
HTTP Basic / Digest access authentication.

Yes! I want to write about .htpasswd and .htdigest files and how can you use them in your Node.js application.
<!--more-->
In this article I will write about [http-auth](http://http-auth.info/) module that I created to support .htpasswd and
.htdigest files in Node.js applications.

## Installation
The best way of installing it is via [npm](https://www.npmjs.com/):

<pre><code class="language-bash">$ npm install http-auth</code></pre>

## Usage
Depending what type of authentication you want to use you should call corresponding method `auth.basic` or
`auth.digest`. You can view available configurations in [configurations section](https://github.com/http-auth/http-auth#configurations).

<pre><code class="language-javascript">// Authentication module.
var auth = require('http-auth');
var basic = auth.basic({
    realm: "Simon Area.",
    file: __dirname + "/../data/users.htpasswd"
});

// Creating new HTTP server.
http.createServer(basic, function(req, res) {
    res.end("Welcome to private area - " + req.user + "!");
}).listen(1337);
</code></pre>

You might notice that application is calling [http.createServer](https://nodejs.org/api/http.html#http_http_createserver_requestlistener)
with mutated argument list, which is strange.

Correct! Application is changing native node.js method to provide some flexibility in usage. You might
say that it is not future proof and **one should never change what he / she does not own**.

You are right, I just thought that there is very little possibility that the most used method in [Node.js](https://nodejs.org) will be changed.

## Integrations
Module has integrations with some popular [Node.js](https://nodejs.org) modules and for sure the most important one is
[express.js](http://expressjs.com) integration.

<pre><code class="language-javascript">// Authentication module.
var auth = require('http-auth');
var basic = auth.basic({
    realm: "Simon Area.",
    file: __dirname + "/../data/users.htpasswd"
});

// Application setup.
var app = express();
app.use(auth.connect(basic));

// Setup route.
app.get('/', function(req, res){
  res.send("Hello from express - " + req.user + "!");
});
</code></pre>

## Command line tools
As a bonus you can install [htpasswd](https://github.com/http-auth/htpasswd/) or [htdigest](https://github.com/http-auth/htdigest/)
command line tools using npm. Those should provide functionality similar to Apache's tools.

<pre><code class="language-bash">$ npm install -g htpasswd</code></pre>

or

<pre><code class="language-bash">$ npm install -g htdigest</code></pre>

## Related links

- [Node.js package for HTTP basic and digest access authentication.](http://http-auth.info)
- [GitHub repository](https://github.com/http-auth/http-auth)