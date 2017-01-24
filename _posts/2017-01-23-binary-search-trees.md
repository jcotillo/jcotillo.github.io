---
layout: inner
title: 'BST: A Recursive Experience'
tags: bst binary
featured_image: 'http://i.giphy.com/1YJPV0RAWkecw.gif'
lead_text: 'I found this image randomly on Giphy and I love how it ends at the worst-case scenario O(sq(n)) heheh'
---
Probably one of the most challenging data structures that I code'd in python so far (well, since I came back into the coding world a month ago). Maybe because this was the first time I seen the power of recursion really show off. Beyond the concept of nodes with two children at most, BST offers recursive methods under the hood that allow flexible and reliable data manipulation. Following along Princeton's Algorithms I, my implementation is divided between public methods which begin the call stack to their supplementary private methods.
[Complete code here.](https://github.com/jcotillo/princeton_algorithms/blob/master/week_4/binary_search_tree.py)

**Easy recursion: base case is when the node is found. Keep moving in the correct direction until found.**

``` python
def get(self, key):
    return self._get(self.root, key)

# recursive private method
def _get(self, key):
    x = self.root
    while x is not None:
        if key == x.key:
            return x.val
        if key < x.key:
            return self._get(x.left, key)
        else:
            return self._get(x.right, key)
```

**Medium recursion: here we must find the biggest key SMALLER than given key. we recursively call ourselves until we find the floor level of either side. Always moving to the right until we hit a None value at which point we'll return the node desired.**

``` python
  def floor(self, key):
    x = self._floor(self.root, key)
    return x.key if x is not None else None

  def _floor(self, x, key):
    if x is None:
        return None
    if key == x.key:
        return x
    elif key < x.key:
        return self._floor(x.left, key)
    # go to the right tree always...
    t = self._floor(x.right, key)
    return t if t is not None else x
```
