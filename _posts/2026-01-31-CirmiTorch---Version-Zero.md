---
layout: post
title: "CirmiTorch – Version Zero"
categories: 
tags: 
  - flashlight 
  - ATtiny402 
  - CN5711 
categories:
  - Electronics Projects
---

Every project needs a beginning. Not a polished, market-ready product, but a *version zero*: something real, working, and imperfect. CirmiTorch is exactly that.

This is a small, simple flashlight project built around experimentation, constraints, and learning. It is intentionally a **0. version**, designed to be good enough to exist — and flexible enough to be improved.

![Desktop View](/assets/img/post/cirmi-torch/front.jpg){: width="6016" height="4010" .w-75}
_The front side of the flashlight._

## The Idea

CirmiTorch is a compact flashlight powered by **three AA batteries**, controlled by an **ATtiny402**, and driving LEDs via a **CN5711**. On paper, this is nothing exotic. In practice, the combination of limited resources, power management, user interface, and physical design turned it into a surprisingly rich engineering exercise.

From the very beginning, the philosophy was clear:

> First, make it work. Then make it better.

That mindset applies to everything here:

* the schematic
* the component selection
* the firmware
* the ergonomics
* and the physical design of the lamp itself

## Living With Constraints

The ATtiny402 is not a generous microcontroller. Memory is tight, peripherals are limited, and every feature has a cost. Instead of fighting that, CirmiTorch embraces it.

One of the more interesting outcomes of these constraints was the need to write a **custom OLED driver** from scratch. The display used is a **48×88 pixel OLED**, and none of the existing libraries were a good fit — either too large, too slow, or simply incompatible.

So a dedicated, minimal OLED library was written specifically for this project, optimised for:

* small flash size
* low RAM usage
* just the features actually needed

## User Interface

Despite the simplicity, the flashlight has a small display that shows:

* the current **battery voltage**
* the **brightness level** as a percentage

![Desktop View](/assets/img/post/cirmi-torch/back.jpg){: width="6016" height="4010" .w-75}
_The back side of the flashlight with it's user interface._

Both of these turned out to be more challenging than expected.

Measuring battery voltage accurately with limited ADC resolution, then turning that into something meaningful for the user, required careful scaling and filtering. On top of that, handling **decimal values and percentages** on a tiny microcontroller without floating point hardware meant being very deliberate about fixed-point maths and rounding.

These are not problems you notice on larger MCUs — which is exactly why solving them here was so satisfying.

## Design

During the mechanical design phase, one particularly nice detail emerged almost accidentally: the **snap-fit back cover**. The rear plate clicks into place with just the right amount of force — secure enough to hold firmly, yet easy to remove without tools.

![Desktop View](/assets/img/post/cirmi-torch/cover.png){: width="1280" height="690" .w-75}
_3D render of the back cover._

It is a small thing, but details like this often define how a device *feels* in daily use.


## Hardware and Source Code

The hardware side of CirmiTorch is deliberately simple and hands-on.
The PCBs were milled on a CNC machine, not ordered from a board house. From the very beginning, the PCB layout was designed with milling in mind: all clearances are suitable for mechanical isolation, with a minimum spacing of 0.5 mm throughout the design.

 There are **two separate boards**: one dedicated to the control electronics and another serving purely as the LED panel. Splitting the design this way made iteration easier and allowed each board to be optimised for its specific role.

The firmware is fully open source and available on GitHub, along with **all other project resources**. This includes:

* the complete firmware source code
* KiCad design files for the schematics and PCBs
* the FreeCAD files used for the mechanical design

Everything needed to understand, reproduce, or build upon CirmiTorch is collected in one place:

[CirmiTorch](https://github.com/stu-forge/CirmiTorch)



## What’s Next?

CirmiTorch is not finished. It is *started*.

Future iterations may refine:

* efficiency
* LED driving strategy
* enclosure ergonomics
* firmware structure
* or even the choice of microcontroller itself

But none of that would exist without this first step.

Version zero matters. Without it, there is nothing to improve.

This is CirmiTorch 0.0.
