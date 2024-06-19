---
parent: PCB
---

# Importing

This document describes how to import the Template board into a new or existing PCB in KiCad. For doucmentation on project library management, see the [libraries docs](libraries.md).

## How to Start a New PCB

Choose whether to keep the commit history from the Template repository or throw it away, and follow the instructions for the respective choice.

### Keeping Commit History

Use Git to duplicate the entire repository (note that this is different than cloning the repository). Create a new repository on CADLAB and follow the instructions [here](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/duplicating-a-repository#mirroring-a-repository) to duplicate the Template repository into the new repository.

After the entire repository is duplicated, feel free to change all files named `Template.*` or `Template-cache.lib` to a name fitting the new repository.

### Throwing Away Commit History

Create a new repository on CADLAB and copy over all files and folders from the Template repository into the new repository. Make sure to copy over the `.gitignore` file too.

After the entire repository is duplicated, feel free to change all files named `Template.*` or `Template-cache.lib` to a name fitting the new repository.

## How to Copy into an Existing PCB

First copy the library files, then copy the schematic files. Make sure to copy over any changes in the `.gitignore` file too.

### Copying the Library Files

Copy the `Libraries/UVA_SolarCar_Template/` folder to the existing PCB project (make sure that the `Libraries/` folder is at the same level as the existing PCB project's `.pro` file). If the existing project already has a `Libraries/UVA_SolarCar_Template/` folder, it can still be copied over and overwritten.

If this is the first time copying the library files, follow the next two steps. Otherwise, move on to [Copying the Schematic Files](#copying-the-schematic-files).

Next, add the `Libraries/UVA_SolarCar_Template/UVA_SolarCar_Template.lib` file as a Project Symbol Library to the existing PCB project in KiCad:

1. Go to `Preferences > Manage Symbol Libraries...`
1. Go to the `Project Specific Libraries` tab
1. Click on the folder symbol near the bottom left (2nd from the left, it says `Add existing library to table` when hovering over it) and select the file `Libraries/UVA_SolarCar_Template/UVA_SolarCar_Template.lib`
1. Check that the library path is correct, it uses the `${KIPRJMOD}` substitution, and uses `/` instead of `\`
1. Click `OK`

Finally, add the `Libraries/UVA_SolarCar_Template/UVA_SolarCar_Template.pretty/` folder as a Project Footprint Library to the existing PCB project in KiCad:

1. Go to `Preferences > Manage Footprint Libraries...`
1. Go to the `Project Specific Libraries` tab
1. Click on the folder symbol near the bottom left (2nd from the left, it says `Add existing library to table` when hovering over it) and select the folder `Libraries/UVA_SolarCar_Template/UVA_SolarCar_Template.pretty/`
1. Check that the library path is correct, it uses the `${KIPRJMOD}` substitution, and uses `/` instead of `\`
1. Click `OK`

### Copying the Schematic Files

Use KiCad's "Append Schematic Sheet Content" tool to import relevant schematic parts into an existing PCB.

To do this:

1. In the `Template.sch` file, create a new heirarchical sheet and call it `export.sch`.
2. Copy-paste all components to export into `export.sch`.
3. Save.
4. Open the existing PCB schematic to import into.
5. Create a new heirarchical sheet and call it `import.sch`.
6. In `import.sch`, click on `File > Append Schematic Sheet Content...`
7. Find and open `export.sch`.
8. If asked, use relative path instead of absolute path.
9. If an error message saying "A duplicate library name that references a different library exists in the current library table. This conflict cannot be resolved and may result in broken symbol library links for the schematic." appears, do NOT continue the load. Cancel it and instead do the following:
    - This error message only appears if trying to append a component for which an external footprint/schematic symbol was used. If importing such components, delete them from `export.sch` and manually add them into `import.sch` after appending.
10. It should now be possible to copy-paste any relevant parts of the imported schematic to the existing PCB schematic.
11. Delete any unnecessary heirarchical sheets and save.

