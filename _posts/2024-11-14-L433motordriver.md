---
layout: post
title: "Brushless Motor Driver with CAN Bus"
image: /images/l433_bldc/IMG_2573_241116.jpg
---

A custom motor driver for small gimabl motors. This post is partly sponsored by [PCBWay](https://www.pcbway.com/), who manufactured and assembled the PCBs for this project.

Brushless (BLDC) motors are commonly used for motion control systems that require smooth, fast, precise operation. They are efficient and can often be found with low 'KV' values which result in good toque without needing to use gearboxes.

Camera gimbals are one application where the use of these low-KV BLDC motors are widely used, and these gimbal motors can be repurposed for use in other robotics or motion control systems. The [iPower GM3506 with encoder](https://shop.iflight.com/gimbal-motors-cat44/ipower-motor-gm3506-brushless-gimbal-motor-w-as5048a-encoder-pro1155) is a low-cost gimbal motor which features a magnetic encoder on the back, which reads the position of a diametrically magnetised magnet attached to the motor shaft.

<img src="/images/l433_bldc/IMG_2580_241116.jpg" alt="" class="inline">
<img src="/images/l433_bldc/encoder.jpg" alt="" class="inline">

Dedicated gimbal motor driver boards are available to create custom camera gimbals using these motors, but they are often not ideal for other use cases, and require lots of wires between the driver board and motor/encoder. Whilst there are standalone drivers for closed-loop BLDC motor control (e.g. [ODrive](https://odriverobotics.com/)) these can be quite expensive, and as they are intended to be used on a wide variety of motors, they can be hard to integrate with a small gimbal motor in a compact, easy way.

[SimpleFOC](https://simplefoc.com/) is an open-source library and community for controlling BLDC motors using Field Oriented Control (FOC) in a modular, cross-platform way that works with many common microcontrollers and motor drivers. The inspiration for this project came from using the [SimpleFOC Mini](https://docs.simplefoc.com/simplefocmini) motor driver, which is small and low-cost but still requires a separate encoder and microcontroller.

<img src="/images/l433_bldc/IMG_2564_241116.jpg" alt="" class="inline">

As I'd recently made a new version of my [Low-cost STM32 development board](https://cormack.xyz/stm32devboard/) which worked well with the SimpleFOC Mini and the iPower GM3506, but the wiring was a bit of a mess and the encoder on the GM3506 was a bit unreliable (I think due to the small loose connector). So I decided to make custom gimbal motor driver board that fit within the footprint of the GM3506, without needing any external wiring for the microcontroller, encoder, or regulator.

I used the same [DRV8313 2.5-A Triple 1/2-H Bridge Driver](https://www.ti.com/product/DRV8313) as the SimpleFOC Mini, but using the smaller VQFN package, and a row of smaller ceramic capacitors, instead of the single large electrolytic capacitor. I placed a [AS5048A](https://ams-osram.com/products/sensor-solutions/position-sensors/ams-as5048a-high-resolution-position-sensor) magnetic encoder in the middle of the board, which will be mounted so that it can read the magnet angle on the back of the GM3506.

The same [STM32L433CCT6](https://www.st.com/en/microcontrollers-microprocessors/stm32l433cc.html) and [TCAN330](https://ti.com/product/TCAN330) as I used on my previous dev board were used, along with some step down converters for 5V and 3.3V. A USB-C port allows for easy programming, debugging, and control, and an XT30(2+2) connector can provide power from either a standard XT30 source, or power and CAN bus control from a compatible source. The DRV8313 has a 6.3V undervoltage lock-out, which means that when powered only by USB, the STM32 can be programmed and the encoder/CAN bus tested, without worrying about the motor spinning and drawing too much current from a USB port.

<img src="/images/l433_bldc/L433_SimpleFOC_Mini.png" alt="" class="inline">

I designed the PCBs in KiCAD, and they were manufactured and assembled by PCBWay. You can either order blank PCBs to assemble yourself (or by another third party), or send them a BOM and pick-and-place files for them to source and fully assemble the PCBs as well.

<img src="/images/l433_bldc/IMG_2587_241116.jpg" alt="" class="inline">

I designed a small 3D printed enclosure to hold the PCB in place on the rear of the motor, and to protect it during use.

<img src="/images/l433_bldc/IMG_2573_241116.jpg" alt="" class="inline">
<img src="/images/l433_bldc/IMG_2578_241116.jpg" alt="" class="inline">

The external size of the PCB and enclosure match that of the original encoder + enclosure.

<img src="/images/l433_bldc/IMG_2590_241116.jpg" alt="" class="inline">

and it works! I uploaded the same code as I used for testing the SimpleFOC Mini with the GM3506 and my L433 dev boards, and it seems to work well.

## To Do

* More testing!
* Tidy up schematic/PCB files (open source?)

## Future Upgrades?

* USB-C PD power option. 12V or 15V are common options on USB-C PD power supplies, at up to a couple of amps. Perfect for the GM3506 and this driver.
* More flexible mounting hole locations, for easier use with alternative motors.