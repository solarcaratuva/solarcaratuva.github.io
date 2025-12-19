---
title: HIL Testing Development Guide
nav_order: 5
parent: Embedded
has_children: false
---

# Hardware-in-Loop Testing Development Guide

*This page serves as the main guide for UVA Solar Car Team's Hardware-in-Loop (HIL) testing system. Here, we will provide a description of it's implementation and how to use it.* 

[Hardware-in-Loop Testing GitHub Link](https://github.com/solarcaratuva/HiL_Testing)

## Interaction with the Rivanna3 Repo

TODO

## Interfaces and Simulated Hardware

The HIL system has the same interfaces that the real boards have with the rest of the car, enabling the system to simulate the rest of the car and the driver without the embedded code under test knowing. 

**Digital GPIO Pins**

Digital GPIO pins are described in the `gpioPin.py` file located in the `HIL_Testing` repository. It primarily uses the `gpiozero` library to utilize pins on the Raspberry Pi.

- *Digital Inputs:* digital inputs use a pulldown resistor and are active-high

    - `read(self) -> bool`: reads the current input and returns a boolean

- *Digital Outputs:* digital outputs are active-high and initialized as 0 

    - `write(state: bool)`: writes a 1 or 0 with to the output

    - `on()`: outputs a 1 to the pin; does nothing if already on

    - `off()`: outputs a 0 to the pin; does nothing if already off

    - `toggle()`: toggles the output of the pin

**Analog GPIO Pins**

Analog GPIO pins are also described in `gpioPin.py` file. 

- *Analog Output*: analog outputs are implemented using a PWM signal of 1 kHz. 

    - `write(value: float)`: sets the duty cycle of the PWM, and takes a value between 0 and 1

    -  `read() -> float`: returns the current stat of the pin

    - `on()`: sets the analog pin to its maximum value (duty cycle of 100%)

    - `off()`: set the analog pin to its lowest value (duty cycle of 0%)

**CAN Messaging**

TODO

**Motor Controller**

TODO

## Physical Hardware

TODO

## Making Tests

TODO

## Tests Driver

TODO