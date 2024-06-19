---
parent: PCB
---

# Libraries

This document describes the project library management. For documentation on how to import the Template PCB into a new or existing PCB in KiCad, see the [importing docs](importing.md).

## Organization

All symbol and footprint libraries are contained in the `Libraries/` directory.

In this Template project, there is only one sub-directory in the `Libraries/` directory: `Libraries/UVA_SolarCar_Template/`. This is where common components used by all teams are placed.

After importing the Template PCB, all teams should place their team-specific components in a different sub-directory, named `Libraries/UVA_SolarCar_TeamName/`. New team-specific components should never be added to the `Libraries/UVA_SolarCAr_Teamplate/` directory.

## Adding New Components

There are two main steps for adding new components. The first step is to create the team-specific library (if adding a team-specific component). This only needs to be done once. The second step is to add the component into KiCad using [LibraryLoader](https://www.samacsys.com/library-loader/). This must be done each time a new component is added.

### Creating a Team-specific Library

1. Create a new sub-directory in the `Libraries/` directory, name it `Libraries/UVA_SolarCar_TeamName/`, where `TeamName` is replaced with the team's name
1. Download LibraryLoader. Follow the [help page](https://www.samacsys.com/library-loader-help/) for more info
1. In LibraryLoader's KiCad `Settings`, change the `Directory` to `Libraries/UVA_SolarCar_TeamName/` created earlier
1. Ensure that the `Downloads Folder` in LibraryLoader is set to the folder that web downloads go to automatically
1. Download the new component's ECAD file. LibraryLoader should automatically add the downloaded component to the `Directory` specified earlier as a KiCad Library
1. In KiCad, add the Symbol Library
    1. Go to `Preferences > Manage Symbol Libraries...`
    1. Go to the `Project Specific Libraries` tab
    1. Add the file `Libraries/UVA_SolarCar_TeamName/SamacSys_Parts.lib` by clicking on the folder symbol on the bottom left (2nd from the left, says `Add existing library to table` when hovering over it)
    1. Change the `Nickname` to `UVA_SolarCar_TeamName`, where `TeamName` is replaced with the team's name
    1. Click `OK`
1. In KiCad, add the Footprint Library
    1. Go to `Preferences > Manage Footprint Libraries...`
    1. Go to the `Project Specific Libraries` tab
    1. Add the directory `Libraries/UVA_SolarCar_TeamName/SamacSys_Parts.pretty/` by clicking on the folder symbol on the bottom left (2nd from the left, says `Add existing library to table` when hovering over it)
    1. Change the `Nickname` to `UVA_SolarCar_TeamName`, where `TeamName` is replaced with the team's name
    1. Click `OK`
1. Delete the example symbol, footprint, and 3D model that was included with LibraryLoader (optional)
    1. In KiCad, open the Symbol Editor (2nd button on Home Screen's right side, looks like OpAmp)
        1. Search `uva`
        1. Delete the example symbol
    1. In KiCad, open the Footprint Editor (2nd button on Home Screen's right side, looks like OpAmp)
        1. Search `uva`
        1. Delete the example symbol
    1. In the file explorer, delete the file `Libraries/UVA_SolarCar_TeamName/SamacSys_Parts.3dshapes/EXAMPLE.stp`, where `TeamName` is replaced with the team's name and `EXAMPLE` is replaced with the example part number

### Adding the Component into KiCad

This is done almost entirely automatically by LibraryLoader when downloading the new component's ECAD model, as described above. The only thing Library Loader does not handle well is the 3D model: it uses an absolute path for each 3D model rather than a relative path (on Windows it also uses `\` instead of `/`, which will not work on Mac and Linux).

To fix this follow the steps below:

1. Import into KiCad using LibraryLoader
    1. In LibraryLoader's KiCad `Settings`, change the `Directory` to `Libraries/UVA_SolarCar_TeamName/` if adding a team-specific component, or to `Libraries/UVA_SolarCar_Template/` if adding a common component used across all teams
    1. Ensure that the `Downloads Folder` in LibraryLoader is set to the folder that web downloads go to automatically
    1. Download the new component's ECAD file. LibraryLoader should automatically add the downloaded component to the `Directory` specified earlier as a KiCad Library
1. Fix the 3D model's path in KiCad
    1. Go to the `Footprint Editor`
    1. Search `uva`
    1. Double click on the newly added component
    1. Go to `Footprint Properties` (the first setting icon on the top or `Edit > Footprint Properties...`)
    1. Go to the `3D Settings` tab
    1. Click on the folder icon (in between the + icon and the trash icon) and add the file `Libraries/UVA_SolarCar_TeamName/SamacSys_Parts.3dshapes/PartNumber.stp` if adding a team-specific component, or the file `Libraries/UVA_SolarCar_Template/UVA_SolarCar_Template.3dshapes/PartNumber.stp`, where `PartNumber` is replaced by the part number of the newly added component
    1. Ensure that the added model is the correct one, uses the `${KIPRJMOD}` substitution, and uses `/` instead of `\`
    1. Remove the old model by clicking on it and clicking the trash icon (to the right of the folder icon)
    1. Click `OK`
    1. Save (after saving, the newly added component should not be bolded or have a * symbol next to its name)
1. Add the component to the schematic
    1. Add the part to the correct location(s) on the schematic
    1. Annotate the schematic to include the new components
    1. Go to `Tools > Assign Footprints...`
    1. If prompted to update the "missing lib nickname", click OK
    1. Save the change by clicking OK again to exit the `Assign Footprints` menu
