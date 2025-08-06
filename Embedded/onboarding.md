---
title: Onboarding
nav_order: 11
parent: Embedded
has_children: false
---
# 2025 Embedded Onboarding

**Welcome to the Solar Car Team and the Embedded Subteam!** Onboarding will consist of the following action items. Complete them in this order: 
1. downloading and configuring software
2. learning about Git
3. the onboarding project

This page will serve as the hub for onboarding, similar to how this wiki is a hub for the Embedded Subteam's info. You should familiarize yourself with the guides and datasheets in [Documentation](https://solarcaratuva.github.io/Embedded/documentation.html), so you know what is available there. 

For the first month or so, PowerPoints will be presented at the start of the Sunday meetings to help bring new members up to speed. The goal of these presentations is not to teach new members everything they will need, but rather create a foundation so new members know how things work in general and know what questions to ask. These will be posted in [Documentation](https://solarcaratuva.github.io/Embedded/documentation.html) afterwards. 

New members should research the basics of C++ and Python if they are unfamiliar with these programming languages. Here are some helpful resources:
- [C++ Basics](https://www.w3schools.com/cpp/default.asp)
- [Python Basics](https://www.w3schools.com/python/)

## Downloading Software

1. Create a GitHub account and Discord account, if you don't already have one.
2. Install [Python](https://www.python.org/downloads/)
3. Install [VS Code](https://code.visualstudio.com/download).
4. Complete the software installation and setup on [this page](https://solarcaratuva.github.io/Embedded/riv3_compile_upload.html). Complete all of *Compiling*, and complete *Uploading* and *Monitoring* software installation. 
5. Windows users: install [USBipd](https://learn.microsoft.com/en-us/windows/wsl/connect-usb)
6. Authenticate your GitHub account on Git: follow [these instructions](https://docs.github.com/en/get-started/git-basics/caching-your-github-credentials-in-git#github-cli)

## Learning about Git

[Git](https://en.wikipedia.org/wiki/Git) is the industry-standard verison control system which we use to collaberate effectively when coding. Work through [this guide](https://www.w3schools.com/git/default.asp?remote=github), completing the following sections:
- Git Tutorial: all but *Git Config*
- Git and GitHub: from *Pull from GitHub* to *Push branch to GitHub*
- Git Contribute: *Git Clone from GitHub* and *GitHub Send Pull Request*
- Git Undo: *Git Reset*
- Git Advanced: *Git .gitignore* and *Git Submodules*


## Onboarding Project

- The project will be a short exercise where new members can interact with the Embedded codebase.
- Every individual should complete their own project (but can ask others for help); this will probably be the only time you work on a project completely independently while on the team.

**Directions** TODO xxx
1. Open the *Rivanna3* project on your computer, switch branches to the `onboarding_project` branch (`git checkout onboarding_project`)
2. make a new branch from this called `onboarding_project_yourname` (`git branch onboarding_project_yourname`) and switch to it using git checkout
3. Open `DriverBoard/src/main.cpp` and go to the `signalFlashHandler` function
4. Read the instructions in the comments, and implement the described logic
5. When you have reached a milestone:
    - compile *Rivanna3* to ensure your code in syntactically correct for C++ (compilation warnings are fine, compilation failure is not)
    - commit and push the changes to your branch
6. When you are done or have questions, talk to Colby or an Onboarding TA
