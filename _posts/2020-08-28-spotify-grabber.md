---
layout: post
title: Sentence a Day progressive app & Spotify Playlist Grabber
excerpt: "Two simple C# projects that I couldnt seem to find with third party software so developed a solution.I can create a diary entry for each day using some old windows forms code that allows for minimizing to icon tray, progressive and can be continually worked on while functionality is still supported. The Spotify grabber returns all the songs in a play list with their artist and album, great if you want to migrate away from Spotify and move onto another platform without losing playlists. "
categories: [c#, code]
comments: true
---

# Sentence a day

## Win Forms


# Spotify Grabber

## HTTP Auth



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