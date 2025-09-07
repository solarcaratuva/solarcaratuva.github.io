---
title: LTE Module
nav_order: 2
parent: Telemetry
has_children: false
---

# LTE Module
[LTE ("Long Term Evolution")](https://www.digi.com/blog/post/what-is-lte) is an efficient and more optimized path to communicate cellular data across devices. During some Solar Car competitions, the team needs to stream telemetry data from the car to another device at the pit station, which requires long distance cellular communication. We're currently at work configuring and implementing an XBee LTE Module into our car to enable this feature.  

**Project Status: *Work in Progress***


## Setup Resources

For hardware, we have a Digi Xbee LTE Module, a Digi XBee Development Board, a SIM card, etc. To learn about these devices and how to configure them, please check out the following links:
- [Interactive setup guide for the XBee LTE Kit](https://www.digi.com/start/digi-xbee-3-global-lte-m-nb-iot)
- [Tutorial Documentation for XBee LTE Module](https://docs.digi.com/resources/documentation/digidocs/90002420/#containers/cont_getting_started.htm?TocPath=Get%2520started%2520with%2520the%2520XBee%257C_____0)

Here are some software that may be required to develop the LTE Module:
- [XCTU](https://hub.digi.com/support/products/xctu/?_gl=1*10gir5s*_gcl_au*NjEzNzMwNzY3LjE3NDMxODU5ODA.*_ga*MTc2ODM4NDU0MC4xNzQzMTg1OTgw*_ga_RZXDK3PM3B*MTc0MzE5Njk5Mi4yLjEuMTc0MzE5OTcyNC42MC4wLjEyOTMxODUzMzQ): traditional software used to configure settings for the LTE Module and other XBee devices.
- [Digi XBee Studio](https://www.digi.com/products/embedded-systems/digi-xbee/digi-xbee-tools/digi-xbee-studio): application for monitoring, configuring, and testing the XBee LTE Module (newer than XCTU, but we don't know much about how to use it yet). 