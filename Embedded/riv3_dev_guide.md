---
title: Rivanna3 Development Guide
nav_order: 2
parent: Embedded
has_children: false
---

# Rivanna3 Development Guide

*This page is the main source for explanations about development decisions, and how implemented logic is meant to work at a high-level, for the Rivanna3 Embedded Codebase*

[Rivanna3 GitHub Link](https://github.com/solarcaratuva/Rivanna3)

## Project Architecture

**Folder Structure**: at a high level, the project is structured into folders as follows:
- Boards: `WheelBoard`, `TelemetryBoard`, and `PowerBoard` hold code for those respective boards
- `Common` contains code that is used across the entire project; a significant portion of it is auto-generated
- MbedOS: `mbed-os` and `TARGET_UVA_SOLAR_CAR` contain MbedOS libraries and configuration
- `cmake_build` contains the compiled code from across the project that is actually uploaded to the car
- Legacy: `DriverBoard`, `BatteryBoard`, and `Motor` are legacy boards and code used in *Rivanna2S*, and are only shown in *Rivanna3* for easy reference

**CAN**: under `*board_name*/lib/src` for each board there is a file `*board_name*CANInterface.cpp` that represents the actual CAN connection for each board.
- To send messages: code in `main.cpp` calls the `send()` function, and the message is sent and logged.
- To receive messages: the `message_handler()` function waits for CAN messages. When one is received, the function logs the message, and checks if the message is one of the types of CAN messages it is waiting for. If so, the function calls the appropriate `handle()` function in `main.cpp`; if not, the message is disregarded.

## PowerBoard

**Signal Flash Handler**:


## WheelBoard
*Note: the Telemetry Subteam is responsible for controlling the embedded screen on the WheelBoard; this is just discussion on Embedded's section of the board*


## TelemetryBoard
*This board is the responsibility of the Telemetry Subteam, see them for help*