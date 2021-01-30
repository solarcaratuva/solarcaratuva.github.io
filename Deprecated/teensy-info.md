---
nav_order: 1
parent: Deprecated
---

# Teensy Development Info
The KiCAD PCB design files and the ECU code are located in the [EmbeddedSystem repository](https://github.com/solarcaratuva/EmbeddedSystem).

## Code Development ##
* Install the Arduino IDE.
* Install the Teensyduino add-on.
* Go to the Teensyduino install location and delete the included version of FlexCAN.
    * On Linux, this is located at `/usr/share/arduino/hardware/teensy/avr/libraries/FlexCAN`.
* Replace the FlexCAN folder by cloning the [fork of the FlexCAN library by pawelsky](https://github.com/pawelsky/FlexCAN_Library) into the same location.
* To build the lights code, the Arduino "Chrono" library will need to be installed.
    * In the Arduino IDE, go to `Tools > Manage Libraries`.
    * Search for "Chronometer" and install the "Chrono" library by Thomas O Fredericks and Sofian Audry.
* The ECU code is located inside the `ECU` folder of the main `EmbeddedSystem` repository.
* Sample code in `KLS.ino` for testing the KLS motor controllers is in the [KLS motor controller library](https://github.com/solarcaratuva/KLS).

## PCB Design ##
* Install KiCAD.
* The KiCAD project is located inside the `ECU_PCB` folder.
