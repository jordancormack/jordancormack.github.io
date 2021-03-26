---
layout: post
title: "Digital Battery Backpack for the 1985 Canon VM-E1"
image: /images/vme1-battery/thumb.jpg
---

<img src="/images/vme1-battery/iso.jpg" alt="" class="inline">

In 1985 Canon produced its first single-unit video camcorder, the [VM-E1](https://global.canon/en/c-museum/product/8mmvc310.html#:~:text=Canon%20produced%20its%20first%20single,and%20outstanding%20operability%20and%20functionality.). Whilst browsing Facebook Marketplace I saw one for sale for around £10 broken. Initially, I was mostly interested in it only for the included hard-case, but I have also always enjoyed taking apart old electronics equipment so I thought it was worth buying.

<img src="/images/vme1-battery/case.jpg" alt="" class="inline">

After picking it up I noticed that although dirty, it seemed to be in good condition for something 35 years old. I took the side off for a view inside, and again noticed it was in good condition and showed no signs of being dropped or damaged.

<img src="/images/vme1-battery/inside1.jpg" alt="" class="inline">

I measured the voltage of the battery, and quickly realised that it was far too low to be able to power up the camera. Unfortunately it didn't come with a charger, but there was an included AC adaptor. After connecting it, and plugging it in...it turned on! Below is a photo taken through the viewfinder.

<img src="/images/vme1-battery/view.jpg" alt="" class="inline">
<img src="/images/vme1-battery/eye.jpg" alt="" class="inline">

Taking a closer look at power input on the camera, it was clear that the batteries and AC adaptor just connected to some contacts on the rear of the camera, at 7.2V according to the AC adaptor. I decided that creating a replacement battery with a modern Li-Po in a 3D printed case would be a nice little project.

<img src="/images/vme1-battery/read-bat.jpg" alt="" class="inline">
<img src="/images/vme1-battery/rear-open.jpg" alt="" class="inline">

Alongside this, I was wondering what the best way would be to actually record video from the camera, as finding 8mm videocassettes in 2020 isn't as easy as it was in 1985. Looking through the case it came with, I noticed a little RF unit, for feeding video in or out of the camera. I took it apart and figured out that the composite analog video output from the RF unit was directly passed through to a couple of pins on the connector that clips on to the rear of the camera.

<img src="/images/vme1-battery/rfunit.jpg" alt="" class="inline">
<img src="/images/vme1-battery/rearbottom.jpg" alt="" class="inline">

In order to record the composit output with a somewhat portable setup, I used an AV to HDMI converter and a HDMI USB capture stick, connected to a Raspberry Pi Zero.

<img src="/images/vme1-battery/adapt.jpg" alt="" class="inline">

As the battery used some custom contacts for power, I decided to use the backplate of one of the old batteries as a base for my 3D printed unit, which could then slot into the back easily. I mounted the Raspberry Pi Zero to the top, and added a couple of regulators to step down the Li-Po battery voltage to 7.2V for the camera, and 5V for the Pi.

<img src="/images/vme1-battery/readpi.jpg" alt="" class="inline">

I then 3D printed an enclosure for to house the rest of the components and hide all of the messy wiring and hot glue. A lid could then be attached, which included a battery strap to hold a Li-Po on the outside. In a future revision this could be replaced with an internal battery, or swapped for something more friendly such as 18650 Li-Ion cells.

<img src="/images/vme1-battery/rearcaseopen.jpg" alt="" class="inline">
<img src="/images/vme1-battery/rearfinal.jpg" alt="" class="inline">

Below is a video of one of the recordings I have taken. Both the AV to HDMI converter and HDMI capture device are low-cost versions, so I have absolutely no idea how this compares to the original quality using 8mm tapes, but it at least works!

<div class="video-container">
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/xj_3vBegMwM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>
