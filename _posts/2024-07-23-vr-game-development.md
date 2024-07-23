---
layout: post
title: "PhD to VR Indie Developer, 3 Reasons Why"
excerpt: "Written for gamedeveloper.com, after an evaluation into the state of the VR, it appears VR early adoption phase is coming to an end. From the technical potential and immpressive array of worlds at this years VRKet, quality of VR development frameworks and new research into VR interfaces helping guide player expectations, the recent annoucement of future HMDs from Meta and Google comes as no suprise.."
categories: [VR🥽]
comments: true
image:
  feature: feature/pa-science.jpg
galleries:
 1:
   -
     - { url: '/img/line.gif', alt: 'vr filter'}
 2:
   -
     - { url: '/img/modular/ui.gif', alt: '1'}
     - { url: '/img/modular/pa/3DUI_1.gif', alt: '2'}
 3:
   -
     - { url: '/img/modular/pa/climbing_gif1.gif', alt: 'vr filter'}
     - { url: '/img/modular/pa/climbing2.gif', alt: 'vr filter'}
 4:
   -
     - { url: '/img/modular/pa/portal.gif', alt: 'vr filter'}
     - { url: '/img/modular/pa/portal2.gif', alt: 'vr filter'}
---

## The Problem with VR Interaction
For gamedeveloper.com discussing how PhD UI/UX research lead to the development of an indie VR game. 

The course of the last 3 years I have focused on UI/UX and Optimization techniques in research for VR and AR Devices. To which I feel the VR market, in general, is in a really good position to develop something future proof with longevity for the coming wave of VR headsets and players. The Quest 2 and 3 HMDs boast strong hardware capability able to rival game consoles. One of the common questions around the unique selling points any new technology is what is it going to replace in the players life. Phone? TV? Game Console? PC? There are only so many hours in a day and players have preferences over what technology or game platform they want to spend their time on. 

With this, the quality of games that can now be developed thanks to developer experience and research in VR, we are seeing an immergence in standalone games. A large part of my recently completed PhD was to understand what are the problem spaces faced by the VR gaming industry today from a user perspective and develop solutions based around these. Which resulted in a few key areas of research. 

- What are the accessibility barriers for players when they use VR?

- What is the primary means of interaction in the digital space?

- And to that, how can they be improved?


This post aims to highlight the research I have completed over the past few years in hope it demonstrates why I took the leap of "trust the process" to develop Pixel Arcade, full-time self funded using the new processes discovered. These include three key things, a 3D interface, portals and locomotion.

{% include gallery.html  gallery=1 %}
> Example of a ray based / laser pointer interaction from Half-Life: Alyx

# Exclusive 3D Interface

Every VR title somewhere exploits the laser pointer for interacting with interface elements. One of the key reasons for this is because developers just translated the traditional 2D interfaces into a 3D space without trying to evolve interaction so much. So translating functionality of a traditional cursor to a laser pointer is an obvious evolution. This is where I wanted to consider if there is another general means of interaction we can exploit in VR? Given this, I wanted to use an accessibile first design philosophy to try explore this area where we take consideration for all players needs at the start, and not left as an afterthought.

Improving existing ray-based interaction was also a study focus. To which, a viable solution which takes 10 minutes for VR developers to integrate which has shown promising results and is due to be published soon.  
With the use of a low pass filter like the 1-Euro Filter, we can almost remove these tremors found in every healthy individual to increase engagement and prevent frustration when interacting with 2D UI in VR. My hypothesis is we can reduce symptomatic parkinson tremors with this filter.

Moving into the 3D interface, the Modular 3D interface is designed to empower the player to decide where the interface is positioned. 

{% include gallery.html  gallery=2 %}
> Panels with borders which act as buffer zones to prevent interacting with UI componenets attached

# No Loading Screens, Only Portals

This was only theorized and was in the future-work section of my PhD thesis. However I now have a solution working that is using something that has an acroymn of AAAS. Asyncrhonous, Additive, Addressable Scenes. Its just a combination of level loading techniques put together to make a seamless gaming experience exploiting RAM useage over GPU (when done correctly). 

The technicals of this are specific to the game, but a key reason why people play VR over traditional mediums is for immersive properties and having anything immersion breaking could be just the thing that makes the player take off the HMD. 

{% include gallery.html  gallery=4 %}

# Best locomotion for gameplay

"Best" locomotion for is absolutely subjective, but lets consider the locomotion problem at the heart of the discussion. Players who dont have their VR legs yet are prone to locomotion sickness when using the joystick to navigate smoothly around VR. I've had feedback from players stating it almost feels like youre constantly in an icerink, and suspect this reaction or response is partially to do with this, beyond the standard vestibular occular reflect disconnect that research points towards (brain thinks we are in motion but are not). The other form of movement is teleportation, to what can be described as a magical locomotion strategy. 1:1 Playspace tracking is a high-fidelity interaction medium where we can use real world walking / motion to translate positioning in the game space. To consider another form of interaction, everything else is magical. 

Enter climbing locomotion! I originally discovered this in 2017 during my undergrad where I wanted to explore with various VR SDKs and fell inlove with climbing as a medium to solve the locomotion problem. Although flawed and needed adjustment (enter the PID controller), the ability to use gravity and climb around was just a moment of magic. I still dont quite understand why it feels so natural as we dont ever throw ourselves around objects, but our ability to predict where we will land is suprisingly organic as far as learning curves go. I have put people who dont play video games into Pixel Arcade Legacy but they are able to climb around like a natural born gamer.

It is for this reason, as a unique game mechanic (although gorilla tag and climbey come to mind that also use climbing of sorts)  that pixel arcade is entirely physics based. The lessons learnt through developing a 3D interface that relys on the physics engine pushed me towards this. Event loops are almost non existant beyond the players start and end game loop. What i mean by this is that every object in the game world responds to physics, meaning beyond item pick up, the world is running on its own where the players actions have consequences. Such as grabbing a moving object, being pushed off the ledge.. all common game design mechanics but to take the physics engine as president over just simply moving a game object with collision has implications critically impacting player speed.

{% include gallery.html  gallery=3 %}



## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pre-Print VR Tremor Reduction](https://arxiv.org/abs/2405.07335)
* [VR Tremor Reduction GitHub Repo](https://github.com/corriedotdev/vr-tremor-reduction)
* [3D Modular Interface Paper](https://link.springer.com/chapter/10.1007/978-3-031-35634-6_2)
* [3D Modular Interface GitHub Repo](https://github.com/corriedotdev/vr-modular-3d-gui)


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