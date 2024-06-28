---
layout: post
title: Pixel Arcade and Find Poly
excerpt: "Pixel Arcade was released in 2016 and I have been looking at making a multiplayer sequel for some time now and my love for casual mobile games has now resulted in the IP I previously mentioned called Find Poly! Check out some development previews inside."
categories: [VR🥽]
comments: true 
image:
  feature: feature/pixel.jpg
galleries:
  1:
   -
     - { url: '/img/ic.png', alt: '1'}
     - { url: '/img/portal.png', alt: '1'}
     - { url: '/img/in.png', alt: '1'}     

  2:
   -
     - { url: '/img/vfx.gif', alt: '1'}
     - { url: '/img/electric.gif', alt: '1'}
     - { url: '/img/cubes flicker2.gif', alt: '1'}
  3:
   -
     - { url: '/img/find1.gif', alt: '1'}
     - { url: '/img/find2.gif', alt: '1'}
     - { url: '/img/find3.gif', alt: '1'}

---

# Pixel Arcade
The original game is now titled "Pixel Arcade Legacy" on Steam. Released to VR Arcades in south korea, this game still has an active player base and I personally love the game. You will now get to experience an entire codebase revamp, supporting 3D interface elements for VR and support on Quest stand alone. 

The game is set in neon cyber space, with a new NPC called "Neon". They will help and guide you through the levels. The games premise is the same as the original, climb and vault your way through the vertical platform envionment to get your best score and time. Its a calorie burner and stimulating experience for VR where you defy gravity with the coolest locomotion mechanic to hit VR, vaulting. There are new powerups such as a launch pad and the opportunity to play in multiplayer. The game will be release on Oculus first, then can see what the PC port looks like. I suspect a phased launch where multiplayer will come in time. 

Portals are also used so NO LOADING SCREENS!

{% include gallery.html  gallery=1 %}

<p style="text-align:center;">
<video id="videoElement" width="720" height="480" playsinline autoplay muted loop>
      <source src="{{ site.url }}/img/teaser.mp4" type="video/mp4">
      Your browser does not support the video tag.
</video>
</p>


{% include gallery.html  gallery=2 %}

# Find Poly
Having developed for the hyper casual market in the past, it was long over due to get a new title released to mobile that contains all my development efforts in this market area. Find poly will be multiplatform, after the mobile launch. Your task is to locate the characters or objects in a fully immersive 3D world where characters interact with the enviornment and have discussions roaming the level. Difficulty will scale based on the complexity of the environment but its mainly an exploration game where you can enjoy small 3D levels that I relish designing once the code base is complete. Again to theme with my hate for loading screens its a nice little async system developed that should keep you interested during load times if you even notice them.

- Interactive
- Cozy chill game, passive
- Minimal UI
- Fun

The idea is to be able to make fun creative enviornments as level design into the future. Id like this to be such a polished core code base and release to the public for decades to come with new content.


{% include gallery.html  gallery=3 %}

## Monetization
I want this to be the first true multiplatform game. NO IAPS. Its a live service based game where you should play the game without paying or needing ads. However I am still working this out, to prevent piracy ads are a good angle but I will only allow this if the player wants to watch a video and be rewarded with some bonus gems which will allow you to customize your characters home environment, were props and have a variety of assets to ineract with. Such as sitting down reading a newspaper, playing with a ball, speaking to other AI characters. The idea here is that "poly" in your home base menu will gradually become more and more sentient and you can interact and engage with it, think of a tamagotchi! 

This game isnt a techncially difficult game, but the fundementals of game design, optimization and monetization are areas I wanted to prove I could implement. In addition, the real technical aspect of development is thinking of a monetization structure that will allow the game to be played on all platforms Mobile, PC, Switch and VR. To which im thinking of a first person find the character game or a mixed reality experience where you look at a table in your real world and pick the character up so you that you are trying to locate. 


### When?
This is not my full time gig so can only work on these when my creative itch is needing scratched, which is mostly on Sundays where I even have considered streaming the development on Twitch. So expect years before you see anything, especially with my thesis Audio book adaptation taking my Sundays up just now.


## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pixel Aracde 1](https://store.steampowered.com/app/618570/Pixel_Arcade_Legacy/)


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