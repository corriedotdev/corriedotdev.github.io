---
layout: post
title: "We can Remove Tremors in VR using the 1-Euro-Filter"
excerpt: "I want to see this filter integrated into every VR HMD Accessibility Menu with a Toggle. It’s just a single script.. One core component discovered during my PhD for the best part of 3 years. Review process is killing me so have decided to share the science now and wait on journal publication. We CAN remove tremors in VR. I want every VR system to have this as an option in Meta / Valve / Pico Accessibility Settings."
categories: [VR🥽,Publication📕, Download🔻]
comments: true
image:
  feature: feature/vr-filter.jpg
galleries:
 1:
   -
     - { url: '/img/filter/filter.PNG', alt: 'vr filter'}
 2:
   -
     - { url: '/img/filter/vr.png', alt: 'vr filter'}
     - { url: '/img/filter/Capture.PNG', alt: 'vr filter'}     
 3:
   -
     - { url: '/img/filter/noise.gif', alt: 'vr filter'}
     - { url: '/img/filter/ev.gif', alt: 'vr filter'}
 4:
   -
     - { url: '/img/filter/slider.png', alt: 'vr filter'}
     - { url: '/img/filter/button.png', alt: 'vr filter'}
---

![JWT Screen]({{ site.url }}/img/filter/filter.PNG)
{: .pull-center}
> I want to see this filter integrated into every VR HMD Accessibility Menu with a Toggle. It's just a single script.

Paper pending Publication at my preferred journal which is Springer Nature Virtual Reality
**Pre-Print** Paper available [here]()          

**Git Study Repo** Paper available [here](https://github.com/corriedotdev/vr-tremor-reduction)      

## Intro
All of us have benign essential tremors, you may notice these shakes in VR when you are selecting an item in a menu using a laser pointer. Some tremors are exaggerated due to the tracking of controllers or hand tracking techniques when using vision. These can be system signal noise or, essential tremors. Between the range of 4-12Hz we have psychotic tremors (sometimes refferred to as essential tremors). Some tremors have a high frequency but a low amplitude resulting in them barely being noticable. Unlike parkinsons tremors where the high amplitude often makes them much more obvious. 

In VR selecting UI components, often at a distance, we neglect to take these tremors into consideration. 

{% include gallery.html  gallery=3 %}


With the use of a low pass filter like the 1-Euro Filter, we can almost remove these tremors found in every healthy individual to increase engagement and prevent frustration when interacting with 2D UI in VR. We can also use this filter during any 3D interaction in VR, as the filter is lightweight and has a delta cut off where the filter is disabled during fast velocity hand movement and only enabled for fine control. My hypothesis is we can reduce symptomatic parkinson tremors with this filter.


## Study

I completed a 30 participant user study, the demographic included the general population with and without exposure to VR before. No participants were aware of neuromuscular disorders and were considered healthy. 

The study required users to interact with 2D buttons and sliders at various ranges. The filter was enabled and disabled at set intervals and their times recorded for integer selection. 

I found that there was significant improvement for buttons at 10m ranges and sliders at 5m and 10m ranged tasks. However, there was average improvement across all interactions with the filter enabled. 

## Results
{% include gallery.html  gallery=4 %}

**Remember** Degrees of Freedom in the T-Test for Means is N-1 
{: .notice}


| Button Range | T-Test Result| 
|:--------|:-------:|
| 1m   | t(29)= 1.0608, p=0.2975  | 
| 5m   | t(29)= 2.1426, p=0.0406  | 
| 10m  | t(29)= 4.5569, p < 0.01  | 
|----


| Slider Range |T-Test Result| 
|:--------|:-------:|
| 1m   | t(29)= 0.7833, p=0.4397  | 
| 5m   | t(29)= 1.8518, p=0.0742  | 
| 10m  | t(29)= 3.1750, p=0.0035  | 
|----

{: rules="groups"}

In summary, the t-test proves significance for 10m button, 5m slider and 10m slider. However we see an overall average improvement time across the board. The charts above show this clearer, grey is filter off so standard VR interaction and white is interaction with the filter enabled.

## Improve Your Item Placement in VR
I will make another post here soon for this as there is a lot to break down but as I am disclosing this research in pre-print format for now and awaiting Journal publication, this graphic can be used to help with item placement in VR. All demos include this so you can experience it first hand.
{% include gallery.html  gallery=2 %}
<div markdown="0"><a href="https://corrie.dev/img/filter/vr.png" class="btn btn-success" download >Download Graphic</a></div>
**Minimum Comfort Angle** = (HMD FoV/2)+30 
{: .notice}

**Maximum Comfort Angle** = (HMD FoV/2)+55 
{: .notice}

## Fitts Law
As distance increases, movment time for user interaction also scales. Something to consider and discussed throughout the paper.

**Movement Time** = a+b (log) ^2  (distance/(size+1))
{: .notice}

## Closing Remarks
The use of a laser pointer for interacting with 2D UI elements in VR space could be considered as an interim solution for most VR interactions as many UI elements are similar to that of traditional UI and don’t take advantage of 3D space. By combining the accessibility approaches discussed, an outline of key considerations has been discovered to support developing an ability-first design approach.

Please cite if you use this, its been 3 years of work in short. I really think this can help improve many peoples quality of life. 


# Experience the filter, Download 
You can download the study Git Repository [here](https://github.com/corriedotdev/vr-tremor-reduction) and experience it yourself via Desktop VR. You can also see how to implement the filter, its a single script!

<div markdown="0"><a href="https://github.com/corriedotdev/vr-tremor-reduction/releases/tag/vr" class="btn btn-info" download >GitHub Study Build</a></div>

If you want to experience it on Quest standalone, please download the experience mentioned in my Modular 3D interface post. 
<div markdown="0"><a href="https://drive.google.com/file/d/1a3d-kjpbjUMr74AmUbnhwgbjU7NUtXv4/view?usp=sharing" class="btn btn-success" download >Download Quest</a></div>

## Further Reading
Check out the following links for inspiration and further reading about this topic
* [Pre-Print tbc]()
* [GitHub Repo Here](https://github.com/corriedotdev/vr-tremor-reduction)
* [Springer Paper](https://link.springer.com/chapter/10.1007/978-3-031-35634-6_2)
* [3D VR Interface GitHub Repo](https://github.com/corriedotdev/vr-modular-3d-gui)


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