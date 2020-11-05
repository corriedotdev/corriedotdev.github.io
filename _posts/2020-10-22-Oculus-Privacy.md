---
layout: post
title: Privacy in Oculus VR is Dead and it's going to get worse.
excerpt: "Oculus have updated their privacy policy to align more with their parent company Facebook. Almost every action you make is linked back to your official Facebook account ID, and forget using an online persona, if caught with an online alias your new Quest 2 headset is now a £300 paper weight.

Meta data isn't meta if you are recording everything on separate applications."
modified: 2013-05-31
categories: [Privacy]
tags: [privacy, oculus, facebook, vr]
galleries:
 1:
   -
     - { url: '/img/oc-fitbit.PNG', alt: 'facebook-fitbit'}
 2:
   -
     - { url: '/img/oc-process.PNG', alt: 'info'}
 3:
   -
     - { url: '/img/oc-device.PNG', alt: 'device'}
 4:
   -
     - { url: '/img/asda-self.PNG', alt: 'asda'}
---

# Opening Statement
Before reading I would like to note that there are some statements here that are speculative and these will be marked as such. Otherwise all information was gathered from official websites and supporting documentation. Assumptions include how Oculus may be tracking users interiors in the future to enhance their AR experience plans based of their 2020 Facebook Connect event. I also must note that some of the language used here is more on the edgy sides of my posts. We are human. We swear from time to time when surprised by something and in this case I was naturally shocked at some of the findings. I am not an advanced writer who can convey extreme senses of emotion 

## Updated Oculus Policy

On the 11th of October 2020 their policy was updated. The delta between 10th and the 11th isn't significant and honestly Oculus quest requires a Facebook account to even get onto the Quest 2 device which officially started shipping on the 14th of October When you launch the headset up for the first time it requires an online connection and then you must sign into your 'official' Facebook account. You are allowed to play offline after this moment, but [forums online](https://www.reddit.com/r/oculus/comments/iv0yex/using_oculus_offline_avoiding_data_collection/) came to the same conclusion I did and that is the Quest will pool your user movements and other data into a queue for when you connect online again.

## Use Cases of Data Management
So I don't have Instagram, nor an active Facebook account as such. It contains some friends and a now empty wall after an online purge. It is however using my real name and not an alias so any data collected by Facebook & Oculus can now be linked back to this profile, acting as a primary key for any other meta data collected by themselves and their partners.

I have first hand experience with data processing from companies like Facebook, and the processing that is handled behind the scenes. Not all information is hashed or encrypted for a start. However I want to start on a scenario where data acquisition is good, there are of course many advantages but an insight to how mobile games and games in general use analytics will set the stage as to why Oculus may now be collecting too much. 

When a game is released to beta and players inevitably get stuck at a specific level, I have no way of knowing until I get an email saying "please help the game is busted" to which I respond "get good." when in reality after a few emails I will investigate the issue. [Unity Remote settings](https://blogs.unity3d.com/2017/06/02/introducing-remote-settings-update-your-game-in-an-instant/) allows for changing specific game variables on the fly without recompiling a new apk for executable, therefore speeding up an issue to resolution (also great to enabling seasonal events or 2xp days). Using data gathered exclusively in game from player actions like time taken to pass a level, their health after a boss fight, what equipment they have out at a specific point, how much coin they have etc. All of this meta data is good for the developer to tailer the experience to how they imagine it.

[Game Analytics](https://gameanalytics.com/docs/item/unity-sdk) however is an example of an SDK which you integrate into your application, this which is what a "Partner" is. When a privacy policy says "shared with our partners" this is what it often means. Where a third party stores and data provided from Facebook on a specific users online habits which will then be passed onto the aforementioned partner which will then lead to something like targeted advertisements.


# I Requested all my Oculus data
You can request information stored by Facebook specifically, but the focus of this discussion is Oculus.. as they have the power to record a whole lot more with their proprietary hardware containing 180 cameras, mics and operating system. Its absolutely terrifying. After visiting their [privacy centre](https://secure.oculus.com/my/privacy/#view-your-information)) you can view information stored in a nicely formatted webpage without having to download anything. Here we see some basic information that we expect such as name, email, last log in time and what apps and games you've played and viewed. However there was one section that caught my attention. "*Information About your devices.*"

{% include gallery.html  gallery=3 %}

It contains a a list of my oculus VR headsets and the computers running oculus home or that have done in the past. I selected CJG-Laptop which is my daily runner and was greeted with a message saying when a device was last synced to the machine. Now when I clicked it was in the afternoon and I had not touched the VR headset nor plugged it into the system in over 24 hours. I checked the time to see 0600 was the last sync time. How was this possible? There was nothing in the system tray to say oculus home is running, so I checked task manager and lo-behold we have a service that is running even when Oculus Home is closed. This must have been syncing to the oculus servers at 6am.


{% include gallery.html  gallery=2 %}

I wasn't happy about this, and found in some more forums of people who were disabling write access to a specific log directory in %appdata% so I need to investigate this. My initial reaction after searching was the logs there are ok and just basic system stuff. Regardless I was unaware my machine was syncing to the oculus servers when I am not even using Oculus Home or a VR device. 

I then downloaded my data to see if there was any additional information that was not being displayed in the website. To my surprise there was a lot more in there. All files were in html and a lot seemed to be items you have in your virtual home but there was also a json file which contained everything. I threw this into a parser app in C# to get a better understanding.

Most alarmingly plain text chat messages appeared in the downloaded archive of information that I requested but not in the link found [here][] which is linked in a more "user friendly interface" and more convenient than parsing json and reading through random .html files.. Giving us data in the form of shitty webpages wont work with computer dorks cunts. 


**They have all the conversation history from chats in plain text** 
{: .notice}

I have since reached out to Oculus privacy team and asked if this is ever encrypted or are all conversation windows stored in plain text, meaning facebook have access to this meaning they can literally target ads from your chat windows. I want to know if the mechanism for chat here works the same as facebook messenger, which I will admit I still use. 


## Facebooks AR Vision
Back in [2016 a reddit user u/OculusHomeHacker](https://www.reddit.com/r/oculus/comments/4ddj1g/what_oculus_network_traffic_contains/)) de-compiled Oculus Home to look at the data which is being fed out the Oculus Home app and came to the conclusion that there was no personally identifiable information being sent.. Well the irony is in 2020 when you now are forced to log into a fucking Facebook account to use an Oculus device which will use data fusion on all the different companies that Facebook own about you then you have a tonne of information and often personal information about you.

[Banning users for using an account with a fake name](https://www.theverge.com/2020/10/15/21518194/oculus-quest-2-headset-facebook-account-suspension-problems#:~:text=The%20Quest%202%20is%20the,with%20a%20separate%20Oculus%20account). If you don't want an online presence then you're shit out of luck because Facebook want everything collected to your account including your location, height, VR play space, hand size, audio recordings, camera access, browsing history.. the list is infinite at this point and incredibly creepy.

So is it just for advertisements? Probably eventually, but I am confident they are slowly transitioning into a data mine field for their upcoming AR glasses which will in some form likely display ads or sell products to you. This is speculative. Data is required to support effective development of AR glasses, cameras provide real time data but require processing power and are intrusive. Processing wirelessly with 6Ghz routers coming out now is likely the way forward for interior AR and with 5G coming for mobile it makes sense that more processing capability can be offloaded to the cloud. Now Oculus have released a headset with all the sensors mentioned above, they have free testers or data miners to record their [inside environment](https://www.youtube.com/watch?v=JTa8zn0RNVM) and daily life duties to support development of features like assistance when navigating or finding an item in the real world you may have forgot where it was placed but the AR capable hardware can direct you to. Facebook connect announced more information of this but [Facebook Aria](https://venturebeat.com/2020/09/16/facebook-will-release-its-first-ar-glasses-in-2021/) is exclusively for research and data gathering for the support of AR development. So gyroscope, cameras and mics including eye tracking are all recording from a users app on their phone. Well.. all I will say is that Oculus just released Quest 2 which just go happens to have cameras and mics along with mandatory Oculus app installation. This is highly speculation but I dont see why Facebook can't use or get away with using consumer grade data tracking for an unreleased product or invention even.

## Monopoly Market

[Valve](https://valvesoftware.github.io/steamvr_unity_plugin/articles/intro.html) have arguably the best VR development SDK from a developers perspective. SteamVR Support is almost mandatory to prevent isolated development for each VR headset, and the Unity / Unreal plugin support with controller messaging already out the box, its a no brainer in many cases. I will personally use SteamVR api for a project and worry about specific ports thereafter such as Quest 2 mobile. The attraction to the Valve index is its high fidelity desktop capabilities, but also because Valve have been doing this for a while and their support for games on the steam store is large. Steam VR has growing rates with [2% of their total player base](https://www.roadtovr.com/steam-survey-vr-headset-growth-august-2020/) recently recorded months after their flagship title Alyx.

The thing is its expensive, and requires a desktop computer. Oculus released the rift, then the Go which was a first for an all in one headset that didn't require a PC (not including the Samsung gear) it was all android processing. This was later canceled and the Quest 1 released, showing a product development trend over time to all in one wireless headsets. This cuts prices down for user adoption, and with linking back to their Facebook account directly along with the release of their [new cloud gaming experiences](https://www.theverge.com/2020/10/26/21528438/facebook-cloud-gaming-beta-android-web-jason-rubin-interview) its clear there is now a more prominent trend towards facebook gaming over recent years and may have started with the acquisition of Oculus. 

Facebook have been sued in the past over their use of data with cambridge analytica but the IPO only sued them for $500k which is nothing to Facebook and I get the impression its not going to deter them in the future should they process users information unlawfully or without good cause. Which leads onto my next comment.


**So they have your exact longitude & latitude location, height, friends, interior design choices, appearance, gender, birthday could you imagine if they had access to your biometrics?** 
{: .notice}

{% include gallery.html  gallery=1 %}

### Right to Object to Data Collection & Processing
I emailed them with a list of objections and questioned why chats in plain text were deemed necessary. I will update here when I hear back from the privacy team or an updated report to the IPO.

* [Right to Object the use of your data](https://ico.org.uk/your-data-matters/the-right-to-object-to-the-use-of-your-data/)
* [Statement on an agreement reached between Facebook and the ICO](https://ico.org.uk/about-the-ico/news-and-events/news-and-blogs/2019/10/statement-on-an-agreement-reached-between-facebook-and-the-ico/)


## Policing User interaction

So they have your data.. how about [policing how you interact in VR?](
https://support.oculus.com/1694069410806625/) Supporting the end user with the capability of "safe zones" where people cant come too close or they disappear are good and I can attest to this with first hand experience. No one wants some drunk dude to start caressing you when you're vibing in various VR worlds. Also the ability to block shouldn't have to be questioned. But facebook setting the standard for you? This is a new space, and perhaps something that needs to be taken into consideration even more. Users have reported their headsets are being bricked due to misconduct that facebook deemed unsuitable. Entertain the idea that just like the YouTube "ad-pocalypse" that facebook will be entirely family friendly on their VR platforms to allow for advertisers to use it. If facebook are harsh with their code of conduct policies, then they can sell to advertisement agencies your data along with the guarantee that their ad is being displayed in an environment they can control.


### Closing Statement
As you can see here as well after a shop to get some eggs at my local Asda, my face is now being recorded nice and close to be stored on a database somewhere. With next to no contact with their privacy team to tell me where it is being stored. I have reached out for comment but don't suspect I will get much joy as [this gent](https://medium.com/@ScottMcGready/asdas-right-to-collect-your-data-outweighs-your-right-to-privacy-e80cf6cc4376) didn't either and his Asda was also in Scotland. They also type in your date of birth, at least they don't have my name.. Oh wait I paid by card.. damn.

{% include gallery.html  gallery=4 %}

It does seem like the more markets get monopolized, the less privacy and control you have. Just makes me think of a dystopian future. The lines between your digital life and real life are almost non existent if this continues. 

I fear that privacy is dead in the sense that corporations can do what they want in this space to the general user. 

**Nothing to hide is what I say, but an invasion on my privacy to no personal benefit is hard for me to justify.**
{: .notice}

Which is why you won't see me complaining about Google Home an awful lot.. (also their privacy controls are the best accessible ive seen from a golden cuff company)


## Further Reading
* [GDPR Complaints](https://ico.org.uk/your-data-matters/the-right-to-object-to-the-use-of-your-data/)
* [Asda recording your face at self scan](https://medium.com/@ScottMcGready/asdas-right-to-collect-your-data-outweighs-your-right-to-privacy-e80cf6cc4376)
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