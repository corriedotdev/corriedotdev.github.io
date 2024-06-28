---
layout: post
title: "Download & Experience the VR Interface here"
excerpt: "Download the PC and Quest Standalone experience of YOVE. A very small single world experience that showcases some VR experiments completed during the PhD. Launch a rocket too. Your Own Virtual Environment"
categories: [VR🥽, Download🔻]
comments: true
image:
  feature: feature/13.jpg
galleries:
 1:
   -
     - { url: '/img/yove-vr.png', alt: '1'}
---

## Intro
The experience showcases;
A short video player with a blur effect for the screen. The Slider is a placeholder for something I havent integrated yet. Launch a Saturn V rocket. See why filters are great at improving accuracy. The controller will flick a little and I havent adjusted values entirely but you will get to experience ray input with a 1-Euro Filter enabled. You can also see a simple implementation of a reference frame to help VR players find points of interest. 

> Its an offline application in both builds.  

<video id="videoElement" width="720" height="480" playsinline autoplay muted loop>
      <source src="{{ site.url }}/img/yove-vr.mp4" type="video/mp4">
      Your browser does not support the video tag.
</video>
### PC Steam VR 
Download the PC VR Compatable experience below.

<div markdown="0"><a href="https://drive.google.com/file/d/12H8ig6VHB-xfK5jMU2KUZYuKxU-UOFOu/view?usp=sharing" class="btn btn-success" download >Download PCVR</a></div>

### Quest APK 
Download the Quest Pro and Quest 2 compatable .apk. Ensure you have download from trusted sources enabled. 

<div markdown="0"><a href="https://drive.google.com/file/d/1a3d-kjpbjUMr74AmUbnhwgbjU7NUtXv4/view?usp=sharing" class="btn btn-success" download >Download Quest</a></div>


{% include gallery.html  gallery=1 %}


## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pre-Print](https://arxiv.org/abs/2304.10541)
* [Springer Paper](https://link.springer.com/chapter/10.1007/978-3-031-35634-6_2)
* [Youtube Video](https://youtu.be/3NhJOPAUMCs)


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