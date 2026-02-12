---
title: Common Terminology
nav_order: 98
parent: Embedded
has_children: false
---

# Common Terminology

- Riv3, Riv3S… - shorthand for the Rivanna3 car, Rivanna3S car, etc. 
- CAN – Controller Area Network, a common communication line that runs throughout the car, purple cable
    - described in much detail in the [Development Guide](https://solarcaratuva.github.io/Embedded/riv3_dev_guide.html)
- Board – printed circuit boards with a microcontroller, designed by *Hardware Integration* but programmed by *Embedded* and *Telemetry*
    - Rivanna3 has PowerBoard, WheelBoard, and TelemetryBoard
- Fault – a critical error where the car MUST stop / shutdown for safety reasons. Faults are almost always from the BMS and Motor Controller
- STM chip – one of the microcontrollers we use, made by ST Microelectronics 
- “Upload” code – copy a binary executable to the microcontroller, industry term is “flashing”, but the team has always called it uploading 
- ST-Link – the physical device used to upload code
- LV, HV – low voltage, high voltage
    - LV hardware is managed by *Hardware Integration*, HV hardware is managed by *Power*, *Solar*, *Hardware Integration*
- 3V3 – 3.3 volts, the voltage we interact with most of the time
- BMS, BPS – Battery Management / Protection System, the system that controls the battery pack
