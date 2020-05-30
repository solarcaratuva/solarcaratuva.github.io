# STM32 Development Info
## MCU Info
* The STM32 board that we are currently evaluating is the [Nucleo-F413ZH](https://www.st.com/en/evaluation-tools/nucleo-f413zh.html).
* The target STM32 SKU is the [STM32F413](https://www.st.com/en/microcontrollers-microprocessors/stm32f413-423.html).
* The STM32F413 was chosen for its 3 built-in CAN 2.0B controllers and the STM32F4 line being popular with many top solar car teams.
* There are many other SKUs in [the STM32 family](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html); if needed, a lower-cost/more stripped down SKU or dual core versions such as the [STM32H745](https://www.st.com/en/microcontrollers-microprocessors/stm32h745-755.html) could also be considered.

## RTOS Info
* A real-time operating system (RTOS) is currently being considered to allow for better modularity and multiple task scheduling.
* The RTOS currently being considered is [Mbed OS](https://www.mbed.com/en/platform/mbed-os/).
    * Open source
    * Many built-in libraries (especially for connectivity)
    * Developed and backed by ARM
    * Many options for toolchains/development environments
    * Code written for Mbed can be run on a large number of supported ARM hardware
  
## Development Environment
### Software
* PlatformIO Core/CLI
  * Required for base installation. Using the CLI tool is **highly recommended**.
  * On MacOS, this can simply be installed using the "platformio" package available in Homebrew. 
  * On Arch Linux, this can simply be installed using the PlatformIO AUR package.
  * For other platforms, please refer to [this guide](https://docs.platformio.org/en/latest/core/installation.html).
* PlatformIO Extension for [Visual Studio Code](https://code.visualstudio.com/) **(optional)**
  * [Extension installation instructions](https://platformio.org/install/ide?install=vscode)

### Configuration
* [Getting started with the CLI](https://docs.platformio.org/en/latest/core/quickstart.html)
   * The platform for STM32 is `ststm32`.
   * The evaluation board is `nucleo_f413zh`.
   * The framework is `mbed`.
   * If using the RTOS features in the Mbed API, an extra build flag option should be specified in the `platformio.ini` file with a value of `build_flags = -D PIO_FRAMEWORK_MBED_RTOS_PRESENT`.
* The default behavior for PlatformIO with Mbed OS is to recompile the *entire* RTOS every time a project is built with the `PIO_FRAMEWORK_MBED_RTOS_PRESENT` compiler flag. This can lead to extremely long build times.
   * To prevent PlatformIO from rebuilding the RTOS each time, a [build cache directory can be specified to cache the Mbed binaries](https://docs.platformio.org/en/latest/projectconf/section_platformio.html#build-cache-dir).
   * The first project build will cache the binaries in the specified location, and will be automatically fetched on subsequent builds.

## Helpful References
* Pin definitions for the evaluation board are in the [Mbed OS source](https://github.com/ARMmbed/mbed-os/tree/master/targets/TARGET_STM/TARGET_STM32F4/TARGET_STM32F413xH/TARGET_NUCLEO_F413ZH).
* [Full API documentation for Mbed](https://os.mbed.com/docs/mbed-os/v5.15/apis/index.html).
