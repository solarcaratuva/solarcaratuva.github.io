---
nav_order: 2
parent: Software
---

# STM32 Development Info

## MCU Info
* The STM32 board that we are currently evaluating is the [Nucleo-F413ZH](https://www.st.com/en/evaluation-tools/nucleo-f413zh.html).
* The target STM32 variant is the [STM32F413](https://www.st.com/en/microcontrollers-microprocessors/stm32f413-423.html).
* The STM32F413 was chosen for its 3 built-in CAN 2.0B controllers and the STM32F4 line being popular with many top solar car teams.
* There are many other variants in [the STM32 family](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html); if needed, low power or dual core versions of the STM32 such as the [STM32H745](https://www.st.com/en/microcontrollers-microprocessors/stm32h745-755.html) could also be considered.

## RTOS Info
* A real-time operating system (RTOS) is currently being considered to allow for better modularity and multiple task scheduling.
* The RTOS currently being considered is [Mbed OS](https://www.mbed.com/en/platform/mbed-os).
    * Open source
    * Many built-in libraries (especially for connectivity)
    * Developed and backed by ARM
    * Many options for toolchains/development environments
    * Code written for Mbed can be run on a large number of supported ARM hardware
  
## Development Environment

### Software
* PlatformIO Core/CLI
  * Required for base installation. Using the CLI tool is **recommended**.
  * On MacOS, this can simply be installed using the "platformio" package available in Homebrew. 
  * On Arch Linux, this can simply be installed using the PlatformIO AUR package.
  * For other platforms, please refer to [this guide](https://docs.platformio.org/en/latest/core/installation.html).
* PlatformIO Extension for [Visual Studio Code](https://code.visualstudio.com) **(optional)**
  * [Extension installation instructions](https://platformio.org/install/ide?install=vscode)

### Configuration
* [Getting started with the CLI](https://docs.platformio.org/en/latest/core/quickstart.html)
   * The platform for STM32 is `ststm32`.
   * The evaluation board is `nucleo_f413zh`.
   * The framework is `mbed`.
   * If using the RTOS features in the Mbed API, an extra build flag option should be specified in the `platformio.ini` file with a value of `build_flags = -D PIO_FRAMEWORK_MBED_RTOS_PRESENT`.
* The default behavior for PlatformIO with Mbed OS is to recompile the *entire* RTOS every time a project is built with the `PIO_FRAMEWORK_MBED_RTOS_PRESENT` compiler flag. This can lead to extremely long build times.
   * To prevent PlatformIO from rebuilding the RTOS each time, a [build cache directory can be specified to cache the Mbed binaries](https://docs.platformio.org/en/latest/projectconf/section_platformio.html#build-cache-dir).
   * The first project build will cache the binaries in the specified location, and the binaries will be automatically fetched on subsequent project builds.

### Serial Terminal
During development, there will almost certainly be a need to use a serial terminal to view text output or do text input to the device. Several different methods can be used to access the serial terminal, depending on what computer is used:
* On Linux, either GNU Screen or many other terminal emulators can be used.
   * The most straightforward one is GNU Screen, which can be installed from almost all repositories. The command to use it to access the terminal is `screen /dev/ttyACM0 9600`, where `/dev/ttyACM0` and `9600` are the default device and baudrate and can be changed. To exit screen, use `Ctrl-A \` or `Ctrl-A` and type `:quit`.
   * Another good option is picocom, which can be installed from most repositories, including Arch and Debian. To access the serial terminal, use `picocom -b 9600 /dev/ttyACM0`. Again, the settings can be changed from the defaults.
* On MacOS, `screen` is also available, and is used similarly to the one in Linux. However, the device path will be different.
* On Windows, the most popular option is [PuTTY](https://www.putty.org/).
On Linux and MacOS, the device path can be found using the command `ls /dev/tty*` before and after plugging in the STM32 board. The new device is the STM32.
On Windows, the COM port used can be found using Device Manager in a similar manner. It will be listed in the "Ports (COM & LPT)" section.

Alternatively, the PlatformIO extension for VSCode has a built-in Serial Monitor that can be accessed from the blue toolbar on the bottom of the IDE. [This link](https://docs.platformio.org/en/latest/integration/ide/vscode.html#ide-vscode-toolbar) shows the toolbar and what each button does. Click on the 8th button from the left (Serial Monitor, looks like a plug) to open up the built-in Serial Terminal.

## Helpful References
* [Pin definitions for the Nucleo-F413ZH in the Mbed source](https://github.com/ARMmbed/mbed-os/tree/master/targets/TARGET_STM/TARGET_STM32F4/TARGET_STM32F413xH/TARGET_NUCLEO_F413ZH).
* [Pin diagrams for the Nucleo-F413ZH](https://os.mbed.com/platforms/ST-Nucleo-F413ZH).
* [Full API documentation for Mbed](https://os.mbed.com/docs/mbed-os/v5.15/apis/index.html).
