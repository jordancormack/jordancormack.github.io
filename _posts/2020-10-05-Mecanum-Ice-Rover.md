---
layout: post
title: "Mecanum Wheel Ice Cream Tub Rover"
image: /images/mecanum-ice/rover.jpg
---

After seeing [this post](https://howtomechatronics.com/projects/arduino-mecanum-wheels-robot/) about an Arduino based robot that used stepper motors and mostly 3D printed mecanum wheels I decided I wanted to try something similar with some of the components I had laying around. My old 3D printer (Anet A8) had recently broken which left me with not only a set of NEMA17 stepper motors, but also an Arduino compatible control board based on the ATMEGA1284P 8-bit microcontroller, with built-in stepper drivers.

<img src="/images/mecanum-ice/anet-board.jpg" alt="" class="inline">

The 3D printable mecanum wheel designs on this post [this post](https://howtomechatronics.com/projects/arduino-mecanum-wheels-robot/) required metal rods to be cut and inserted through each of the rollers as individual axles. I decided to instead modify the wheel side pieces to feature small posts that would act as the axles, instead of separate metal rods. After also modifying the hub geometry to be a tight friction fit around the shafts of the stepper motors, I 3D printed all of the rollers and hubs and assembled them onto four of the NEMA17 stepper motors.

<img src="/images/mecanum-ice/wheels.jpg" alt="" class="inline">

After dropping one of the wheels accidentally, I realised why using metal rods were chosen as axles instead of 3D printed stubs. Still, they were more than strong enough to support the weight of the rover, as long as I decided not to push it off my desk.

<img src="/images/mecanum-ice/broken-wheel.jpg" alt="" class="inline">

I then designed and 3D printed a H-frame to hold the motors and ensure that they remained aligned and fixed in position relative to each other, which is especially key for a rover using mecanum wheels.

<img src="/images/mecanum-ice/frame-print.jpg" alt="" class="inline">

I then needed some sort of box to house the control board and any other components such as the battery and reciever. For this I just happened to have finished a tub of ice cream which ended up being perfect.

<img src="/images/mecanum-ice/rover.jpg" alt="" class="inline">

I managed to use some of the pins intended for the 3D printer's LCD for a standard PPM RC reciver, which fit inside along with a 3 cell Li-Po battery, which gave approximately 12V which is the intended operating voltage of the board.

<img src="/images/mecanum-ice/inside2.jpg" alt="" class="inline">

Below is a video of the rover driving around.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/asmioWCbCow" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
