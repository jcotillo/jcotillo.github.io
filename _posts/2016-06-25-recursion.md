---
layout: inner
title: 'Recursion: inception in computer science'
categories: recursion computerscience
tags: algorithms
featured_image: 'https://media.giphy.com/media/ab641h7daG6Nq/giphy.gif'
lead_text: 'mindblown'
---
Recursion was a subject that has always surpassed logic to me. I would understand one example of recursion, but then would be entirely stunned by a different implementation. Here is my attempt to have a deeper understanding in recursion and the ways we can leverage this tool to solve problems.

## Three laws of recursion
1. A recursive algorithm must have a base case.
2. A recursive algorithm must change its state and move toward the base case
3. A recursive algorithm must call itself, recursively.

simple - ha? let's look at the classic example of a function that returns a string input in reverse.
{% highlight Python %}
  def reverse(s):
      if len(s) <= 1:
          return s
      else:
          return reverse(s[1:]) + s[0]

  reverse("hello")
{% endhighlight %}

Below, you can see that there is a stack of calls to reverse() and each time, the string has a character removed from the front until it meets the base case; when there is only character length. At this point, the stacked operations start being complete carrying the string up each layer and adding the last return of reverse and the first character of the string.. finalizing in an entirely reverted string. *Space complexity: n, memory: o(n)*

a more advanced problem:
[Tower of Hanoi](http://interactivepython.org/runestone/static/pythonds/Recursion/TowerofHanoi.html)

![stack calls]({{ site.url }}/assets/reverse_stack_calls.png)
