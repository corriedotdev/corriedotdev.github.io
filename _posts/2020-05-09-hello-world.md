---
layout: post
title: First Post
excerpt: "An initial post to play around with the syling of the site and get an idea on what to write."
categories: [code]
comments: true
---





# How this was made

This site is quite cool in my oppinion. The platform has no third party storage access such as databases and the cms being used is, I guess jekyll. 

From my understanding since starting the site up last night is that it it will ask for various configuration variables such as title, theme, categories etc and it will then inject these values this into generated html pages. Basically a super find and replace function for site themes. Its a little smarter however as we can set up categories, tags and links to other social media with only changing it in one place. What is kind of interesting is you have to "compile" the site every time you make a new post. I quite like it as I have it running locally and dont need to follow the auto deployments that github will do once you upload the site to your git repo. Thats where this site will live and be hosted at, github pages is a tool integrated into github repos that now allow you to host your own static sites on it.

{% highlight css %}
 bundle exec jekyll serve 
{% endhighlight %}
Example of the commands I have to run.

If you want to set up yourself, then I would advise reading this and then this. But in short these are the steps to get the site loaded. I did find some issues and this was primarily due to different site theme templates requiring different dependancies specified in the sites gem file. 

## In short
These are the key things that can get you set up pretty quickly.
1. Fork a theme you like into your repo
2. Install ruby 2.6 dev kit (I found that ruby 2.7 was too high for a lot of themes to run)
3. Install Jekyll 
4. Run the gem file  
5. CD to your theme dir and run 

{% highlight cmd %} 
gem install jekyll bundler 
{% endhighlight %}
{% highlight css %} 
bundle install 
{% endhighlight %}
{% highlight css %} 
bundle exec jekyll serve 
{% endhighlight %}



## List Types

### Ordered Lists

1. Item one
   1. sub item one
   2. sub item two
   3. sub item three
2. Item two

### Unordered Lists

* Item one
* Item two
* Item three

## Tables

| Header 1 | Header 2 | Header 3 |
|:--------|:-------:|--------:|
| cell 1   | cell 2   | cell 3   |
| cell 4   | cell 5   | cell 6   |
|----
| cell 1   | cell 2   | cell 3   |
| cell 4   | cell 5   | cell 6   |
|=====
| Foot 1   | Foot 2   | Foot 3   |

## Code Snippets

{% highlight css %}
 Debug.Log("We have code formatting");
{% endhighlight %}

## Buttons

Make any link standout more when applying the `.btn` class.

{% highlight html %}
<a href="#" class="btn btn-success">Success Button</a>
{% endhighlight %}

<div markdown="0"><a href="#" class="btn">Primary Button</a></div>
<div markdown="0"><a href="#" class="btn btn-success">Success Button</a></div>
<div markdown="0"><a href="#" class="btn btn-warning">Warning Button</a></div>
<div markdown="0"><a href="#" class="btn btn-danger">Danger Button</a></div>
<div markdown="0"><a href="#" class="btn btn-info">Info Button</a></div>

## Notices

**Watch out!** You can also add notices by appending `{: .notice}` to a paragraph.
{: .notice}

## Post Quote

> "Computers are useless.  They can only give you answers." - Pablo Picasso 

They have many uses and one is to get answers. I dont like this one.