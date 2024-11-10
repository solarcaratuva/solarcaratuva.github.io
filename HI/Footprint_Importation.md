---
title: Handling Rivanna 3 Repository
nav_order: 5
parent: Hardware Integration
has_children: false
---

# Footprint Importation
[Link](https://myuva-my.sharepoint.com/:w:/g/personal/grt2ez_virginia_edu/EUOBiP9rCKpKgtjtbv8AurIBhKWTxw_TARXTIykQl25CnQ?e=JdH2P8) to tutorial for Importing Footprints from Mouser into KiCad

# Frequently Asked Questions

###  I have cloned the library but I cannot see the any of the footprints with in the KiCad Libraries folder. What do I do?

If you do not see any files within this repository then run the following command. Since the repository for Rivanna 3 is set up to invove submodules, this changes our approach to handling and updating the KiCad library.

        git submodule update  --init --recursive