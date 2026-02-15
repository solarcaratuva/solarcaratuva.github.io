---
title: Common Terminology
nav_order: 98
parent: Embedded
has_children: false
---

# Common Terminology

## Team & Car Specific

- **Riv3, Riv3S...** - shorthand for the Rivanna3 car, Rivanna3S car, etc.
- **Board** - printed circuit boards with a microcontroller, designed by *Hardware Integration* but programmed by *Embedded* and *Telemetry*
    - Rivanna3 has PowerBoard, WheelBoard, and TelemetryBoard
- **Fault** - a critical error where the car MUST stop / shutdown for safety reasons. Faults are almost always from the BMS and Motor Controller
- **BMS, BPS** - Battery Management / Protection System, the system that controls the battery
- **LV, HV** - low voltage, high voltage
    - LV hardware is managed by *Hardware Integration*, HV hardware is managed by *Power*, *Solar*, *Hardware Integration*

## Hardware Components

- **STM chip** - one of the microcontrollers we use, made by ST Microelectronics
- **ST-Link** - the physical device used to upload code
- **GPIO** - General Purpose Input / Output pins, these pins are used to input and output digital signals
- **3V3** - 3.3 volts, the voltage we interact with most of the time
- **High, Low** - the voltage is at its maximum or minimum, used in reference to digital signals
- **AD2**: An all-in-one electrical / embedded measurement and testing device. It uses Waveforms (AD2's software app) to interface with it.
    - If you take ECE 2300 'Applied Circuits', this is the same device the course gives you

## Communication Protocols

- **CAN** - Controller Area Network, a common communication line that runs throughout the car, purple cable
    - described in much detail in the [Development Guide](https://solarcaratuva.github.io/Embedded/riv3_dev_guide.html)
- **UART, I2C, SPI** - various serial communication protocols we use

## Software Concepts

- **"Upload" code** - copy a binary executable to the microcontroller, industry term is "flashing", but the team has always called it uploading
- **Buffer** - a set size block of memory that temporarily holds data, data is copied into and out of a buffer
- **Interrupt** - when some 'hardware event' occurs (ex. IO event), the microcontroller pauses the code it is currently running to run another function to handle the event
- **IO** - input / output operations
- **Polling** - constantly checking some hardware condition until the condition is met (ex. reading a pin in an infinite while loop)
- **Real Time Operating System (RTOS)** - library that provides threading and synchronization support