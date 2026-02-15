---
title: LTE Module
nav_order: 2
parent: Telemetry
has_children: false
---

During Solar Car competitions, the team needs to stream telemetry data from the car to another device at the pit station, which requires long distance cellular communication. We're currently at work configuring and implementing a [Digi XBee LTE Module](https://www.digi.com/products/embedded-systems/digi-xbee/cellular-modems/digi-xbee-3-global-lte-m-nb-iot) into our car to enable this feature.

## What is LTE?
You ever wonder why your smartphone sometimes displays the letters "LTE" by the top-right data bars? It's likely because the cellular network conntected to your phone has swapped to (or currently uses) the 4G LTE cellular network!

*Add picture here*

[LTE ("Long Term Evolution")](https://www.digi.com/blog/post/what-is-lte) is a technology providing an efficient, optimized pathway to communicate cellular data across devices. Its often referred as 4G LTE, becauses it's part of the 4th cellular network generation. Essentially, "generations" divide and organize the gradual improvement of the cellular network by decade, with each generation significantly improving upon the latency (time delay of data transmission), bandwidth (data transfer rate), and other features from the previous decade.

For instance, 5G is the current cellular generation for the 2020s, and it features ultra-low latency (1-4 ms) and high bandwidth (up to 20 Gbps). Being the previous generation, 4G LTE has more latency and less bandwidth than 5G, but it does have better coverage and reliability. If your phone typically runs on 5G, it may swap to the 4G LTE network if the 5G signal is weak/unavailable in your area. 

An LTE module is a hardware component that connects devices to the 4G LTE cellular network for data transmission. The particular LTE module we're using is the [Digi XBee 3 Global and Low-Power LTE-M/NB-IoT](https://www.digi.com/products/embedded-systems/digi-xbee/cellular-modems/digi-xbee-3-global-lte-m-nb-iot).



## Setup Resources

For hardware, we have a Digi Xbee LTE Module, a Digi XBee Development Board, a SIM card, etc. To learn about these devices and how to configure them, please check out the following links:
- [Interactive setup guide for the XBee LTE Kit](https://www.digi.com/start/digi-xbee-3-global-lte-m-nb-iot)
- [Tutorial Documentation for XBee LTE Module](https://docs.digi.com/resources/documentation/digidocs/90002420/#containers/cont_getting_started.htm?TocPath=Get%2520started%2520with%2520the%2520XBee%257C_____0)
  - [Tutorial Documentation for Micropython Programming](https://docs.digi.com/resources/documentation/digidocs/90002219/)

Here are some software that may be required to develop the LTE Module:
- [XCTU](https://hub.digi.com/support/products/xctu/?_gl=1*10gir5s*_gcl_au*NjEzNzMwNzY3LjE3NDMxODU5ODA.*_ga*MTc2ODM4NDU0MC4xNzQzMTg1OTgw*_ga_RZXDK3PM3B*MTc0MzE5Njk5Mi4yLjEuMTc0MzE5OTcyNC42MC4wLjEyOTMxODUzMzQ): traditional software used to configure settings, run commands, and implement scripts on the LTE Module and other XBee devices.
- [Digi XBee Studio](https://www.digi.com/products/embedded-systems/digi-xbee/digi-xbee-tools/digi-xbee-studio): application for monitoring, configuring, and testing the XBee LTE Module (though hasn't been used that frequently). 
