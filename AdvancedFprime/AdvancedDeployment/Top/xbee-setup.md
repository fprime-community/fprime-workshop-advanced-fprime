## XBee setup for Advanced Tutorial

This walks through how to set-up 2 XBee modules to communicate with each other. One XBee will be connected to the GDS machine, and the other will be connected to the AdvancedDeployment application on Raspberry Pi.

1. Install XTCU https://www.digi.com/products/embedded-systems/digi-xbee/digi-xbee-tools/xctu
2. Connect the first XBee to your computer using a USB-C adapter
3. Open XCTU and add/discover the XBee module
5. Change the following settings in the Networking/Addressing sections:
    - PAN ID: 0x1234 (or any other value, but both XBees must have the same PAN ID)
    - DH: 0x0
    - DL: 0x2
    - MY: 0x1 for the first XBee (connected to the computer)
    - BD: set baud to 115200
6. Click "Write" to save the settings
7. Disconnect the first XBee and connect the second one. Repeat with the following changes:
    - PAN ID: 0x1234 (must match the first XBee)
    - DH: 0x0
    - DL: 0x1 (the MY address of the first XBee)
    - MY: 0x2 for the second XBee (connected to the Raspberry Pi)
    - BD: set baud to 115200
11. Click "Write" to save the settings

