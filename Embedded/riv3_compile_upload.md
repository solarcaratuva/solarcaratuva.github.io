---
title: Rivanna3 Compile & Upload
nav_order: 2
parent: Embedded
has_children: false
---

# Compiling

[Rivanna3 GitHub Link](https://github.com/solarcaratuva/Rivanna3)

**Software Installation**

1. Install Git: [Link](https://git-scm.com/download/win)
2. Windows Users: Install Windows Subsystem for Linux 2 (WSL): [Guide](https://learn.microsoft.com/en-us/windows/wsl/install)
    - the WSL command prompt can be activated by entering `wsl` into any command prompt
3. Windows Users: update all packages on WSL by activating WSL (type `wsl` into a command prompt) and run `sudo apt-get update && sudo apt-get upgrade`
    - you will be prompted for your WSL password, not Windows password
4. Install Docker: [Link](https://docs.docker.com/engine/install/)
    - Windows Users: enable the WSL integration setting: `Settings >> Resources >> WSL Integration`

**Setting up the Compilation Environment**

Windows Users: do these steps within WSL using a WSL command prompt (type `wsl` into a command prompt to enter WSL)
1. Make a folder for Solar Car code on your machine, if not done already, and `cd` into it
2. Clone Rivanna3 into that directory using `git clone https://github.com/solarcaratuva/Rivanna3.git`
3. Change directory into the cloned directory (`cd Rivanna3`)
4. Run the following command: `docker run --name Rivanna3_compile -it -v $(pwd)/:/root/Rivanna2:Z ghcr.io/solarcaratuva/rivanna2-env`
5. Run `cd Rivanna2` then `mbed-tools deploy`

**Actually Compiling**

1. Attach the command prompt to the container by running `docker attach Rivanna3_compile`
    - Docker Desktop and the *Rivanna3_compile* container must be running
2. Run `cd Rivanna2` then `./compile.sh`
    - compilation should take under a minute

Compiled files are stored in the `cmake_build` directory. <br>
Remember that this compiles the *current* Git branch only. 

**What is Actually Happening**

1. A Docker container is an isolated space on your computer, only sharing foundational system files with the rest of the computer, as well as limited computational resources. The isolation of the container ensures that everyone has the EXACT same environment when compiling, which prevents phantom, often unsolvable errors from occurring.
2. The `compile.sh` script runs `mbed-tools compile -m UVA_SOLAR_CAR -t GCC_ARM`, which uses MbedOS's own compilation system to compile the code.
3. The compiled code is stored, ready for upload, and reducing the number of files needed to be compiled in the future.

# Uploading

**Software Installation: Windows**

1. Download [ST Tools](https://github.com/stlink-org/stlink/releases). Note that you will install this on Windows, not WSL
    - Recommended: download `stlink-1.7.0-x86_64-w64-mingw32.zip` from version `1.7.0`. Version `1.8.0` has dependency issues and doesn't have any apparent features not in `1.7.0`
2. Unzip the zip file and copy the unzipped folder to `Program Files (x86)`
3. Inside the unzipped folder there is a `bin` folder, add this to path
    - [Guide: Adding values to Path](https://www.eukhost.com/kb/how-to-add-to-the-path-on-windows-10-and-windows-11/)

Verify: Open a new command prompt and enter `st-flash --version`. This should print the software version. 


**Software Installation: Mac**

Run the command `brew install stlink`

Verify: Open a new command prompt and enter `st-flash --version`. This should print the software version. 

**Actually Uploading**

1. Open the *Rivanna3* folder
    - Windows Users: this should be stored in WSL; open in WSL, not through the Windows file explorer
2. In the *Rivanna3* folder, run `python3 upload.py board`, replacing *board* with the name of the board you are uploading to

**What is Actually Happening**

1. Windows Users: the WSL file system is added as a network drive, named `W:`, allowing a program running in Windows to easily access files stored in WSL
2. The appropriate `st-flash` command is run
    - Windows Users: this is run in Windows, not WSL
3. Windows Users: the network drive `W:` is deleted
