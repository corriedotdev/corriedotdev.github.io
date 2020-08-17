---
layout: post
title: Low-rate Picture Transmission from Weather Satellites 1
excerpt: "Watched a really cool video on an attack on a garage door by reverse engineering the radio transmission from the fob. I am now looking at taking real time photos from weather satellites."
categories: [Satellites]
comments: true

---

# What

# Hardware
 HRPT at a 30 degree the Meteors M2 look out the question, GOES 13 is 25.4.. Would love to try get an image from GOES 16  and then try a Meteor M2 if the initial GOES 16 test works. But doubtful as noted SO NOAA 15 looks like my best bet due to polar orbits.

1. [Antenna][1] - Thinking of a v-dipole initially as the kit that the RTL-SDR comes with linked below does have the basic antenna and i can 3D print the mount to create a V-Dipole if needs adjustment. Should get 137mhz. Can get some galvanised wire alternatively and cut to spec alternatively.
2. [SAWBird Filter][2] I am unsure on 1430hz or what purpose this is exactly (in my reading material). In lament terms is this going to clean the signal and support removing / preventing noise? Confused as to the set up here, under the impression is it exclusively hardware and no software required..
3. [RTL-SDR Blog V3][3] - This is the official v3 and comes with some essentials to get started, will just connect to the local radio freq. Link in further reading is great to see an experiment in recording device radio waves from garage doors etc. 500 kHz to 1.7 GHz

# Software 

Will be [wxtoimg][4] to decode the signal to image, make sure the beta install is used. Ran msi exec in cmd to see what the issue was and not going to bother debugging. Beta worked first time.

[SDR Sharp][5] to "record" and complete the DSP.

[Orbitron][6] will automatically configure the tuning and timing of satellites in SDR Sharp. Needs to be ran with compatibility for XP SP2 though

ZADiag will install the correct drivers for the rdl str dongle but inside the installer for SDR Sharp this is bundled with a version (may be out of date but works)

VB Cable for Xtoimg

[1]:https://www.thingiverse.com/thing:4234647
[2]:https://www.amazon.co.uk/NooElec-SAWbird-H1-Barebones-Applications/dp/B07XJLKQDN/ref=sr_1_3?dchild=1&keywords=sawbird+filter&qid=1595027782&sr=8-3
[3]:https://www.ebay.co.uk/itm/RTL-SDR-Blog-V3-original-RTL2832U-1PPM-HF-BiasT-SMA-Dongle/324123706220?epid=15022750294&hash=item4b7747436c:g:7QIAAOSwoJxbdvkq
[4]:https://wxtoimgrestored.xyz/
[5]:https://www.pe0sat.vgnet.nl/sdr/sdr-software/sdrsharp/
[6]: http://www.stoff.pl/

## First attempt

Correct IQ should be set. 
Test on FM first
Coax cable too tight around sdr
Windows Direct Sound Virtual Cable

## Third
multiplier set to 40

## Further Reading
* [Hacking Radio](https://www.youtube.com/watch?v=1RipwqJG50c)
* [Reference Photo](https://preview.redd.it/d47sz11wrbb51.jpg?width=4032&format=pjpg&auto=webp&s=f821115044400eadc1baec8132fb3e63a318a50d)
* [Sat Wiki](https://www.satwiki.info/index.php?title=Getting_started)
* [Two-line element coordinate system](https://spaceflight.nasa.gov/realdata/sightings/SSapplications/Post/JavaSSOP/SSOP_Help/tle_def.html)
* [Unidentified Noise](https://www.sigidwiki.com/wiki/Signal_Identification_Guide)




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