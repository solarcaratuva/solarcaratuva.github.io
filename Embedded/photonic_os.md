---
title: PhotonicOS
nav_order: 4
parent: Embedded
has_children: false
---
# PhotonicOS

![PhotonicOS Logo](/assets/images/Embedded/PhotonicOS%20Logo.jpeg)

PhotonicOS is the name for the custom real-time embedded operating system that the *Embedded Subteam* began developing in 2025. The OS sits between our application-level code and the physical hardware drivers. It provides support for multithreading, easier to use drivers, and more. 

The team previously used [MbedOS](https://os.mbed.com/mbed-os/), but chose to leave it after it reached end of life, and we bought hardware (the screen in the steering wheel) that MbedOS does not support. 

## What is included in PhotonicOS

**Kernel**: We use the [FreeRTOS](https://www.freertos.org/Documentation/00-Overview) kernel. It provides support for multithreading and concurrency utilities. We created high level C++ wrappers to wrap around the features we use to provide a nicer interface.

**Drivers**: The manufacturer of our microcontrollers, [STM](https://www.st.com/content/st_com/en.html), provides *STM HAL drivers*, which are C drivers that control the physical hardware. We wrap around these drivers with our own high-level C++ drivers. The key benefit of our C++ drivers, besides creating a nicer object-oriented interface, is peripheral initialization. Through files such as `peripheralmap.cpp`, application code must only provide the pins of a peripheral instead of the peripheral number itself when initializing a peripheral; this automates the process of determining which peripheral instance supports the pins the programmer wants to use. 

**File System**: a file system only exists on the logging SD card. We use [FatFS](https://en.wikipedia.org/wiki/FatFs) for this. 

**Devops**: there are multiple Python scripts we have to ease development operations: `upload.py` to abstract flashing code to a microcontroller, `compile.py` to abstract the compilation system, `monitor.py` to read log data from the microcontroller, and code generation scripts.

## Adding new features

**Not hardware related**: (example: adding a class to process data) <br>
If this library will only be used by a specific board, put the code in that board's folder, otherwise put it in `Common/`.

**Hardware related**: (example: adding support for OctoSPI peripherals)
1. Find the STM HAL driver for the new peripheral.
2. Write a C++ wrapper for the peripheral in `Common/drivers/`, and make sure to update `peripheralmap.cpp` as needed to handle looking up which pins are associated with which instance of the peripheral.
3. Update the code generations scripts to handle the new peripheral.
4. Regenerate code for all microcontrollers, to ensure all microcontroller can run your new code.

## Adding a new board

Example: creating a new board called *TopBoard*, which will use an already supported microcontroller.

TODO


## Adding support for new microcontrollers 

Example: adding support for the STM32xyzABCx microcontroller

**Warning**: PhotonicOS was designed for exclusive use with STM32 microcontrollers. Adding support for other brands of microcontrollers will be a lot of work!

TODO
