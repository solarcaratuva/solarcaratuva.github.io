---
nav_order: 2
parent: Deprecated
---

# Importing Template Repositories

Because we decided to combine all of the different boards into one repository, these instructions are now deprecated. However, they are included here in case we ever decide to use template repositories again.

## Importing the Template Project (DEPRECATED)

In the following instructions, replace all instances of "Team" with a subteam board name (PowerAux, Motor, ECU, or Solar).

1. Duplicate the [TemplateCode repository](https://github.com/solarcaratuva/TemplateCode) following the instructions [here](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository#mirroring-a-repository). 
    1. `$ git clone --bare https://github.com/solarcaratuva/TemplateCode.git`
    1. `$ cd TemplateCode.git`
    1. Create a new repository in the [UVA Solar Car organization](https://github.com/solarcaratuva), named TeamCode.
    1. `$ git push --mirror https://github.com/solarcaratuva/TeamCode.git`
    1. `$ cd ..`
    1. `$ rm -rf TemplateCode.git`
1. Clone the new repository (TeamCode) to your local machine.
    1. `$ git clone https://github.com/solarcaratuva/TeamCode.git`
    1. `$ cd TeamCode`
1. Add the TemplateCode repository as a remote of the new TeamCode repository following the instructions [here](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork).
    1. `$ git remote add upstream https://github.com/solarcaratuva/TemplateCode.git`
1. Now to sync the new TeamCode repository with changes in the TemplateCode repository, simply fetch and merge the remote called upstream by following the instructions [here](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).
    1. `$ git fetch upstream`
    1. `$ git checkout master`
    1. `$ git merge upstream/master`
