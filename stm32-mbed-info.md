# STM32 Development Info # 
## MCU Info ##
* The STM32 board that we are currently evaluating is the [Nucleo-H743ZI](https://www.st.com/en/evaluation-tools/nucleo-h743zi.html). Some members may have received the updated rev. 2 board, the [Nucleo-H743ZI2](https://www.st.com/en/evaluation-tools/nucleo-h743zi2.html).
* The target STM32 SKU is the [STM32H743](https://www.st.com/en/microcontrollers-microprocessors/stm32h743-753.html), which is a single-core MCU that can run up to 480 MHz.
* There are many other SKUs in [the STM32 family](https://www.st.com/en/microcontrollers-microprocessors/stm32-32-bit-arm-cortex-mcus.html); we may want to evaluate a lower-cost/more stripped down SKU, or if needed, dual core versions such as the [STM32H745](https://www.st.com/en/microcontrollers-microprocessors/stm32h745-755.html).

## RTOS Info ##
The RTOS currently being considered is [Mbed OS](https://www.mbed.com/en/platform/mbed-os/).
* Open source
* Many built-in libraries (especially for connectivity)
* Developed and backed by ARM
* Lots of options for toolchains/development environments
* Code written for Mbed can be run on a large variety of hardware
  
## Development Environment ##
* PlatformIO IDE: [Visual Studio Code](https://code.visualstudio.com/)
  * PlatformIO extension ([Instructions](https://platformio.org/install/ide?install=vscode))
* PlatformIO Core: [CLI tool](https://docs.platformio.org/en/latest/core/installation.html)
  * On MacOS, this can simply be installed using the "platformio" package available in Homebrew.
  * On Arch Linux, this can simply be installed using the PlatformIO AUR package.
  
## Helpful References ##
* Pin definitions for the evaluation board are in the [Mbed OS source](https://github.com/ARMmbed/mbed-os/tree/master/targets/TARGET_STM/TARGET_STM32H7/TARGET_STM32H743xI)
