---
layout: inner
title: 'Hashing: A documentary'
tags: hashtable miami
featured_image: 'http://i.giphy.com/vPMnDdfHx13Bm.gif'
lead_text: 'When I live in Miami and everything reminds me of a rap song'
---
Who knew that there could be so much more into hashing than simply the key-value pair storage? I had never given much though of how exactly that was possible. It turns out, there are many ways to compute values into a hash function. The most basic approach is taking the modulo remainder of the hash length and the value and storing it accordingly.

Ideally, we would avoid collision by constructing a **perfect hash function** - one that maps each item into a unique slot. We could accomplish this in many ways:

1. increasing the size of the hash table so that each possible value in the item range can be accommodated.
  * Impractical with large dataset.
2. **Folding method** begins by dividing the item into equal-size pieces (the last piece may not be of equal size). Adding these pieces together and taking the modulo of that will result in a placement.
  * Some folding methods go one step further and reverse every other piece before the addition.
3. Another numerical technique for constructing a hash function is called the **mid-square method**. We first square the item, and then extract some portion of the resulting digits.
  * For example, if the item were 44, we would first compute 442=1,936442=1,936. By extracting the middle two digits, 93, and performing the remainder step, we get 5 (93 % 1193 % 11).

Cannot talking about hashing methods, without covering **Collision resolution techniques**:

1. Open addressing tries to find the next open slot or address in the hash table.
  * By systematically visiting each slot one at a time, we are performing an **open addressing technique** called linear probing.
2. To deal with clustering, **rehashing** is a nifty way of dealing with the new values.
  * With simple linear probing, the rehash function is newhashvalue = rehash(oldhashvalue) where rehash(pos)=(pos+1)%sizeoftable... 1 being the skip value. Note: a prime number ensures that the table is eventually distributed.
3. A variation of the linear probing idea is called **quadratic probing**.
  * Instead of using a constant “skip” value, we use a rehash function that increments the hash value by 1, 3, 5, 7, 9, and so on. This skips a perfect squares succesives.
4.  **Chaining**  allows many items to exist at the same location in the hash table. 
