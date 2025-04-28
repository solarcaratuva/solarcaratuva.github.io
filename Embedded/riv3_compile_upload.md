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
    - Windows Users: When you first open WSL, the working directory will be `/mnt/c/Users/username`. This is inside your Windows filesystem. You should NOT make the folder here; if you do, compilation will be VERY slow. You should run `cd ~` to go to your Linux home directory and make the folder there; the path of the folder should be similar to `~/solarCarRepo` or `/home/username/solarCarRepo`. 
2. Clone Rivanna3 into that directory using `git clone https://github.com/solarcaratuva/Rivanna3.git`
3. Change directory into the cloned directory (`cd Rivanna3`)
4. Run the following command: `docker run --name Rivanna3_compile -it -v $(pwd)/:/root/Rivanna2:Z ghcr.io/solarcaratuva/rivanna2-env`
5. Run `cd Rivanna2` then `mbed-tools deploy`

**Actually Compiling: using the script option**

In the *Rivanna3* folder, run the compile script, `compile.py`. See the API below:

Arguments: 
- `-c`, `--clean`: flag, optional. Deletes previous build files before compiling, forcing the compiler to do a clean compile.
- `-s`, `--silent`: flag, optional. Will stop the compile command from printing debug info and showing the progress bar.

Example: `python3 compile.py -c`.

Note that this script won't work if the container wasn't made with the `docker run...` command from above, or with old versions of Docker. 

**Actually Compiling: manual option**

1. Start the container by running `docker start Rivanna3_compile`
1. Attach the command prompt to the container by running `docker attach Rivanna3_compile`
    - Docker Desktop must be running
2. Run `cd Rivanna2` then `./compile.sh`
    - compilation should take under a minute

Compiled files are stored in the `cmake_build` directory. Remember that this compiles the *current* Git branch only. 

**What is Actually Happening**

1. A Docker container is an isolated space on your computer, only sharing foundational system files with the rest of the computer, as well as limited computational resources. The isolation of the container ensures that everyone has the EXACT same environment when compiling, which prevents phantom, often unsolvable errors from occurring.
2. The `compile.sh` script runs `mbed-tools compile -m UVA_SOLAR_CAR -t GCC_ARM`, which uses MbedOS's own compilation system to compile the code.
3. The compiled code is stored, ready for upload, and reducing the number of files needed to be compiled in the future.

# Uploading

**Software Installation: Windows**

1. Run `wget https://github.com/stlink-org/stlink/releases/download/v1.8.0/stlink_1.8.0-1_amd64.deb` in WSL to download the package installer
2. Run `sudo dpkg -i --force-overwrite ./stlink_1.8.0-1_amd64.deb` in WSL to install the package; this will take a few minutes
3. Run `rm stlink_1.8.0-1_amd64.deb` in WSL to delete the installer when finished
4. Verify: Open a new command prompt in WSL and run `st-flash --version`. This should print `v1.8.0`. 
    - GLIBC Error: Your version of Ubuntu is too old, [update Ubuntu](https://documentation.ubuntu.com/server/how-to/software/upgrade-your-release/index.html).
5. Install [usbipd](https://learn.microsoft.com/en-us/windows/wsl/connect-usb) in Windows

**Software Installation: Mac**

1. Run the command `brew install stlink`
2. Verify: Open a new command prompt and enter `st-flash --version`. This should print `v1.8.0`. 

**Actually Uploading**

1. Open the *Rivanna3* folder
    - Windows Users: this should be stored in WSL; open in WSL, not through the Windows file explorer
2. In the *Rivanna3* folder, run the upload script, `upload.py`. See the API below:

Arguments:
- `board`: positional, required argument. Specifies which board you are uploading to.
- `-p `, `--sudo`: flag, **required for Windows users**. The flag should be followed by your WSL password.
- `-s`, `--silent`: flag, optional. Will stop the upload command from printing debug info and showing the progress bar.

Example: `python3 upload.py power -p my_password`

**What is Actually Happening**

1. Windows Users: the ST-Link is attached to WSL, giving WSL access to it. Commands from `usbipd.exe` are used, which are called from WSL but actually run in Windows. 
2. The appropriate `st-flash` command is run.
    - Windows Users: the command is run as *sudo*, because your WSL user account isn't given permission to use the ST-Link.
3. Windows Users: the ST-Link is detached from WSL.

# Monitoring

A serial monitor, such as `monitor.py`, can be used to read debug log statements from the microcontrollers. 

These log messages look like:
```log
00:00:02 DEBUG /root/Rivanna2/Common/src/MainCANInterface.cpp:40: Sent CAN message with ID 0x406 Length 6 Data 0x5b1e5e010000
00:00:02 DEBUG /root/Rivanna2/Common/src/MainCANInterface.cpp:40: Sent CAN message with ID 0x200 Length 8 Data 0x0080010000000000
00:00:02 DEBUG /root/Rivanna2/Common/src/MainCANInterface.cpp:40: Sent CAN message with ID 0x406 Length 6 Data 0x321f1e000000
00:00:03 DEBUG /root/Rivanna2/Common/src/MainCANInterface.cpp:40: Sent CAN message with ID 0x300 Length 1 Data 0x04
```

`monitor.py` should be run in WSL for Windows Users. *Pyserial* must be installed, run `python3 -m pip install pyserial`. The script has the following arguments:
- `-p `, `--sudo`: flag, **required for Windows users**. The flag should be followed by your WSL password.
- `-l`, `--log`: flag, optional. The flag should be followed by a file path. Logs all messages to the file, creates the file if it doesn't exist, appends if it does exist.
- `-s`, `--silent`: flag, optional. Will stop any messages from being printed to the terminal. Should be used with *log*.

Example: `python3 monitor.py -p my_password -l logfile.log`
