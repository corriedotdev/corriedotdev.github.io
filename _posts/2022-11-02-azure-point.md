---
layout: post
title: Download - Point Cloud Realtime Player & Clothing Demo
excerpt: "The application streams the azure kinect once ran as admin using vfx graph. Its effect is voxel with volumetric lighting in real time. Allowing for camera to be panned around viewing the subject in full 360. Just a tech demo, similar to brain dance from cyberpunk. Also shared a small demo I made for changing clothing using the kinect. Simple but may give insight."
categories: [Download🔻]
comments: true 

---

# Point Cloud
Please download from the link below and extract to get running. Pre-req is an Azure Kinect DK and to run it as an admin. The folder is zipped with .7z


<!-- 
![JWT Screen]({{ site.url }}/img/kinect.png)
{: .pull-center} -->

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Real time volumetric lighting with azure kinect <a href="https://twitter.com/hashtag/unity?src=hash&amp;ref_src=twsrc%5Etfw">#unity</a> <a href="https://t.co/ZrWXn7PkVx">pic.twitter.com/ZrWXn7PkVx</a></p>&mdash; Corrie (@corriedotdev) <a href="https://twitter.com/corriedotdev/status/1501587367823650816?ref_src=twsrc%5Etfw">March 9, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

<div markdown="0"><a href="{{ site.url }}/releases/Kinect_Realtime_Voxel.7z" class="btn btn-success" download >Download</a></div>

# Clothing Demo
Please download from the link below and extract to get running. Pre-req is an Azure Kinect DK and to have the pre-req which are highlighted in yellow. Video demo of that [here](https://www.youtube.com/watch?v=PGsxP6Yoq9I&t=1s) .


> DLL's required are in filelist.txt at the relevant dir


- Body Tracking SDK 1.1.0
- Kinect SDK 1.4.1

![JWT Screen]({{ site.url }}/img/clothing.png)
{: .pull-center}


<div markdown="0"><a href="{{ site.url }}/releases/Kinect_clothing_demo.zip" class="btn btn-success" download >Download</a></div>




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