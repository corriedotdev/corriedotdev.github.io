---
layout: post
title: "Modular 3D Interfaces for Accessible VR Applications"
excerpt: "Published in Springer Nature VR Book, im going to go over the main points of the framework Ive developed so you can create a UI that supports an accessible first design approach while also supporting multimodal input, future proofing your UI for all input mediums."
categories: [VR🥽,Publication📕]
comments: true
image:
  feature: feature/11.jpg
galleries:
 1:
   -
     - { url: '/img/modular/ui.gif', alt: '1'}
     - { url: '/img/modular/panel.PNG', alt: '2'}
 2:
   -
     - { url: '/img/modular/yove.gif', alt: '3'}
 3:
   -
     - { url: '/img/modular/new.PNG', alt: '4'}
---

## Intro
The paper has been published in Springer notes which can be found [here](https://link.springer.com/chapter/10.1007/978-3-031-35634-6_2) the pre-print is available [here](https://arxiv.org/abs/2304.10541). This page will cover the basics of the system to allow you to integrate into your own projects. I would recommend watching the youtube video, which is a more "entertaining" version of the presentation I did at HCI International 2023. 

<p style="text-align:center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/3NhJOPAUMCs" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
</p>

## Key Features
Existing interfaces are not, if ever, designed with accessibility in mind. It's a difficult thing for developers to implement as its not clear on exactly what makes a design accessible. This interface has been developed with an accessible first design philosophy, aiming to remove this responsibility from the developer allowing for a multimodal input approach allowing users to select their preferred input mechanism whilst also providing support for relocating the positions of UI elements. 

- Free-floating allows for adjustment in 6-DOF for users with specific viewing angle requirements and allows for anchored placement in 3D space.

- Contextual, allowing elements to only be displayed when relevant to the location in the environment resulting in;

- Predictable task-focused interactions, using skeuomorphs and colors around 3D interface trims in designated context zones

## Demo Download 
The [Github repo](https://github.com/corriedotdev/vr-modular-3d-gui) you can download various demonstrations of the application. You can integrate this into your project by creating a panel with a border that allows for grabbable interactions. The 

{% include gallery.html  gallery=3 %}

> Point cloud, video, photogrammetry and GIS dataset visualisation with custom placement for UI 

{% include gallery.html  gallery=1 %}

> Panels with borders which act as buffer zones to prevent interacting with UI componenets attached

{% include gallery.html  gallery=2 %}

> The panels are kinematic and work with the physics engine allowing for static placement but also interact with the envionment


## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pre-Print](https://arxiv.org/abs/2304.10541)
* [Springer Paper](https://link.springer.com/chapter/10.1007/978-3-031-35634-6_2)
* [Youtube Video](https://youtu.be/3NhJOPAUMCs)
* [GitHub Repo](https://github.com/corriedotdev/vr-modular-3d-gui)


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