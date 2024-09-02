---
layout: post
title: "Pixel Arcade VR - Demo Oct 14th Steam Next Fest"
excerpt: "Written for gamedeveloper.com. From the technical potential and immpressive array of worlds at this years VRKet, quality of VR development frameworks and new research into VR interfaces helping guide player expectations, the recent annoucement of future HMDs from Meta and Google comes as no suprise.."
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

<iframe src="https://store.steampowered.com/widget/2603560/" frameborder="0" width="646" height="190"></iframe>

## The Problem with VR Interaction
For gamedeveloper.com discussing how PhD UI/UX research lead to the development of an indie VR game based on the findings. 

The course of the last 3 years I have focused on UI/UX and Optimization techniques in research for VR and AR Devices. To which I feel the VR market, in general, is in a really good position for the development of high quality immersive experiences, future proof with longevity for the coming wave of VR headsets and players. The Quest 2 and 3 HMDs boast strong hardware capability able to rival game consoles. One of the common questions around the unique selling points any new technology is what is it going to replace in the players life. Phone? TV? Game Console? PC? There are only so many hours in a day and players have preferences over what technology or game platform they want to spend their time on. A key barrier to access is, well, accessibility. Many users will have a cognitive accessibility constraint when placed in a virtual environment they are not familiar with, resulting in a learning curve to understand how the UI works. Additionally, the means of interaction may not cater to all users with temporary accessibility constraints such as broken limbs or more common, benign essential tremors.

With these points taken into consideration, the quality of games that can now be developed thanks to developer experience and research in VR, we are seeing an immergence in standalone games. This growth is also largely due to the reduction in HMD (Head-Mounted Display) costs, which has made VR more financially accessible. A large part of my recently completed PhD was to understand what are the problem spaces faced by the VR gaming industry today are from a player perspective and develop solutions based around these. Which resulted in a few key areas of research. 

- What are the accessibility barriers for players when they use VR?

- What is the primary means of interaction in the digital space?

- And to that, how can they be improved?


This post aims to highlight the research I have completed over the past few years in hope it demonstrates my convinction in the results and why I took the leap of "trust the process" to develop Pixel Arcade, full-time self funded using the research. These include three key areas, a 3D interface, portals and locomotion.

{% include gallery.html  gallery=1 %}
> Example of a ray based / laser pointer interaction from Half-Life: Alyx

# Exclusive 3D Interface

Every VR title somewhere exploits the laser pointer for interacting with interface elements. One of the key reasons for this is because developers just translated the traditional 2D interfaces into a 3D space without trying to evolve interaction so much. So translating functionality of a traditional cursor to a laser pointer is an obvious evolution. This is where I wanted to consider if there is another general means of interaction we can exploit in VR? Given this, I wanted to use an accessibile first design philosophy to try explore this area where we take consideration for all players needs at the start, and not left as an afterthought.

Improving existing ray-based interaction was also a study focus. To which, a viable solution which takes 10 minutes for VR developers to integrate which has shown promising results and is due to be published soon but source code and demos are available on GitHub so you can start reducing tremors in VR for your next release.  

All of us have benign essential tremors, you may notice these shakes in VR when you are selecting an item in a menu using a laser pointer. Some tremors are exaggerated due to the tracking of controllers or hand tracking techniques when using vision. These can be system signal noise or, essential tremors. Between the range of 4-12Hz we have psychotic tremors (sometimes refferred to as essential tremors). Some tremors have a high frequency but a low amplitude resulting in them barely being noticable. Unlike parkinsons tremors where the high amplitude often makes them much more obvious. My hypothesis is we can reduce symptomatic parkinson tremors with this filter as well.

With the use of a low pass filter like the 1-Euro Filter, we can almost remove these tremors found in every healthy individual to increase engagement and prevent frustration when interacting with 2D UI in VR. We can also use this filter during any 3D interaction in VR, as the filter is lightweight and has a delta cut off where the filter is disabled during fast velocity hand movement and only enabled for fine control. My hypothesis is we can reduce symptomatic parkinson tremors with this filter.

With an improvement to existing VR interface, I wanted to explore a more natural means of interaction where we can reduce the barrier to access by using our propriception ability, which is our understanding of 3D space. By developing a 3D interface we can empower the player to decide where the interface is positioned preventing an ablist mindset, where player ailments that may have been overlooked during development.

{% include gallery.html  gallery=2 %}
> Panels with borders which act as buffer zones to prevent interacting with UI componenets attached

# No Loading Screens, Only Portals

This was only theorized and was in the future-work section of my PhD thesis. However I now have a solution working that is using something that has an acroymn of AAAS. Asyncrhonous, Additive, Addressable Scenes. Its just a combination of level loading techniques put together to make a seamless gaming experience exploiting RAM useage over GPU (when done correctly). 

The technicals of this are specific to the game, but a key reason why people play VR over traditional mediums is for immersive properties and having anything immersion breaking could be just the thing that makes the player take off the HMD. 

{% include gallery.html  gallery=4 %}

# Best locomotion for gameplay

"Best" locomotion for is absolutely subjective, but lets consider the locomotion problem at the heart of the discussion. Players who dont have their VR legs yet are prone to locomotion sickness when using the joystick to navigate smoothly around VR. I've had feedback from players stating it almost feels like youre constantly in an icerink, and suspect this reaction or response is partially to do with this, beyond the standard vestibular occular reflect disconnect that research points towards (brain thinks we are in motion but are not). The other form of movement is teleportation, to what can be described as a magical locomotion strategy. 1:1 Playspace tracking is a high-fidelity interaction medium where we can use real world walking / motion to translate positioning in the game space. To consider another form of interaction, everything else is magical. 

Enter climbing locomotion. I originally discovered this in 2017 during my undergrad where I wanted to explore with various VR SDKs and fell inlove with climbing as a medium to potentially solve the locomotion problem. Although flawed and needed adjustment (enter the PID controller), the ability to use gravity and climb around was just a moment of magic. I still dont quite understand why it feels so natural as we dont ever throw ourselves around objects, but our ability to predict where we will land is suprisingly organic as far as learning curves go. I have put people who dont play video games into Pixel Arcade Legacy and they are able to climb around like a natural born gamer.

It is for this reason, as a unique game mechanic (although gorilla tag and climbey come to mind that also use climbing of sorts) that Pixel Arcade is entirely physics based. The lessons learnt through developing a 3D interface that exclusively relies on the physics engine pushed me towards this. Event loops are almost non existant beyond the players start and end game loop. What I mean by this is that every object in the game world responds to physics, meaning beyond item pick up, the world is running on its own where the players actions have direct consequences to the environment. Such as grabbing a moving object, being pushed off the ledge.. all common game design mechanics but to take the physics engine as president for interaction over just simply moving a game object with collision has implications, critically, impacting player speed and therefore progression.

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