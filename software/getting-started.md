---
nav_order: 1
parent: Software
---

# Getting Started

## Installing PlatformIO IDE
Follow the [installation instructions](https://platformio.org/install/ide?install=vscode) to install the PlatformIO IDE extension for [Visual Studio Code](https://code.visualstudio.com).

## Importing the Template Project

In the following instructions, replace all instances of "Team" with a subteam board name (PowerAux, Motor, ECU, or Solar).

1. Duplicate the [TemplateCode repository](https://github.com/solarcaratuva/TemplateCode) following the instructions [here](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository#mirroring-a-repository). 
    1. `$ git clone --bare https://github.com/solarcaratuva/TemplateCode.git`
    1. `$ cd TemplateCode.git`
    1. Create a new repository in the [UVA Solar Car organization](https://github.com/solarcaratuva), named TeamCode.
    1. `$ git push --mirror https://github.com/solarcaratuva/TeamCode.git`
    1. `$ cd ..`
    1. `$ rm -rf TemplateCode.git`
1. Clone the new repository (TeamCode) to your local machine.
    1. `$ git clone https://github.com/solarcaratuva/TeamCode.git`
    1. `$ cd TeamCode`
1. Add the TemplateCode repository as a remote of the new TeamCode repository following the instructions [here](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork).
    1. `$ git remote add upstream https://github.com/solarcaratuva/TemplateCode.git`
1. Now to sync the new TeamCode repository with changes in the TemplateCode repository, simply fetch and merge the remote called upstream by following the instructions [here](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).
    1. `$ git fetch upstream`
    1. `$ git checkout master`
    1. `$ git merge upstream/master`

## Running the Code

All tasks neccessary to run the code and see its output can be performed using either the [Project Tasks GUI](https://docs.platformio.org/en/latest/integration/ide/vscode.html#project-tasks) or the [PlatformIO Core (CLI)](https://docs.platformio.org/en/latest/integration/ide/vscode.html#platformio-core-cli).

### Environments

Before running any tasks, the idea of PlatformIO's [configuration environments](https://docs.platformio.org/en/latest/projectconf/section_env.html) must be explained. Taking a look at the `platformio.ini` file at the root of the TemplateCode repository shows the configuration environments defined for the project (the many `[env:NAME]` sections of the file).

One of them, for example is the `uva_solar_car` environment, which uses the `uva_solar_car` board, a custom target that specifies the setup of our board, including specifications of the MCU used, hardware around the MCU, and a few settings that define the behavior of the MCU (for example, what frequency to run the system clock at).

The `uva_solar_car` environment is what we will use when uploading code to the boards we have developed. Until the boards are printed and populated, however, we will need to run our code on one of STM's development boards, which is what the other environments are for. The exact MCU used for compiling and uploading doesn't affect the code we write using Mbed OS, since the hardware details will be abstracted away. These configuration environments in PlatformIO is how we tell Mbed OS which hardware to build for.

### Building

Building compiles and links all project source files into an binary executable file that the MCU will understand and be able to run. However, it does not upload this executable, but instead stores it locally on your PC. This is useful for checking and correcting compile time issues, and does not require any hardware to be connected to your PC.

To build the project using the CLI, simply run the [`pio run` command](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html) and specify the environment to run using the [`-e` or `--environment` option](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html#cmdoption-pio-run-e). For example, to build the `uva_solar_car` environment, run `pio run -e uva_solar_car`.

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Build`. For example, to build the `uva_solar_car` environment, click `env:uva_solar_car` > `General` > `Build`.

### Uploading

Uploading performs a build then uploads the generated executable to the MCU. This requires the MCU to be connected to your PC via the STLink using a USB cable. After the upload is complete, this task will also restart the MCU to ensure the newly uploaded program starts execution at the beginning of the program.

To upload the project using the CLI, simply run the `pio run` command and specify the target as `upload` using the [`-t` or `--target` option](https://docs.platformio.org/en/latest/core/userguide/cmd_run.html#cmdoption-pio-run-t). Make sure to also specify the environment. For example, to upload the `uva_solar_car` environment, run `pio run -e uva_solar_car -t upload`.

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Upload`. For example, to upload the `uva_solar_car` environment, click `env:uva_solar_car` > `General` > `Upload`.

### Using the Serial Monitor

Now your program is running on the MCU, but how do you know if it is working as expected? An easy way to debug your code is by using print statements, but because the MCUs do not include screens to display these print statements, the PC screen will be used instead. This is accomplished by diverting all standard output to one of the PC's COM ports using UART and displaying that data to the built in Serial Monitor. If that sounds complicated, don't worry, because luckily, Mbed OS and PlatformIO already did all of that work for us.

To open the Serial Monitor using the CLI, simply run the [`pio device monitor` command](https://docs.platformio.org/en/latest/core/userguide/device/cmd_monitor.html).

Alternatively, if using the Project Tasks GUI, click the dropdown for the environment and under the `General` tab, click `Monitor`. For example, to monitor the `uva_solar_car` environment, click `env:uva_solar_car` > `General` > `Monitor`.

## Concluding Remarks

For more information about all of the CLI commands, see the [CLI Guide](https://docs.platformio.org/en/latest/core/userguide/index.html).

The only form of debugging explained in this document was printing, but for more complex issues it may be better to use the powerful [Debugging feature](https://docs.platformio.org/en/latest/integration/ide/vscode.html#debugging) built in to PlatformIO.

The next steps to take are to read through the [Mbed OS API](https://os.mbed.com/docs/mbed-os/latest/apis/index.html) and learn about the classes we will be using in our project (e.g. `CAN`, `I2C`, `DigitalIn`, `DigitalOut`, `AnalogIn`, `Ticker`, etc.).
