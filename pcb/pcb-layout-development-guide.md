---
nav_order: 1
parent: PCB
---

# PCB Layout Development Guide
## Overview
This guide walks through how to start working on a layout for a PCB that already has a layout file setup (a file with the .kicad_pcb extention). A very useful part of Git's design is using branches. Branches allow you to work on your own 'copy' of the master code and still retain the master code. When you make a new branch, it initially starts on your local machine and then you can push the branch to the remote server (GitHub, Cadlab, etc.). This allows multiple versions of the code/kicad files to exist at the same time for anyone to see.

IMPORTANT NOTE: This was originally for Motor board, so anywhere where there is a specific project, switch that to whatever you are trying to work on if it's not Motor.

## Directions

1. Clone the repository with the PCB files (If you already have the folder for the project on your local machine, skip this step)

Go to a folder you want to put the files in and clone the files 

(make sure to replace ${yourUsername} with yours. you can find this link at https://cadlab.io/project/23201/master/files at the Git URL in the upper lefthand corner)

`git clone --branch master https://${yourUsername}@git.cadlab.io/Solar-Car-at-UVa/Motor.git`

2. Make a new local branch

(cd into the repository first, put your name in the branch name)

`git checkout -b ${your-branch-name}`

3. Start layout work

Open up Motor.pro, then open Motor.kicad_pb to edit the layout and Motor.sch as well to see the function of each of the components

4. Save your work (all the time) and for a final time once you finish the work section

5. Commmit your changes

(go into the Motor directory)

`git add . # stage all file changes`

`git commit -m "${meaningful commit message}" # commit the staged changes`

6. Push your changes to your branch on the remote server (note: this will not affect the master branch so don't be afraid to do it for anyone)

`git push origin ${your-branch-name} # push your local branch to remote`

## Starting another work session

In case someone has made any changes on your branch in between work sessions, first pull any changes

(cd into the repository)

`git pull`

Then you can start working and when you're done repeat steps 4 - 6.