---
nav_order: 1
parent: Git
---

# Git Quick Start Guide

## Working with Repositories
Git is an extremely powerful version control software and has many more complex features than is covered here. The commands covered are the basic requirements to work with a Git repository. Feel free to look
through [this guide](https://dont-be-afraid-to-commit.readthedocs.io/en/latest/git/commandlinegit.html) to explore what else Git has to offer!

### Cloning
After setting up your Git environment, the first step to start working is cloning a repository to get a local version of the project files. 
This can be done by using the command `git clone <repository-address>`. The `<repository-address>` is typically either an HTTPS link or an SSH URI such as `git@github.com:user/repository.git`. 
  
### Status
The `git status` command is useful for tracking changes in the repository and the currently staged changes.

### Committing
To commit your local changes to a remote repository (such as a GitHub repository), follow the three following steps to stage, commit and push your changes.
#### 1. Stage Changes  
Use the command `git add <path>` to stage changes in a file or directory located at `<path>`. In other words, this is selecting the desired changes to commit. The command `git add --all` stages all changes.
#### 2. Commit Changes
Use the command `git commit -m "description of changes"` to commit your changes. The `-m` flag allows for a message to be written describing the changes made.
#### 3. Push Changes
Use the command `git push` to push changes to the remote repository, which updates your changes there.

### Pulling
After initially cloning the repository, the local repository can be updated with the latest changes from the remote by using the command `git pull` while in the local repository directory.
