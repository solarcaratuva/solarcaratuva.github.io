# GitHub Tutorial
This page contains information on how to install the necessary software for working with GitHub and a quick guide on how to download and commit changes to a repository.
## Software
### Windows
A popular option for using GitHub on Windows is Git Bash because it provides an easy to use CLI for pulling from and committing to the repo. 
The link to download Git Bash can be found [here](https://gitforwindows.org/).
### Mac and Linux
I don't have much knowledge on working with Git on Mac or Linux, so if someone using Mac/Linux sees this please feel free to add your suggestions.
## Quick Start Guide
### Downloading the Repository
After creating your Git environment, the first step to start working is cloning a repository to download all of its files locally. 
This can be done by downloading a zip file directly from the repositories website, or by using the command `git clone https://github.com/address-of-repo`.  
  
After initially cloning the repository, you can now update your local download using the command `git pull` while in the repository directory.
### Committing to the Repository
To commit your local changes to the repository, follow the three following steps to stage, commit and push your changes.
#### 1. Stage Changes  
Use the command `git add filename` to stage your changes, which simply means preparing the files to commit.
#### 2. Commit Changes
Use the command `git commit -m "description of changes"` to commit your changes. The `-m` flag allows for a message to be written describing the changes you made.
#### 3. Push Changes
Use the command `git push` to push your changes to GitHub, which finalizes your changes in the repository.  
  
There are many more complex features that GitHub has, but these commands are the only ones necessary for downloading and uploading files to and from a repository. Feel free to look
through [this guide](https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html) to explore what else GitHub has to offer!
