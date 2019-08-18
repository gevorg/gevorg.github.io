---
layout: post
title: Python is a great programming language
tags:
 - python
---
Recently I started learning [Python] programming language and loved it a lot.

It is very rich, it is based on principles that I adore and if you know the right way of doing things, you can write
great piece of software just with a few lines of code.
<!--more-->

## Zen of Python
I will start from guiding principles for [Python] design, which one should always keep in mind.

- Beautiful is better than ugly.
- Explicit is better than implicit.
- Simple is better than complex.
- Complex is better than complicated.
- Flat is better than nested.
- Sparse is better than dense.
- Readability counts.
- Special cases aren't special enough to break the rules.
- Although practicality beats purity.
- Errors should never pass silently.
- Unless explicitly silenced.
- In the face of ambiguity, refuse the temptation to guess.
- There should be one-- and preferably only one --obvious way to do it.
- Although that way may not be obvious at first unless you're Dutch.
- Now is better than never.
- Although never is often better than *right* now.
- If the implementation is hard to explain, it's a bad idea.
- If the implementation is easy to explain, it may be a good idea.
- Namespaces are one honking great idea -- let's do more of those!

These principles are known as [PEP 20] or **The Zen of Python**.

## Many ways of doing things

What is great about [Python] is that you can implement same functionality in many ways and depending which path you
choose it describes your maturity level.

Let's consider simple task **create a concatenated string from 0 to 19**:

**Bad solution**

<pre><code class="language-python"># create a concatenated string from 0 to 19 (e.g. "012..1819")
nums = ""
for n in range(20):
  nums += str(n)   # slow and inefficient
print nums
</code></pre>

**Good solution**

<pre><code class="language-python"># create a concatenated string from 0 to 19 (e.g. "012..1819")
nums = []
for n in range(20):
  nums.append(str(n))
print "".join(nums)  # much more efficient
</code></pre>

**Best solution**

<pre><code class="language-python"># create a concatenated string from 0 to 19 (e.g. "012..1819")
nums = [str(n) for n in range(20)]
print "".join(nums)
</code></pre>

## Final conclusion
I would definitely suggest [Python] to any programmer, because in good hands it becomes great tool for magic.

One should certainly consider following guide [The Hitchhiker’s Guide to Python!].

## Related links
- [Python]
- [The Hitchhiker’s Guide to Python!]
- [PEP 20]

[Python]: https://www.python.org/
[The Hitchhiker’s Guide to Python!]: http://docs.python-guide.org/en/latest/
[PEP 20]: https://www.python.org/dev/peps/pep-0020/