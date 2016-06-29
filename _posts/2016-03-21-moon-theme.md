---
layout: post
title:  "Merge sort, JavaScript and ECMAScript 2015 (ES6)"
date:   2016-02-05
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



![Moon Homepage](https://cloud.githubusercontent.com/assets/754514/14509720/61c61058-01d6-11e6-93ab-0918515ecd56.png)    
    
<center><b>Moon</b> is a minimal, one column jekyll theme.</center>
     
 I'm not a developer or designer. And I don't add footer to show who did this theme. If you like this theme or using it, please give a **star** for motivation, It makes me happy.

<iframe src="https://ghbtns.com/github-btn.html?user=TaylanTatli&repo=Moon&type=star&count=true&size=large" frameborder="0" scrolling="0" width="160px" height="30px"></iframe>    
      
## Installation
* Fork the [Moon repo](https://github.com/TaylanTatli/Moon/fork)
* Edit `_config.yml` file.
* Remove sample posts from `_posts` folder and add yours.
* Edit `index.md` file in `about` folder.
* Change repo name to `YourUserName.github.io`    
     
That's all.

## Preview

{% capture images %}
	https://cloud.githubusercontent.com/assets/754514/14509716/61ac6c8e-01d6-11e6-879f-8308883de790.png
	https://cloud.githubusercontent.com/assets/754514/14509717/61ad05ae-01d6-11e6-85ae-5a817dd8763b.png
	https://cloud.githubusercontent.com/assets/754514/14509714/61a89708-01d6-11e6-8fcd-74b002a060df.png
{% endcapture %}
{% include gallery images=images caption="Screenshots of Moon Theme" cols=3 %}

---

{% capture images %}
	https://cloud.githubusercontent.com/assets/754514/14509718/61b09a20-01d6-11e6-8da1-4202ae4d83cd.png
	https://cloud.githubusercontent.com/assets/754514/14509715/61aa9d00-01d6-11e6-81a6-c6837edf2e84.png
{% endcapture %}
{% include gallery images=images caption="Moon Theme on Small Screen Size" cols=2 %}      
      
See a [live version of Moon](http://taylantatli.github.io/Moon) hosted on GitHub.      

## Site Setup
A quick checklist of the files you’ll want to edit to get up and running.    

### Site Wide Configuration
`_config.yml` is your friend. Open it up and personalize it. Most variables are self explanatory but here's an explanation of each if needed:

#### title

The title of your site... shocker!

Example `title: My Awesome Site`

#### bio

The description to show on your homepage.

#### description

The description to use for meta tags and navigation menu.

#### url

Used to generate absolute urls in `sitemap.xml`, `feed.xml`, and for generating canonical URLs in `<head>`. When developing locally either comment this out or use something like `http://localhost:4000` so all assets load properly. *Don't include a trailing `/`*.

Examples:

{% highlight yaml %}
url: http://taylantatli.me/Moon
url: http://localhost:4000
url: //cooldude.github.io
url:
{% endhighlight %}

#### reading_time

Set true to show reading time for posts. And set `words_per_minute`, default is 200.

#### logo
Your site's logo. It will show on homepage and navigation menu. Also used for twitter meta tags.

#### background
Image for background. If you don't set it, color will be used as a background.

#### Google Analytics and Webmaster Tools

Google Analytics UA and Webmaster Tool verification tags can be entered in `_config.yml`. For more information on obtaining these meta tags check [Google Webmaster Tools](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35179) and [Bing Webmaster Tools](https://ssl.bing.com/webmaster/configure/verify/ownership) support.

#### MathJax
It's enabled. But if you don't want to use it. Set it false in  `_config.yml`.

#### Disqus Comments
Set your disqus shortname in `_config.yml` to use comments.

---

### Navigation Links

To set what links appear in the top navigation edit `_data/navigation.yml`. Use the following format to set the URL and title for as many links as you'd like. *External links will open in a new window.*

{% highlight yaml %}
- title: Home
  url: /

- title: Blog
  url: /blog/

- title: Projects
  url: /projects/

- title: About
  url: /about/

- title: Moon
  url: http://taylantatli.me/Moon
{% endhighlight %}

---

## Layouts and Content

Moon Theme use [Jekyll Compress](https://github.com/penibelst/jekyll-compress-html) to compress html output. But it can cause errors if you use "linenos" (line numbers). I suggest don't use line numbers for codes, because it won't look good with this theme, also i didn't give a proper style for them. If you insist to use line numbers, just remove `layout: compress` string from layouts. It will disable compressing.

### Feature Image

You can set feature image per post. Just add `feature: some link` to your post's front matter.

```
feature: /assets/img/some-image.png
or
feaure: http://example.com/some-image.png
```    
 This also will be used for twitter card:

![Moon Twitter Card](https://cloud.githubusercontent.com/assets/754514/14509719/61c5751c-01d6-11e6-8c29-ce8ccad149bf.png)

### Comments
To show disqus comments for your post add `comments: true` to your post's front matter.

---

## Questions?

Found a bug or aren't quite sure how something works? By all means [file a GitHub Issue](https://github.com/TaylanTatli/Moon/issues/new). And if you make something cool with this theme feel free to let me know.

---

## License

This theme is free and open source software, distributed under the MIT License. So feel free to use this Jekyll theme on your site without linking back to me or including a disclaimer.
