---
parent: PCB
grand_parent: Legacy
has_children: false
---

# Pins

This document describes the different functions of each pin on the STM32 MCU. The highlighted functions are the recommended function to use for the pin, though not all of the recommendations must be followed. Some recommendations, however (such as those required for SWD programming/debugging) must be followed. See the datasheet for more details.

The MbedOS pin names are defined in the [github repo](https://github.com/ARMmbed/mbed-os/blob/master/targets/TARGET_STM/TARGET_STM32G4/TARGET_STM32G474xx/TARGET_NUCLEO_G474RE/PinNames.h).

## Sorted by Pin Name

| STM Pin Name | MbedOS Pin Name(s) | Function(s) | Usage |
| :---: | :---: | :--- | :--- |
| PA0 | `PA_0`/`A0` | USART2_CTS, <mark>ADC12_IN1</mark> | _ |
| PA1 | `PA_1`/`A1` | USART2_RTS_DE, <mark>ADC12_IN2</mark> | _ |
| PA2 | `PA_2` | USART2_TX, <mark>ADC1_IN3</mark> | _ |
| PA3 | `PA_3` | USART2_RX, SPI1_CLK, <mark>ADC1_IN4</mark> | _ |
| PA4 | `PA_4`/`A2` | SPI1_NSS, SPI3_NSS, USART2_CK, <mark>ADC2_IN17</mark>, <mark>DAC1_OUT1</mark> | _ |
| PA5 | `PA_5`/`D13` | SPI1_SCK, <mark>ADC2_IN13</mark>, <mark>DAC1_OUT2</mark> | _ |
| PA6 | `PA_6`/`D12` | SPI1_MISO, <mark>ADC2_IN3</mark>, <mark>DAC2_OUT1</mark> | _ |
| PA7 | `PA_7`/`D11` | SPI1_MOSI, <mark>ADC2_IN4</mark> | _ |
| PA8 | `PA_8`/`D7` | I2C3_SCL, I2C2_SDA, USART1_CK, <mark>FDCAN3_RX</mark>, <mark>ADC5_IN1</mark> | _ |
| PA9 | `PA_9`/`D8` | I2C3_SMBA, I2C2_SCL, USART1_TX, <mark>ADC5_IN2</mark> | _ |
| PA10 | `PA_10`/`D2` | I2C2_SMBA, SPI2_MISO, USART1_RX | _ |
| PA11 | `PA_11` | SPI2_MOSI, USART1_CTS, <mark>FDCAN1_RX</mark> | MAIN_CAN_RX |
| PA12 | `PA_12` | USART1_RTS_DE, <mark>FDCAN1_TX</mark> | MAIN_CAN_TX |
| PA13 | `PA_13` | <mark>SWDIO</mark> | SWDIO |
| PA14 | `PA_14` | <mark>SWCLK</mark> | SWCLK |
| PA15 | `PA_15` | <mark>JTDI</mark>, I2C1_SCL, SPI1_NSS, SPI3_NSS, USART2_RX, UART4_RTS_DE, FDCAN3_TX | JTDI (not used) |
| PB0 | `PB_0`/`A3` | <mark>ADC3_IN12</mark>,<mark>ADC1_IN15</mark> | _ |
| PB1 | `PB_1` | <mark>ADC3_IN1</mark>, <mark>ADC1_IN12</mark> | _ |
| PB2 | `PB_2` | I2C3_SMBA, <mark>ADC2_IN12</mark> | _ |
| PB3 | `PB_3`/`D3` | <mark>SWO</mark>, SPI1_SCK, SPI3_SCK, USART2_TX, FDCAN3_RX | SWO |
| PB4 | `PB_4`/`D5` | SPI1_MISO, SPI3_MISO, USART2_RX, UART5_RTS_DE, <mark>FDCAN3_TX</mark> | _ |
| PB5 | `PB_5`/`D4` | I2C1_SMBA, SPI1_MOSI, SPI3_MOSI, USART2_CK, I2C3_SDA, FDCAN2_RX, UART5_CTS | _ |
| PB6 | `PB_6`/`D10` | <mark>USART1_TX</mark>, FDCAN2_TX | USB_TX |
| PB7 | `PB_7` | I2C4_SDA, I2C1_SDA, <mark>USART1_RX</mark>, USART4_CTS | USB_RX |
| PB8 | `PB_8`/`D15` | I2C1_SCL, USART3_TX, FDCAN1_RX, <mark>BOOT0</mark> | BOOT0 |
| PB9 | `PB_9`/`D14` | I2C1_SDA, USART3_TX, FDCAN1_TX, I2C2_SDA, UART5_TX | _ |
| PB10 | `PB_10`/`D6` | USART3_TX, SPI1_SCK | MAIN_CAN_STBY (can be on any pin) |
| PB11 | `PB_11` | USART3_RX, <mark>ADC12_IN14</mark> | _ |
| PB12 | `PB_12` | I2C2_SMBA, SPI2_NSS, USART3_CK, <mark>FDCAN2_RX</mark>, <mark>ADC4_IN3</mark>, <mark>ADC1_IN11</mark> | _ |
| PB13 | `PB_13` | SPI2_SCK, USART3_CTS, <mark>FDCAN2_TX</mark>, <mark>ADC3_IN5</mark> | _ |
| PB14 | `PB_14` | SPI2_MISO, USART3_RTS_DE, <mark>ADC4_IN4</mark>, <mark>ADC1_IN5</mark> | _ |
| PB15 | `PB_15` | SPI2_MOSI, <mark>ADC4_IN5</mark>, <mark>ADC2_IN15</mark> | _ |
| PC13 | `PC_13` |  | _ |
| PC14 | `PC_14` | <mark>OSC32_IN</mark> | OSC32_IN |
| PC15 | `PC_15` | <mark>OSC32_OUT</mark> | OSC32_OUT (not used) |
| PF0 | `PF_0` | <mark>OSC_IN</mark> | OSC_IN |
| PF1 | `PF_1` | <mark>OSC_OUT</mark> | OSC_OUT (not used) |
| PG10 | `PG_10` | <mark>NRST</mark> | NRST |

