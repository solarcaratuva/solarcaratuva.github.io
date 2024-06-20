---
parent: PCB
grand_parent: Legacy
has_children: false
---

# Template PCB Documentation

This document describes the contents of the Template board. For documentation on the recommended pin usage of the STM32 MCU, see the [pins docs](pins.md).

The Template board is a template PCB starter for all the teams to use.

Each of the sections below, apart from the General section, corresponds to a boxed component grouping in the Template schematic. The various component groupings were organized to keep the common component groups (and thus those that will not change frequently) on the left side of the schematic sheet, and the board-specific component groups (and thus those that will be constantly changing while under development) on the right side of the schematic sheet.

## General

This section describes general rules to follow in making the schematic files.

All Labels used to connect nets should be Net Labels and not Global Labels, except for power labels (`VCC_12`, `VCC_5`, and `VCC_3.3`).

Never use absolute file paths. Instead, use relative paths (making use of `./` and `../` as needed) when possible, or KiCad's macros for the project directory `${KIPRJMOD}/`. Also ensure all file paths are Linux/MacOS compatible by using universal forward slashes `'/'` instead of Windows-only back slashes `'\'`, even if that is what KiCad defaults to.

## Power Pathing

There are 3 main power lines: 12 V, 5 V, and 3.3 V. All power lines are generated either from the 12 V power input (`VIN_12V`) to the board, or from the 5 V usb power input (`USB_5V`) to the board.

Though the board can handle being connected to both power supplies at the same time (any back current to the supplies is blocked by a diode on each supply), **it is recommended to connect only one of the two jumpers to select either the external 12 V supply power or the USB power.**

The ST890 is a high-side power switch that limits the current draw on the supplies. See its datasheet on how to set its overcurrent limit.

The Global Label `VCC_12` is the 12 V power line to supply power for all 12 V devices. The Net Label `VIN_12V` is the input 12 V power to the board and should only be connected to the voltage regulator to step down to 5 V. These two nets are connected by a jumper, allowing the user the ability to turn off all 12 V devices while keeping the MCU and all 5 V and 3.3 V devices powered on (this may be useful for when testing only 5 V and 3.3 V devices).

Similarly, all 5 V devices should only connect to `VCC_5` and all 3.3 V devices should only be connected to `VCC_3.3` (i.e., the Global Labels). All other labels (the Net Labels), such as `PS_5V`, `PS_3.3V`, `VIN_5V`, and `USB_5V` should not be connected to any devices. They should only be used within the Power Pathing component group (mainly for the voltage regulators and high-side power switches). Note that `VDD` refers to the same net as `VCC_3.3`, but `VDD` is a Net Label instead of a Global Label and thus should only be used in the Microcontroller component group to refer to the VDD supply pins for the MCU.

## CAN Transceivers

Up to 3 CAN Transceivers may be used, only one is shown on the Template board as an example. See the STM32 MCU datasheet for which pins can be used for CAN TX/RX and connect the STBY pin to a digital output from the MCU to control it by software.

## Microcontroller

Common connections to set up the STM32 MCU, see the datasheet for all components and values. This is where all I/O and communication connections to the MCU must be made. See the MCU datasheet for pin configurations.

Do not add any board-specific components to this component group. Instead, make use of KiCad's Net Labels to make connections to board-specific component groups. Ensure all input pins use the Input Protection sheet as a hierarchical block to protect the STM pins from inductive spikes (this hierarchical sheet should NOT be placed in the Microcontroller component group, but instead placed in a board-specific component group, such as EXAMPLE, to save space near the MCU). Also ensure all unused pins are connected to pull-up resistors using a resistor network.

## USB Connection

Uses the STLINK-V3MODS to program/debug the MCU. SWD is the main protocol used, but a solder bridge can be connected to allow JTAG to be used instead. Also uses UART to communicate with the VCP (Virtual COM Port) on the PC. The STLink also provides access to the 5 V USB power.

## Connectors

This is where all external-facing connectors should be placed. Some common connector pins include the external 12 V power supply, CAN connections between boards, and any Digital or Analog inputs or outputs to the board.

## EXAMPLE

This is where each board will implement specific hardware for their application. In the Template board, this is used to step down an analog input using a voltage divider and enforce the input protection required on all MCU input pins.
