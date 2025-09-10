## XBee setup for Advanced Tutorial

>[!IMPORTANT]
> For in-person workshops, XBee modules will be provided and pre-configured. In which case, you may skip this document. It is provided as a reference.

This walks through how to set-up 2 XBee modules to communicate with each other. One XBee will be connected to the GDS machine, and the other will be connected to the AdvancedDeployment application on Raspberry Pi.

The goal is to set them up so they have the same PAN ID and CH ID, and the MY (source address) of one matches the DH+DL (destination address) of the other, and vice versa.

Note: DH is the high 32-bits of the destination address, and DL is the 32 bits. MY is the source address (only 16 bits). So we set DH to 0x0 and DL to the MY address of the other XBee.

### Detailed instructions

Here's a step-by-step guide. The values are shown as examples, but you can choose different values as long as they are consistent between the two XBees, as explained above (MY1 = DL2, MY2 = DL1, PAN1 = PAN2).

1. Install XTCU https://www.digi.com/products/embedded-systems/digi-xbee/digi-xbee-tools/xctu
2. Connect the first XBee to your computer using a USB-C adapter
3. Open XCTU and add/discover the XBee module
4. Once discovered, click the "Update" button to update firmware to Digi XBee3 802.15.4 TH (v2014 has been tested)
5. Change the following settings in the Networking/Addressing sections:
    - ID (PAN ID): 0x1234 (or any other value, but both XBees must have the same PAN ID)
    - CH: 0xC
    - DH: 0x0
    - DL: 0x2
    - MY: 0x1 for the first XBee (connected to the computer)
    - BD: set baud to 115200
6. Click "Write" to save the settings
7. Disconnect the first XBee and connect the second one. Repeat with the following values:
    - ID (PAN ID): 0x1234 (must match the first XBee)
    - CH: 0xC
    - DH: 0x0
    - DL: 0x1 (the MY address of the first XBee)
    - MY: 0x2 for the second XBee (connected to the Raspberry Pi)
    - BD: set baud to 115200
11. Click "Write" to save the settings


### Example setup

Here's a table of how to set up 5 pairs of XBees to work in the F´ workshop "classroom" setup. PAN ID *must* match for a pair and differ between pairs. Using different CH (channel) values helps avoid interference if multiple pairs are used in the same area (dictates frequency channel).

| Pair # | PAN ID   | Channel (CH) | A: MY | A: DL | B: MY | B: DL | DH (shared) | Baud Rate (shared) |
|--------|----------|--------------|-------|-------|-------|-------|-------------|--------------------|
| 1      | 0x0001   | 0xC          | 0x1   | 0x2   | 0x2   | 0x1   | 0x0         | 115200             |
| 2      | 0x0002   | 0xD          | 0x1   | 0x2   | 0x2   | 0x1   | 0x0         | 115200             |
| 3      | 0x0003   | 0xE          | 0x1   | 0x2   | 0x2   | 0x1   | 0x0         | 115200             |
| 4      | 0x0004   | 0xF          | 0x1   | 0x2   | 0x2   | 0x1   | 0x0         | 115200             |
| 5      | 0x0005   | 0xB          | 0x1   | 0x2   | 0x2   | 0x1   | 0x0         | 115200             |