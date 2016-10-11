---
layout: post
title: Why I love using GitHub Pages with Jekyll?
social: true
tags:
 - github
 - jekyll
summary: "
"
---
After using [GitHub Pages](https://pages.github.com/) for my websites I have some things to share with you.

There are many good things that I loved about it, starting from simple fact that it is completely free to use and
ending with more advanced feature like custom urls.

But also there are few things that I did not like about it and those are mostly cases when I met platform limitations.
<!--more-->

## What is it?

[GitHub Pages](https://pages.github.com/) is free hosting solution wired with your GitHub repositories. So you
need to create GitHub repository, configure few settings and it becomes website hosted on Github.

## Possible usages
You can use it in many ways, but I think the main usages are:

- Personal website / blog
- Project website for presentation / documentation / tutorials / demo
- anything that works on javascript / css / html and sure Jekyll is plus

## Just create repository with your username:

<pre><code class="language-bash">$ git clone https://github.com/username/username.github.io
$ cd username.github.io
$ echo "Hello World" > index.html
$ git commit -am "Initial commit"
$ git push -u origin master
</code></pre>

And you are done, simple website will be available via **username.github.io** url.

## Or create branch gh-pages for existing project:

And your website will be available via **http://username.github.io/repository** url.

## Wire it with your domain

You just need to change domain's A records to following ip addresses:

 - 192.30.252.153
 - 192.30.252.154

And create file [**CNAME**](https://github.com/gevorg/gevorg.github.io/blob/master/CNAME) with your domain name inside.

## Limitation

You can not install any Jekyll plugin on it, but some are [available](https://help.github.com/articles/configuring-jekyll-plugins/)

- jekyll-mentions
- jemoji
- jekyll-redirect-from
- jekyll-sitemap
- jekyll-feed

## Related links

- [Websites for you and your projects](https://pages.github.com/)
- [Configuring A records with your DNS provider](https://help.github.com/articles/setting-up-an-apex-domain/#configuring-a-records-with-your-dns-provider)
- [Configuring Jekyll plugins](https://help.github.com/articles/configuring-jekyll-plugins/)