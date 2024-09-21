---
title: Best GIT Practices for Hardware Integration
nav_order: 2
parent: Hardware Integration
has_children: false
---
#  Git Introduction


Git can be hard to navigate. This page has been created to help HI members to utilize good git practices to prevent extraneous merge conflicts and allow more seamless work on the PCB boards. This page does not include information on how to connect GitHub to CadLab. For this there will be a separate page that is linked on the side.


# Git Commands To Use
Included below is a table of git commands to leverage. It will be a great reference and tool to be able to use not only for Solar Car but also for any future endeavours. Please bookmark this.

(https://drive.google.com/file/d/1uMw3iIvGw6jcLmkmXuhwhxy82nauLgIG/view?usp=sharing)

## Submodules Handling
Since our CadLab repository structure for PCB boards and its respective schematics involve submodules, the following command is extremely important to run each time you work on making change: 

        git submodule update  --remote

This command allows for you to update your submodule to its latest version to deploy and utilize in your designs. For more information on the CadLab repository structure. 

# Best Git Practices


Utilizing good git practices is monumental in allowing for the team to work efficiently. It may seem like a lot but it will become more easy with practice. Below there is a link graciously provided by an Software Development Essentials textbook spearheaded by Professor McBurney from UVA. Please read the link in its entirety to be most prepared for PCB designs.


(https://sde-coursepack.github.io/modules/construction/Best-Practices/)




# Credit/Acknowledgement


We would like to express credit and thanks to Professor McBurney for providing resources on git. We would like to acknowledge that everything from the online textbook is leveraged for educational purposes.

https://www.geeksforgeeks.org/how-to-update-git-submodule-to-latest-commit-on-origin/

