---
layout: post
title: "CirmiSupply Linear 10"
categories: 
tags: 
  - lab power supply
  - bench power supply 
  - linear 
  - analog
  - LT3080
  - 10V
  - ATtiny414
  - INA228
  - LM75B
  - STPS1045B-Y
  - ST7567S
categories:
  - Analog Electronics Projects
---

This project started as a simple idea while browsing through the LT3080 datasheet. I came across a lab supply schematic that immediately caught my attention.
The concept is simple: take the original schematic and add some more functionality, make a simple instrument that is convenient to use. 

## The Schematic

![Desktop View](/assets/img/post/cirmisupply-linear-10/schematic.png){: width="7016" height="4961" .w-100}
_The schematic of the supply._

### Voltage & Current regulation
As I mentioned, the heart of the system is the Analog Devices LT3080 low dropout linear regulator, two of them: one for voltage, and the other for current regulation. 

It comes in a nice 5-Lead DD Pak package, which comes in handy because I mill all my PCBs, with a 0.5 mm clearance, and use SMD wherever I can.

### Output stage
For measuring the output voltage and the current, the INA228 comes into the picture. It’s easy to use and interface with, thanks to the availability of existing libraries. 

2 relays, one for switching the output, another for shorting the output through a resistor, making it easy to set the current limit.

### Display
I plan to use a ST7567S display. I've fallen in love with simple LCDs, so from the beginning I was thinking of using an ST7567S or a 1602-form-factor display. 

## Current project status
At the time of writing, only the schematic is complete. I started working on the PCB layout and routing, but it’s far from complete. For the enclosure and the user interface, I only have concept arts; I haven’t started the design process. 

