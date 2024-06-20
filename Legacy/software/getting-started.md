---
nav_order: 2
parent: Software
grand_parent: Legacy
has_children: false
---

# Getting Started

## Installing PlatformIO IDE
Follow the [installation instructions](https://platformio.org/install/ide?install=vscode) to install the PlatformIO IDE extension for [Visual Studio Code](https://code.visualstudio.com).

## Importing the Template Project

1. Clone the [TemplateCode repository](https://github.com/solarcaratuva/TemplateCode) to your local machine.
    1. `$ git clone https://github.com/solarcaratuva/TemplateCode.git`
    1. `$ cd TemplateCode`

## Adding Support for the Custom Target to PlatformIO

Because PlatformIO does not fully support the STM32G473 MCU, we have to add a configuration file to be able to upload any code to our MCU (note that this is not neccesary to upload code to dev boards):

1. Locate the following folder (either using the following command in Git Bash or clicking through the File Explorer).
    1. `$ start ~/.platformio/packages/tool-openocd/scripts/board`
1. Make a copy of the file in the same folder `st_nucleo_f4.cfg`, and name it `st_nucleo_g4.cfg`.
1. Open the new file (`st_nucleo_g4.cfg`) and edit the 3rd line of code (skip the comments) to `g4` instead of `f4`.
    1. Edit it from `source [find target/stm32f4x.cfg]` to `source [find target/stm32g4x.cfg]`

The new file `st_nucleo_g4.cfg`, located at `~/.platformio/packages/tool-openocd/scripts/board/st_nucleo_g4.cfg`, should now contain (ignoring the comments):

```
source [find interface/stlink.cfg]

transport select hla_swd

source [find target/stm32g4x.cfg]

reset_config srst_only
```

And now you should be able to upload code to our custom boards by following the nest instructions.

## Running the Code

All tasks neccessary to run the code and see its output can be performed using either the [Project Tasks GUI](https://docs.platformio.org/en/latest/integration/ide/vscode.html#project-tasks) or the [PlatformIO Core (CLI)](https://docs.platformio.org/en/latest/integration/ide/vscode.html#platformio-core-cli).

### Environments

Before running any tasks, the idea of PlatformIO's [configuration environments](https://docs.platformio.org/en/latest/projectconf/section_env.html) must be explained. Taking a look at the `platformio.ini` file at the root of the TemplateCode repository shows the configuration environments defined for the project (the many `[env:NAME]` sections of the file). There should be at least one for each of our four boards (ECU, Motor, Power/Aux, Solar).

One of them, for example is the `ecu` environment (note: there is both a `[ecu]` section and a `[env:ecu]` section, the environment is defined by the latter), which extends from both the `uva_solar_car` and `ecu` sections. The `uva_solar_car` section uses the `uva_solar_car` board, a custom target that specifies the setup of our board, including specifications of the MCU used, hardware around the MCU, and a few settings that define the behavior of the MCU (for example, what frequency to run the system clock at).

Each of the individual team environments (`ecu`, `motor`, `power_aux`, and `solar`) are what we will use when uploading code to the boards we have developed. Until the boards are printed and populated, however, we will need to run our code on one of STM's development boards, which is what the `nucleo_...` environments are for. The exact MCU used for compiling and uploading doesn't affect the code we write using Mbed OS, since the hardware details will be abstracted away. These configuration environments in PlatformIO is how we tell Mbed OS which hardware to build for.

The final environment, `native`, is only used to run unit tests locally on your computer or on continuous integration platforms, and not on any embedded hardware.

### Building

Building compiles and links all project source files into an binary executable file that the MCU will understand and be able to run. However, it does not upload this executable, but instead stores it locally on your PC. This is useful for checking and correcting compile time issues, and does not require any hardware to be connected to your PC.

To build the project using the CLI, simply run the [`pio run` command](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html) and specify the environment to run using the [`-e` or `--environment` option](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html#cmdoption-pio-run-e). For example, to build the `ecu` environment, run `pio run -e ecu`.

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Build`. For example, to build the `ecu` environment, click `env:ecu` > `General` > `Build`.

### Uploading

Uploading performs a build then uploads the generated executable to the MCU. This requires the MCU to be connected to your PC via the STLink using a USB cable. After the upload is complete, this task will also restart the MCU to ensure the newly uploaded program starts execution at the beginning of the program.

To upload the project using the CLI, simply run the `pio run` command and specify the target as `upload` using the [`-t` or `--target` option](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html#cmdoption-pio-run-t). Make sure to also specify the environment. For example, to upload the `ecu` environment, run `pio run -e ecu -t upload`.

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Upload`. For example, to upload the `ecu` environment, click `env:ecu` > `General` > `Upload`.

### Using the Serial Monitor

Now your program is running on the MCU, but how do you know if it is working as expected? An easy way to debug your code is by using print statements, but because the MCUs do not include screens to display these print statements, the PC screen will be used instead. This is accomplished by diverting all standard output to one of the PC's COM ports using UART and displaying that data to the built in Serial Monitor. If that sounds complicated, don't worry, because luckily, Mbed OS and PlatformIO already did all of that work for us.

To open the Serial Monitor using the CLI, simply run the [`pio device monitor` command](https://docs.platformio.org/en/latest/core/userguide/device/cmd_monitor.html).

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Monitor`. For example, to monitor the `ecu` environment, click `env:ecu` > `General` > `Monitor`.

## Concluding Remarks

For more information about all of the CLI commands, see the [CLI Guide](https://docs.platformio.org/en/latest/core/userguide/index.html).

The only form of debugging explained in this document was printing, but for more complex issues it may be better to use the powerful [Debugging feature](https://docs.platformio.org/en/latest/integration/ide/vscode.html#debugging) built in to PlatformIO.

The next steps to take are to read through the [Mbed OS API](https://os.mbed.com/docs/mbed-os/latest/apis/index.html) and learn about the classes we will be using in our project (e.g. `CAN`, `I2C`, `DigitalIn`, `DigitalOut`, `AnalogIn`, `Ticker`, etc.).
