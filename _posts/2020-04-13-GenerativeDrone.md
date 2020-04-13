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

These were measured to determine the size and mounting dimensions.



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
