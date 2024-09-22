---
title: CadLab Repository Structure for Rivanna 3
nav_order: 4
parent: Hardware Integration
has_children: false
---
# Introduction
After much request and suffering, we have updated the CadLab repository structure. Please read on to see the amazing new updates to streamline HI schematic and PCB design.

## Submodules
Submodules are leveraged where they are imported libraries that we can set a pointer to a specific commit. When specifying this pointer, we are given the option to use everything that has been implemented and added in that commit. It exists as a simpler way to prevent constant merge conflicts.  At the surface level, submodules allowing for nesting of repositories based on commit history. 

All libraries used in the PCB design layout will be included as submodules. In our PCB implementation, there will be 3 submodule folders corresponding similarly with the Rivanna 3 CadLab repo. The three submodule libraries will be titled the Telemetry, STM and Power Board. The Telemetry submodules will contain all library needs for the telemetry board. The same thing will occur for the power board. The STM submodule will contain library items that are need for all boards across the car. This submodule contains generalized parts that are used everywhere. 

For more information on submodules, follow this [link](https://www.youtube.com/watch?v=8Z4Cmhji_FQ)


## Rivanna 3 Repo Structure

For the PCB boards, there are three folders: Experiments, General and STM boards. The Experiments folder will contain any boards that we create and want to run testing on. This is group of boards that will siply exist for the reason to try out new ideas and create new innovative ways to approach board design for the car.  The General boards folder contains any boards that are placed across the car such as a Modular STM board ( allows for the attaching and detaching of the STM) and the distribution boards. The STM boards folder is comprised of the Power, Telemetry and Template boards. The boards in this folder are grouped together based on the usage of STM. The Power and Telemtry folder will have it srespective layouts while the Template folder within the STM boards folder will have generalized designs on it. When adding in or editing things within the repository, make sure to do so with a branch that specifies the name of what is getting implemented.

**TLDR**

    If you have not had a chance to read any of the information above, this is the most important thing takeaway: The repository is structured due to function and library usage with nested folders specifying exactly what should go in the folder. 


