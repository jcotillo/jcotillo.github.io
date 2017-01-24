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

{% highlight Python %}
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
{% endhighlight %}

**Medium recursion: here we must find the biggest key SMALLER than given key. we recursively call ourselves until we find the floor level of either side. Always moving to the right until we hit a None value at which point we'll return the node desired (the right most node STILL below key). This was tricky to me because of the separate calls to the recursive method; one a return and the other an assignment. The first recursive call with return ensures that we will continue to look left FIRST when the key is still smaller than node being explored currently. It will end once the key is BIGGER than the current node key at which point it'll explore the floor of the right side(looking left first). It will return the last node if the same key is not found.**

{% highlight Python %}
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
{% endhighlight %}

**Advanced recursion: This is to me is the most complicated piece of recursive code in BST. First we have the generic base case, return None when we are at the last node. The next lines are for comparing the key to the current node; only do half the work of exploring ONE tree. When you find the node, if it only has ONE child change the links of that child to the parent. if it has two we move to the last bit of code where we find the min and modify it its right pointer to go to the right child of the soon-to-be-deleted node. Adjust N of each node as you fold back up.**

{% highlight Python %}
def delete(self, key):
        self.root = self._delete(self.root, key)

    def _delete(self, node, k):
        if node is None:
            return None
        if k < node.key:
            node.left = self._delete(node.left, k)
        elif k > node.key:
            node.right = self._delete(node.right, k)
        else:
            # if node only has one child, replace it with that child node
            if node.right is None:
                return node.left
            if node.left is None:
                return node.right

            # if node has TWO children
            t = node
            # go to the right tree and get smallest child to uphold BST symmetry
            node = self._get_min_node(t.right)
            # make the right
            node.right = self._delete_min(t.right)
            node.left = t.left

        node.N = self._size(node.left) +  self._size(node.right) + 1
        return node
{% endhighlight %}

I totally recommend using Python tutor to visualize the trace of these calls. I know I have to draw it out by hand with examples to make sure I understand what is happening, where. Recursion is still too confusing sometimes.
