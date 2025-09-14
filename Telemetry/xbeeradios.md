---
title: Digi Xbee Radio Signals
nav_order: 3
parent: Telemetry
has_children: false
---

# Digi Xbee Radio Signals

This guide explains how to set up two Digi Xbee radio modules to send and receive messages, both using the Digi XCTU software and with a simple Python script.

---

## 1. Install Digi XCTU

Digi XCTU is the official configuration and testing software for Digi Xbee radios.

- **Download XCTU:** [https://hub.digi.com/support/products/xctu/](https://hub.digi.com/support/products/xctu/)
- Install it on **both computers** that will have Xbee modules plugged in.

---

## 2. Connect Xbee Modules

1. Plug each Xbee radio module into its USB adapter or development board.
2. Connect one module to **Computer A** and the other to **Computer B**.
3. Launch XCTU on both computers.
4. Add the Xbee modules to XCTU by clicking **Discover Devices**.
5. Verify both modules are detected and they have each others addresses.  
   - You can change the end addresses under the **Configuration** tab if needed.

---

## 3. Sending Messages in XCTU

1. Open the **Console** view in XCTU on both computers.
2. Click **Open** on both consoles.
3. Type a message in the console on Computer A and press **Send**.  
   The message should appear on Computer B’s console.
4. Try sending messages back and forth to confirm connectivity.

---

## 4. Sending Messages with Python

We can also send messages programmatically using a Python script. This is useful for automation or integrating with other software.

### Steps:

1. Clone the Telemetry repository
2. On **both computers**, install dependencies:

   ```bash
   pip install -r requirements.txt

3. Run python .\xbee_chat.py
4. You should now be able to send messages between two computers
5. Try making your own script now!
