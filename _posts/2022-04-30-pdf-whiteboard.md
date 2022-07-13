---
layout: post
title: All in One PDF Whiteboard Note App
excerpt: "Developed before I started my PhD to support in understanding research topics from no knowledge to eventually having something comprehensible on paper. Haven't updated it since 2021 but used it every week. The format projects are saved to will be supported in future releases. I will discuss this here. "
categories: [code 👨‍💻]
comments: true
---

# The short and sweet of it..
Version 4 can be downloaded below. To use just start annotating on the whiteboard and save to location. If you want to add a .pdf document just drag and drop it onto the page. Give it a few seconds to load (there is no progress bar or beach ball indicator I am aware) and the pdf will be imported. Use the buttons in the corner to remove pdf documents and add in another. They will overlap! Be sure to clear documents before adding in another. I will raycast the documents so in future you could have a massive "mind map" of relevant documents to share with students. 

This is a personal project, I will release open source when I can polish it more. I dont have time. Feel free to spread the word if you find it useful to motivate me to finish it at somepoint.

<div markdown="0"><a href="{{ site.url }}/releases/PDF_Whiteboard_v4" class="btn btn-success" download>Download PDF Whiteboard v4 Here</a></div>

<p style="text-align:center;">
<iframe width="560" height="315" src="https://www.youtube.com/embed/tGRqaxVygio" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</p>
## Further Reading
Check out the following links for inspiration and further reading about this topic
* [More of my free software](https://corrie.dev/articles/2021-12/games)



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