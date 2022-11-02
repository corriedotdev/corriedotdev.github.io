---
layout: post
title: Hosting a Jekyll blog with no database
excerpt: "This website is hosted without a back end. Imagine developing numerous static HTML pages such as header, content and footer elements and then stitching them together to get the page you see now. A static site generator builds a website once, then delivers the pages as static pages with no server side processing. From a high level, its doing a find and replace on key values.."
categories: [code👨‍💻]
comments: true
---

# How this site was created

I love the simplicity of this site. Writing a post in a code editor and compiling it like a project is more familiar than using a commercial solution. I also feel less restricted with what I can develop on the site without jumping through hurdles. 

The platform has no third party storage access such as databases and the cms being used is jekyll. If you want to call it that. 

From my understanding since starting the site up last night is that it it will ask for various configuration variables such as title, theme, categories etc and it will then inject these values this into generated html pages. Basically a super find and replace function for site themes. Its a little smarter however as we can set up categories, tags and links to other social media with only changing it in one place. What is kind of interesting is you have to "compile" the site every time you make a new post. I quite like it as I have it running locally and don't need to follow the auto deployments that github will do once you upload the site to your git repo. Thats where this site will live and be hosted at, github pages is a tool integrated into github repo that now allow you to host your own static sites on it.

If you want to set up yourself, then I would advise loading [this](https://jekyllrb.com/docs/step-by-step/01-setup/) in another tab. In short these are the steps to get the site set up. I did find some issues and this was primarily due to different site theme templates requiring different dependencies specified in the sites gem file. 

## In short
These are the key things that can get you set up pretty quickly.
1. Fork a [theme](https://jekyllthemes.io/free) you like
2. Install [ruby 2.6 dev kit](https://rubyinstaller.org/downloads/) 
3. Install Jekyll 
4. Run the gem file  
5. CD to your theme dir and run 

**Watch out!** 
Need version < 2.7 of Ruby for a lot of themes due to dependency on nokogiri
{: .notice}

### Redirecting to your domain
Github may change their DNS entries but im sure we will be informed or they will auto redirect. Add the following to your A entry for your domain you have purchased. Then head on over to your repo settings and enter your domain under the github pages section.

![DNS Values]({{ site.url }}/img/github-dns.PNG)

### Commands used

This will install Jekyll in your Ruby development environment 
{% highlight ruby %} 
$ gem install jekyll bundler 
{% endhighlight %}

Initially you could just create a new website and then test out functionality once you have completed the steps above. This will then let you clone a theme into the repo and test it locally!
{% highlight ruby %} 
$ jekyll new website
{% endhighlight %}

Updates gem packages
{% highlight ruby %} 
$ bundle install 
{% endhighlight %}

After any changes re run this is the main one
{% highlight ruby %} 
$ bundle exec jekyll serve
{% endhighlight %}

## Further Reading
Check out the following links for inspiration and further reading about this topic
* [A low level breakdown of jekyll](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages)
* [List of supported Ruby Rogue languages for code snippet highlights](https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers)

<a href="#" id="emailclick" onclick="replace_email()">My Email</a>

<!-- SCRIPTS HERE -->
<script>
var email;

function add_mailto() {
  const elem = document.getElementById("emailclick");
  elem.href = `mailto:${email}`;
}

function replace_email() {
  // spam prevention
  const domain = "cjgstudio.com";
  const name = [16, 28, 1, 1, 26, 22];
  const xor_with = 115;
  let constructed = "";
  name.forEach(function(i) {
    constructed += String.fromCharCode(i ^ xor_with);
  })
  email = `${constructed}@${domain}`;
  const elem = document.getElementById("emailclick");
  elem.text = email;

  window.setTimeout(add_mailto, 100);
}
</script>