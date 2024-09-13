---
title: Onboarding
nav_order: 3
parent: Embedded
has_children: false
---
# Onboarding

*This page is written for 2024 onboarding, directed by Colby Wise; unlike other pages, this page is therefore not timeless.*

**Welcome to the Solar Car Team and the Embedded Subteam!** Onboarding will consist of these main parts:
1. downloading and configuring software
2. listening to onboarding presentations
3. independent research
4. the onboarding project

This page will serve as the hub for onboarding, similar to how this wiki is a hub for the Embedded Subteam's info, as well as other subteam's info. You should familiarize yourself with the guides and datasheets in [Documentation](https://solarcaratuva.github.io/Embedded/documentation.html), so you know what is available there. 

## Downloading Software

1. Create a GitHub account and Discord account, if you don't already have one.
2. Go to the [Onboarding Script](https://github.com/solarcaratuva/Onboarding_Installer) and follow the instructions to start the script. This program will download and configure most of the required software. 
3. While that is happening, read through the `Readme` for the [Rivanna3 project](https://github.com/solarcaratuva/Rivanna3). This is our embedded codebase for this year.
    - this project is our biggest project by A LOT, so it is normal to feel overwhelmed by its size and complexity 
    - your goal right now should be to read the entire `Readme`, then get a feel for where stuff is in the codebase
4. Once the Onboarding Script has finished, see if any of the commands have failed
    - if none have failed: you have completed this section
    - if some have failed: run the onboarding script again. There are checks in it to ensure software isn't installed twice by accident.
    - if some have failed and you ran the script twice already: you will need to manually install / configure the failed steps. Ask for help if needed.

## Presentations

For the first month or so, PowerPoints will be presented at the start of the Sunday meetings to help bring new members up to speed. The goal of these presentations is not to teach new members everything they will need, but rather create a foundation so new members know how things work in general and know what questions to ask. These will be posted in [Documentation](https://solarcaratuva.github.io/Embedded/documentation.html) afterwards. 

## Independent Research

New members should research the basics of C++ and Python if they are unfamiliar with these programming languages. Here are some helpful resources:
- [C++ Basics](https://www.w3schools.com/cpp/default.asp)
- [Python Basics](https://www.w3schools.com/python/)

New members should ask questions to other team members, their team lead (Colby), or the internet when they are confused. Asking questions is an essential part of learning. <br>
New members are also recommended to skim through the Embedded Codebase outside of meetings, and try to understand how it works, doing light research as they feel necessary. 

## Onboarding Project

- The project will be a short exercise where new members can interact with the Embedded codebase.
- Every individual should complete their own project (but can ask others for help); this will probably be the only time you work on a project completely independently while on the team.
- Specific directions / goals will be given in person. 

**Directions**
1. Open the *Rivanna3* project on your computer, switch branches to the `onboarding_project` branch (`git checkout onboarding_project`)
2. make a new branch from this called `onboarding_project_yourname` (`git branch onboarding_project_yourname`) and switch to it using git checkout
3. Open `DriverBoard/src/main.cpp` and go to the `signalFlashHandler` function
4. Read the instructions in the comments, and implement the described logic
5. When you have reached a milestone:
    a. compile *Rivanna3* to ensure your code in syntactically correct for C++ (compilation warnings are fine, compilation failure is not)
    b. commit and push the changes to your branch
6. When you are done or have questions, talk to Colby or an Onboarding TA
