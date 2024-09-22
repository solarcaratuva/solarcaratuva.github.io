---
title: Onboarding Software Set Up
nav_order: 3
parent: Hardware Integration
has_children: false
---

# Software and the Steps to Set it Up
This section talks about the software needed to be successful and an integral member of the HI subteam. We will also explore how to set-up repositories from CadLab on your remote desktop.

## Visual Studio Code
One important piece of software we recommend downloading is Visual Studio Code. The website to download Visual Studio Code is linked below.
[Visual Studio Code Download Link](https://code.visualstudio.com/download)
When downloading the software, make sure to choose the configuration that works best for your devivce. Once downloaded, make sure to click on the package and install it and open onto your laptop. For the purpose of HI team, you will not be needing to connect to a remote SSH. However for other classes at UVA especially in the CS department, it is strongly recommended that you install the SSH for those classes into Visual Studio Code. 

Visual Studio Code will provide an avenue to handle all git for the CadLab repository. It also allows for you to see the raw breakdown of the files that are edited in KiCad. Visual Studio Code will also act as an avenue to handle any merge conflicts that arise when updating the branches. To avoid this as much as possible, make sure to pull any new changes onto your branch and make sure the submodule is updated to the most recent version. More information on this will be included on the Git practices subpage. 

## Git
Git is a version control platform that must be downloaded onto your local terminal for both MacOS, Windows and Linux users. We will be setting this up to help move files and changes between everyone's remote deaktop. This allows everyone to be able to contribute to the HI subteam efforts from anywhere (as long as you follow the Git expectations for HI).
### MacOS Users
For MacBook users, there are a couple of possible options to explore. Choose the option which makes you most comfortable. The first option is to download XCode to leverage the command line tool arguments provided and the added benefit of git implementation involved. The other option which allows you to utilize git from your terminal, involves installing homebrew. The command to install home brew is located at this [link](https://git-scm.com/download/mac). All you would need to do is copy and paste the command into your terminal.
Before you can utilize the beauty of CadLab and KiCad, you must link your GitHub account to a CadLab account. The steps are stated below.
### Windows Users


### Github to CadLab Connection
1. Go to the CadLab [website](cadlab.io). 
2. Set up an account with CadLab by signing in with GitHub. This will reroute you to GitHub. 
3. Follow the steps that GitHub needs to verify the account and provide the necessary permissions to CadLab for both to be synced together. Your GitHub and CadLab accounts are officially connected!!

After all of these steps have been completed, you are ready to start exploring CadLab and KiCad.

## Cadlab
Before we getted started on CadLab features, make sure your github and cadlab account are linked as seen above. Thie sill the only way that you will be able to work in the Solar Car CadLab repository. Once these two are linked, go ahead and reach out to the HI lead for next steps and permission to join the repository. Once you have access, make sure to bookmark the page since it will be accessed fairly often. 

To continuously access CadLab seamlessly, please bookmark the Solar Car at UVA Cadlab main directory page. This will make it easier to go between repositories. 

For the next couple steps, make sure to have CadLab bookmarked and Git installed on your local device. First you would go into the Solar Car CadLab repository and access the specific directory. For the 2024-2025 academic, please access Rivanna_3. 

### Setting up the CadLab Repository onto Local Desktop

1. Open the desired repository directory. 
2. Copy the Git URL in the top left of the page as seen in the image below. When copying over the Git Url, make sure to access the right branch to be copied over. We will discuss this in detail later on this page.  

[image](/solarcaratuva.github.io/HI/images/Screenshot%202024-09-21%20at%204.06.02 PM.png)

3. On your local desktop, create a folder to house all Solar Car files to ease the transition and keep everything clean. 
        mkdir Solar_Car_UVA
4. Cd into this folder and paste the copied Git Url into your terminal. This will popuate all of the files in that repository onto you local desktop. 

To streamline the concept of branching, the following section explores how branching will be initiaited and maintained below. 

**concept of branching in CadLab**
Within CadLab, there are two types of branching that can be created: a version branch or a feature branch. To create a new branch, click on the plus button in the top left corner of the screen. It will get you to the following page:

[image](/solarcaratuva.github.io/HI/images/Screenshot%202024-09-22%20at%2012.33.08 PM.png)

For our intents and purposes, most branches created will be implmeneitng a feature of the PCB boards. When we finish and deploy a set of PCB boards to production then we will create a version branch for the next iteration of the boards. Unless otherwise specified, make sure to create a feature branch. The name of the branch will be the thing you are trying to implement. The source branch will be specified so make sure to be using the right branch that you want to branch off of. 

## KiCad
Once CadLab has been set-up and the files from the repository are pulled to your local device, make sure to have a folder structure to be able to organize all the files you will be needing to keep track of in Solar Car. It is better to set this up earlier than later to maintain the maximum efficiency. 

### Downloading KiCad
1. The first step to download files  is to follow this [link](https://www.kicad.org/download/)
2. Specify the operating system used by your laptop and folow the set-up instructions given by KiCad

After KiCad is downloaded, you want to make sure that you are working on the predefined PCB and schematic files. We will discuss how to open them in the next section. 

### Opening Files in KiCad

1. Open your KiCad program
2. You will see the following screen. You want to click on the second icon from the top on the left most side bar. 

[image](/solarcaratuva.github.io/HI/images/Screenshot%202024-09-22%20at%2012.41.53 PM.png)

**Note** A file has already been uploaded in the above screenshot. This is not a default screen.
3. Specify the file/folder you want loaded into KiCad by giving it the directory path to it. The file will be of .kicad_pro type file.  
4. Now that the file has been opened onto KiCad, you should be able ot see everything associated with that board. Feel free to move in between the files. Everytime you are done, make sure to push your changes to the CadLab repository so everyone can have access to the latest changes. 

**Note:**
    To create a new  file in KiCad from scratch, access the icon above the one listed above.  It will be the top most icon on the left most side of the page. 

