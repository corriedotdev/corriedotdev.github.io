---
layout: post
title: Developing Pixel Arcade VR 
excerpt: "At its launch there were few VR games out there. Anything developed was quickly enjoyed by the smaller but passionate VR playerbase. So releasing a VR title in 2016 was unchartered territory. Pixel Arcade has been for sale since on Steam, Vive Port and has a partnership with Smilegate Stove; Tencents approach at VR arcades for the Korean markets. Enjoy the technical breakdown"
categories: [vr]
comments: true
# image:
#   feature: pixelarcade/icon.png
galleries:
 1:
   -
     - { url: '/img/pixelarcade/1.png', alt: '1'}
     - { url: '/img/pixelarcade/2.png', alt: '1'}
     - { url: '/img/pixelarcade/3.png', alt: '1'}    
 2:
   -
     - { url: '/img/pixelarcade/Badge1.png', alt: '1'}
     - { url: '/img/pixelarcade/Badge2.png', alt: '1'}
     - { url: '/img/pixelarcade/Badge3.png', alt: '1'}
     - { url: '/img/pixelarcade/Badge4.png', alt: '1'}
     - { url: '/img/pixelarcade/Badge5.png', alt: '1'}
     - { url: '/img/pixelarcade/foil.png', alt: '1'}
---

# Pre-face
The idea of this write up is to share the development from start to finish of a VR game in 2018 [Pixel Arcade](https://www.pixelarca.de). The process hasn't changed much and will cover working with publishers, getting a VR game set up in South Korea and supporting it to getting it on Indie Gala.

# Background
After a long summer of "internship duties" at Expedia and Google my free time was mostly wasted by publishers who were FANG employees trying to make a quick buck ([in hindsight I would say lessons learnt about publishing/developing your mobile game independently](https://youtu.be/PHgEReA_8Io)) I was then eager to then release anything other than a mobile game. 
That market is extremely saturated and *still* is to this day a difficult one to profit from. It is one of the more fun products to develop however  as there are a lot of sensors you can take advantage on with a mobile. Cue VR and its array of sensors. 

My approach for mobile development now is to work with Voodoo on small prototypes and they will test the game with users and see if we kit KPI's in order to iterate the prototype or call it a day. Win win for me. I get to make small pretty mobile games, and the marketing and launch has a dedicated team. After leaving my job to start a development studio, I once again got taken advantage of and was contracted to make games that could then be tested with Voodoo. Clearly decided to cut the middle man out and risk no pay to go try it myself. Although I wasn't successful at this time, it was a way to develop, learn and iterate rapidly which lead me to interview and work with awesome game studios around the world. I ended up taking a different developer path however.

Back to Pixel Arcade, I had a years honours project to fill and for me I was always interested in understanding the low level processes on the hardware that the Unity engine utilizes to make a more efficient gaming experience. Optimization strategies for VR seems like a new and relatively unexplored field so I went for that. 4 years later I am now studying a PhD for XR optimization so I am passionate about how to use the most of an engine and optimize its capabilities.

{% include gallery.html  gallery=1 %}


## Finding the Graphic Style
The idea of VR movement was something I found interesting. Locomotion was, and still is a problem in VR. I decided to take an approach after countless experiments on movement in VR and what triggers motion sickness, vection illusion etc and try tackle the locomotion problem myself. Below is a video of a demo that I was inspired to make after trying an experience in "carnivals" where you walk down a straight tunnel that is rotating, causing you to become relatively legless and dizzy. 

The atmosphere style was 80's sythwave inspired with the graphics being minimal enough that I could focus on gameplay and movement mechanics while also being able to run on most VR hardware. No real time was spent on experimenting graphics, this just worked for me. The wave was a fun little script to write and thats how the graphic style for Pixel Arcade was born. From a totally random movement demo and listening to [Vitalic](https://www.youtube.com/watch?v=I2dfGC1oziE) all the time. I saw him live mid development which did help.

<p style="text-align:center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/dtkYv00GdCI" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>

> The above video was a demo that took no effort to design, however ended up inspiring the final game feel

The movement was initially in my head but unsure how to implement. I started getting my own climbing framework created which was lightweight and would work with SteamVR which used the OpenVR api. Eventually stopped this and went to using a heavily modified VRTK framework. This was great for development timescale, however NOT great for future proofing the game. If I want to make Pixel Arcade 2 it will require a rewrite. Frameworks are difficult for me, not due to the learning as I really enjoy seeing demos and getting to understand how it was created. Its more the artistic guilt that you didn't create the feature from scratch. I still have this issue and it hinders my productivity, so I have recently put some cash aside to buy assets from the store to try and overcome this and realise its ok not to code ideas if they have already been done for you.

I am now using VR interaction toolkit as its lightweight, and honestly on par with how I would make many features without using Unity DOTS. Which I have a gripe with in its development, you cant have a break in this industry for a few months or you fall behind and when DOTS comes out I think there will be a few developers scratching their heads with the best practices. Unity have released a DOTS demo however which will likely be used as the base framework for many projects to come. 


### Steam
Steam originally required a developer license to upload games to the store. I can't find the exact figure but was around $100. This was for PC desktop titles, not VR. Here Valve and other companies such as Oculus encouraged developers to adopt VR so it didnt flop, so allowed thoses with a VR prototype to apply and get free access to uploading games to the store.

Cue Greenlight. Another opportunity to release your game twice. One in Beta or however early or late in development you chose (which is why many dont like greenlight games as they are severely underdeveloped and likely trying to asset flip games.) It essentially allowed developers with no timeline to release a playable version of the game, get feedback and iterate until its final release. This is what I did as I had less than 9 months to make a game and release to the store. 

Valve uploading mechanism was easy but did require command line terminals and not a web interface to upload files. Seems an interesting approach but every app store has their niches to upload. Google Play, Apple, Valve, Viveport, Oculus, Smilegate Stove are some of the platforms I have had to create bespoke builds of games for and upload to their own storefront which are all entirely different in processes.

> Here is a screenshot of the first upload to steam.

![Vat]({{ site.url }}/img/pixelarcade/firstbuild.png)
{: .pull-center}


## Cards
Steam also had the new trading card feature which allows you to unlock trading cards and use them to craft Steam profile swag like backgrounds, badges, emojis. The process was fun and creative. You have some requirements to fufill but all in all it was fun and only had one or two changes to make related to not showing text; in my case numbers, on the card graphic itself which makes sense for localisation (kinda, even though Pixel Arcade wasnt really localised, but localised by minimalism in text UI)

{% include gallery.html  gallery=2 %}



## The Release
The release after greenlight had a total of 25 levels. Looking at user stats back when I have google analytics in the game and GDPR wasn't a thing. Which my the way I recall leaving the office early at one of my jobs because "my games arnt GDPR compliant and the law comes into action tomorrow." Of course there was flexibility for small development teams but I hated my job so was excited to go home and tinker on Pixel Arcade. 

The game was released in greenlight, viveport, then indie gala and then smile gate stove in that order. Oculus did sent me hardware to develop for their platform, but I didnt see the point. In hindsight perhaps would have been a good move but I didnt want to port from SteamVR to Oculus for my first VR project. In total sold over 7,000 copies on Steam alone. Now most of the revenue comes from Smilegate Stove which are South Korean VR Arcades. The playtime in minutes has increased over 300% in the past 12 months, so safe to say people are starting to look into VR opportunities to play with friends in that market. I do see a future where people can go out for a meal and rather go to a cinema experience, visit a VR type arcade where they can have a 1 hour experience such as the [Apollo Landing HD]() game which I use to showcase VR to most non gamers. It definitely relates well to older demographics as they recall the landing and growing up with the space race.

![Vat]({{ site.url }}/img/pixelarcade/redditcomment.png)
{: .pull-center}


## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pixel Arcade Steam](https://www.pixelarca.de)


<a href="#" id="emailclick" onclick="replace_email()">My Email</a>

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
1
  window.setTimeout(add_mailto, 100);
}
</script>