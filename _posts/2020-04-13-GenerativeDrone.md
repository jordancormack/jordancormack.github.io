---
layout: post
title: "Designing a Drone in Fusion 360 using Generative Design & Modal Analysis"
image: /images/generative_drone1.jpg
---

This post shows how generative design and modal analysis within Fusion 360 can be used to help design and develop a 3D printable drone body. For more specifics on Generative Design in Fusion 360, see my [previous post](https://jordancormack.github.io/GenerativeDesign/). The following electronic components were used for this drone:

|         Component         |                                                                        Manufacturer                                                                        |
|:-------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Flight Controller and ESC | [HGLRC F428 F4 Stack](https://www.hglrc.com/products/6-5g-20x20mm-hglrc-xjb-f428-micro-f4-aio-osd-bec-flight-controller-28a-blhel_s-bb2-2-4s-4-in-1-esc-1) |
|          Battery          |                          [Turnigy 800mAh 3 Cell](https://hobbyking.com/en_us/turnigy-800mah-3s-30c-lipo-pack.html?___store=en_us)                          |
|          Receiver         |                                     [Turnigy TGY-iA6C](https://hobbyking.com/en_us/turnigy-ia6c-ppm-sbus-receiver.html)                                    |
|           Motors          |             [EMAX RS1306 4000kv (Version 1)](https://www.flyingtech.co.uk/electronics/emax-rs1306-racespec-mini-red-bottom-motor-33004000kv) x4            |
|         Propellers        |                           [Gemfan 3035BN 4 Blade](https://hobbyking.com/en_us/3035-bullnose-pc-4-blade-orange-1-pair-cw-ccw.html) x4                       |

### Generative Design Setup

The above components were measured to determine the size and mounting dimensions. An initial preserve geometry could then be created in Fusion 360 as shown below. This preserve geometry will be used by the generative design process as a base to build the body around. In this case the body is 'upside down' as this is the orientation that I want to 3D print it later, and the generative design process can only use the positive axis for the additive manufacturing method. It can be seen that there are four motor mount locations, spaced 110mm apart. The middle square will house the battery, and the bottom plate will be where the flight controller stack will be mounted. Four holes pass through the battery slot to allow access to the flight controller bolts.

<img src="/images/generative_drone_preserve.png" alt="" class="inline">

After the preserve geometry is done, obstacle geometry must be created. This tells the generative design algorithm wher material cannot be placed. Initially, this geometry is created where the battery, motors, flight controller, and bolt paths are located. As generative design has no way to simulate airflow, four large C-shaped bodies have also been created, to allow space in the generated body for air to flow past.

<img src="/images/generative_drone_obstacle.png" alt="" class="inline">
<img src="/images/generative_drone_obstacle2.png" alt="" class="inline">

Each motor is assumed to have around 3N of max thrust with the chosen propeller at 14.8V. A slightly higher load of 5N was applied to each motor mount, and fixed constraints were applied to the inside of the battery housing. In real life, no part of the drone is 'fixed' and the force acts at the centre of gravity - but Fusion 360 will not allow a generative design to run without a fixed constraint somewhere, so this was the most reasonable solution, as the battery is by far the heaviest component.

### Generative Design Outcome Geometry

The generative design algorithm was set to generate an 'unrestricted' outcome, as well as three additive manufacturing outcomes (one for each positive co-ordinate axis). The additive manufacturing method outcomes are supposed to be generated in a way which makes manufacturing them easier in whichever orientation the outcome is set to. This sometimes works well, but in this case the unrestricted outcome (shown below) was already close to being 3D printable.

<img src="/images/generative_drone_body_iso.png" alt="" class="inline">

The only change which was made before 3D printing, was to slice a small amount off the base, to allow it to sit flat on the built plate without needing any support structure.

<img src="/images/generative_drone_body_side.png" alt="" class="inline">
<img src="/images/generative_drone_body_side_cut.png" alt="" class="inline">

Once printed, the components were added to check the mounting dimensions and clearances were all correct.

<img src="/images/generative_drone_assembly_1.jpg" alt="" class="inline">

During the initial flight tests the drone was capable of controlled flight, but there were strong high frequency vibrations causing it to be unstable and the motors to heat up. The high frequency of the vibrations suggested that it was not an issue with the flight software configuration (i.e. Betaflight PIDs). Looking at the onboard blackbox data which was logged at 1KHz, strong oscillations can be seen in the gyro and accelerometer data, starting at around 10% throttle. Zooming in on the gyroscope data, regular oscillations can be seen at around 111Hz.

<img src="/images/BlackBoxLog.JPG" alt="" class="inline">
<img src="/images/BlackBoxLog_gyros.png" alt="" class="inline">

### Modal Analysis

| Mode | Frequency (Hz) |
|:------:|:-----------:|
| 1    | 89.48     |
| 2    | 108.1     |
| 3    | 119.2     |
| 4    | 120       |
| 5    | 145.1     |
| 6    | 379.2     |
| 7    | 501.4     |
| 8    | 517.3     |

### First 8 Modes

Below is a table and GIFs for the first 8 modes of both bodies. The first two modes look to be the same but the rest are not, as the added geometry has affected the stiffness more.

| Mode | Body 1 Frequency (Hz) | Body 2 Frequency (Hz) |
|:----:|:---------------------:|:---------------------:|
|   1  |         89.48         |         94.78         |
|   2  |         108.1         |         121.5         |
|   3  |         119.2         |         271.2         |
|   4  |          120          |         326.7         |
|   5  |         145.1         |         343.3         |
|   6  |         379.2         |         392.6         |
|   7  |         501.4         |         395.2         |
|   8  |         517.3         |         420.3         |

<img src="/images/generative_drone_mode1_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode2_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode3_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode4_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode5_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode6_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode7_comparison.gif" alt="" class="inline">
<img src="/images/generative_drone_mode8_comparison.gif" alt="" class="inline">
