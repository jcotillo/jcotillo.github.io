---
layout: inner
title: 'My First Normal Post on Jekyll'
categories: blog development
tags: html css javascript
featured_image: 'https://31.media.tumblr.com/tumblr_loybogm3481qzs6oc.jpg'
lead_text: 'I miss fat cats.'
---

Sleepy, dreaming of cuddling with fuzzy beings.

{% highlight javascript %}
function meow() {
    return 'meow';
}

function bark() {
    return 'woof';
}

function getRandomAnimal() {

    var animals = [
        'cat',
        'dog',
        'hippo',
        'lion',
        'bear',
        'zebra'
    ];

    return animals[Math.floor(Math.random()*animals.length)];
}

console.log(meow());
console.log(bark());
console.log(getRandomAnimal());
{% endhighlight %}
