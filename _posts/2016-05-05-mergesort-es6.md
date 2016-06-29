---
layout: post
title:  "Merge sort, JavaScript and ECMAScript 2015 (ES6)"
date:   2016-05-05
excerpt: "Minimal, one column Jekyll theme for your blog."
project: true
tag:
- jekyll 
- moon
- blog
- about
- theme
comments: true
---

This post is for people who already have basic understanding of what an algorithm, Big O notation and JavaScript is, you can learn more about these topics here, here and here.

This post will go through the implementation of the popular sorting function merge sort in JavaScript and how using ES6 features could be used to write a more succinct plus elegant implementation.

## What is Merge sort? 

Merge sort is an algorithm capable of sorting a list faster than other simple sorting algorithms.

## Why is Merge sort important? 

When comparing algorithms people use something called Big O notation, what basically is a mathematical representation of how long the execution of a particular logic will take. Merge sort has a Big O notation of N(LogN) — where N is the number of things to sort — and the most simple sorting algorithms have N * N, and well, N(LogN) is less than N * N.

Merge sort is used to implement Array.sort() in JavaScript by major browsers like Mozilla (in case of Google chrome, it use other algorithm called Quick sort, as you can check here).

## What is the idea behind Merge sort? 

Merge sort splits the initial list into smallest ones and sorts the content, and then put them together again.

For example, the image below shows a list of elements: [6, 5, 3, 1, 8, 7, 2, 4]. Then this initial lists is split into [6, 5, 3, 1] and [8, 7, 2, 4]. Then again into [6, 5] , [3, 1], [8. 7] and [2, 4]. And one more time: [6], [5], [3], [1], [8], [7], [2] and [4]. The splitting ends when it is not possible to continue, and that happens when each list has a length of one.

On the list joining phase, the algorithm starts joining the single element lists into: [5, 6], [1, 3], [7, 8], [2, 4] — sorting them each time it does — . Then the process continues to [1, 3, 5, 6], [2, 4, 7, 8] and finally [1, 2, 3, 4, 5, 6, 7 ,8].

![Mergesot ilustration from Wikipedia](assets/img/mergesort.gif')

## Go to the implementation 

First let’s define a function called mergesort, using ES5 friendly syntax (more wide spread version of JavaScript on browser and server side).

<script src="https://gist.github.com/nandodrw/ee6749f47f24cd51892fd31dd830771b.js"></script>

Now let’s check a ES6 version:

<script src="https://gist.github.com/nandodrw/52c250a977106991badc0ae8291d93e2.js"></script>

First of all, the less amount of code is remarkable. on the ES6 version, the line 6 is using the default parameter feature; in case no function is passed to the mergesort function, the code sets a default one. You can learn more about default params on JavaScript here. This line is also using a ES6 feature called fat arrow functions or lambda functions. Fat arrow function, in addition to being convenient notation comes with other features like lexical This binding, you can find more here.

More interesting, line 12 of the ES6 version is using something called destructuring, which basically allows to create and assign values from a data structure like an object. Destructuring assignment has very interesting applications that you can dive deeper into here.

You may have noticed the code comments on the ES6 version says to use the following flags. This is if you test the code in Node 5.0.0 — this is not needed on Node 6.2.0 — :

```
--harmony_default_parameters

--harmony_destructuring
```

These flags are needed since the version of V8 in node 5.0.0 has the default parameters and destructuring as experimental features. If you are not sure what V8 is, you can learn more about it here.

The two snippets of code shown before relies on the existence of the functions splitList and jointLists:

<script src="https://gist.github.com/nandodrw/535df05d39acc9a31508a8b164e27b7a.js"></script>

This last code is ES5 friendly. If we add destructuring on line 14 to save couple lines of code, the functions will turn into:

<script src="https://gist.github.com/nandodrw/25c669dd4cdab0696fd263d6eaf81e6c.js"></script>

Finally the whole code for an ES6 friendly environment, including a testing call, will be:

<script src="https://gist.github.com/nandodrw/ad0e8c3318a0e30a8b3b3e05a23573f8.js"></script>

To run this code in your local Node 6.2.0 just type on the console:

`node mergesort-complete-es6.js`

Or in Node 5.0.0:

`node --harmony_default_parameters --harmony_destructuring mergesort-complete-es6.js`

I you are not sure of which version of Node JS you have, you can type:

`node -v`