---
layout: inner
title: 'Are you trying to tell me that dynamic programming is not dynamic?'
tags: dynamic programming
featured_image: 'http://i.giphy.com/6wM4Zhs4h4PGo.gif'
lead_text: 'When computer science has a sense of humor'
---
>Dynamic programming is mostly just a matter of taking recursive algorithm and finding the overlapping subproblems. You then cache those results for future recursive calls.

Gayle of *cracking the coding interview* has such a way with words. She always seems to show you a simple problem and leaves you hanging for the questions! Just kidding, it's great.

Dynamic programming emphasizes the advantage of caching the results of operations. Combined with recursive calls, this technique can drastically lower running time. One way of caching them is referred to as memoization. This approach assumes the sub-problems are solved and views the tree from the top and evaluates the subproblems from the leaves/nodes back up towards the root. Alternative, bottom-up dynamic programming looks to solve the subproblems first. It establishes an order of computations that is important to memory use of the algorithm.

~to be continued~
