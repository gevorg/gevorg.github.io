---
layout: post
title: I know, I'll use regular expressions!
tags:
 - regexp
 - javascript
---
Famous [quote][1] says:

<blockquote>
    Some people, when confronted with a problem, think 
    "I know, I'll use regular expressions."   Now they have two problems.
</blockquote>

Let's see, if it is true and when you can use regular expressions.
<!--more-->

I will share my knowledge of regexp in JavaScript based on [this source][2].

## Basics

Regular expressions are used with the RegExp methods `test` and `exec` and with the String methods `match`, `replace`, `search`, and `split`. 

 - `exec` - A RegExp method that executes a search for a match in a string. It returns an array of information or null on a mismatch.

 - `test` - A RegExp method that tests for a match in a string. It returns true or false.

 - `match` - A String method that executes a search for a match in a string. It returns an array of information or null on a mismatch.

 - `search` - A String method that tests for a match in a string. It returns the index of the match, or -1 if the search fails.

 - `replace` - A String method that executes a search for a match in a string, and replaces the matched substring with a replacement substring.

 - `split` - A String method that uses a regular expression or a fixed string to break a string into an array of substrings.
 
<pre><code class="language-javascript">// Sample with replace 
var re = /(\w+)\s(\w+)/;
var str = "John Smith";
var newstr = str.replace(re, "$2, $1");
console.log(newstr);
// => "Smith, John".
</code></pre>

## Advanced searching with flags
  
Regular expressions have four optional flags that allow for global and case insensitive searching. 
These flags can be used separately or together in any order, and are included as part of the regular expression.

 - `g` - Global search.
 - `i` - Case-insensitive search.
 - `m` - Multi-line search.
 - `y` - Perform a "sticky" search that matches starting at the current position in the target string.
 
To include a flag with the regular expression, use this syntax:

<pre><code class="language-javascript">var re = /pattern/flags;
// or by using RegExp
var re = new RegExp("pattern", "flags");
</code></pre>

## When you should not use regexp?

As mentioned in [this answer][3]:

<blockquote>
Regular expressions are the wrong tool for the job because you are dealing with nested structures, i.e. recursion.
</blockquote>

## Related links

 - [I know, I'll use regular expressions][1]
 - [JavaScript Regular Expressions][2]
 - [Regular Expression to match outer brackets][3]

[1]:http://regex.info/blog/2006-09-15/247
[2]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions
[3]:http://stackoverflow.com/a/546457/972240