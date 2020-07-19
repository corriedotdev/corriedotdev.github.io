---
layout: post
title: Low-rate Picture Transmission from Weather Satellites 1
excerpt: "Hacking radios leads to taking the ultimate picture from weather satellites."
categories: [Satellites]
tags: [satellites,rtl-sdr]
comments: true

---

# What

# Hardware
 HRPT at a 30 degree the Meteors look out the question, GOES 13 is 25.4.. Appreciate a proof read to check my sanity.  I would love to try get an image from GOES 16  and then try a Meteor M2 if the initial GOES 16 test works. But doubtful as noted SO NOAA 15 looks like my best bet due to polar orbits.

1. [Antenna][1] - Undecided here but thinking of a v-dipole initially as the kit that the RTL-SDR comes with linked below does have the basic antenna and i can 3D print the mount to create a V-Dipole if needs adjustment. Should get 137mhz. Can get some galvanised wire alternatively and cut to spec alternatively.
2. [SAWBird Filter][2] I need advice here as i am unsure on 1430hz or what purpose this is exactly (in my reading material). In lament terms is this going to clean the signal and support removing / preventing noise? Confused as to the set up here, under the impression is it exclusively hardware and no software required.
3. [RTL-SDR Blog V3][3] - This is the official v3 and comes with some essentials to get started, will just connect to the local radio freq and maybe try hack garage open or something initially (6 minutes apparently to break any 8 bit key which is cool)
Software will be [wxtoimg][4] to decode the signal to image and [SDR Sharp][5] to "record" and complete the DSP.

[1]:https://www.thingiverse.com/thing:4234647
[2]:https://www.amazon.co.uk/NooElec-SAWbird-H1-Barebones-Applications/dp/B07XJLKQDN/ref=sr_1_3?dchild=1&keywords=sawbird+filter&qid=1595027782&sr=8-3
[3]:https://www.ebay.co.uk/itm/RTL-SDR-Blog-V3-original-RTL2832U-1PPM-HF-BiasT-SMA-Dongle/324123706220?epid=15022750294&hash=item4b7747436c:g:7QIAAOSwoJxbdvkq
[4]:https://wxtoimgrestored.xyz/
[5]:https://www.pe0sat.vgnet.nl/sdr/sdr-software/sdrsharp/


## Further Reading
* [Hacking Radio](https://www.youtube.com/watch?v=1RipwqJG50c)
* [Reference Photo](https://preview.redd.it/d47sz11wrbb51.jpg?width=4032&format=pjpg&auto=webp&s=f821115044400eadc1baec8132fb3e63a318a50d)
* [Sat Wiki](https://www.satwiki.info/index.php?title=Getting_started)

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