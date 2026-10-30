---
title: Bill of Materials
tags:
  - EGR304
  - Bill of Materials
  - BOM
  - Hardware Orders
  - Robotic Arm
  - Gripper Subsystem
  - Component Selection

## Overview
This Bill of Materials (BOM) documents the components required for the Gripper and Object Handling subsystem of Team 107's Simple Educational Robotic Arm.

The subsystem uses a Kitronik Klaw Mk2 servo-operated gripper, an FSR 402 force sensor, an MCP6004 operational amplifier, and a PIC18F57Q43 Curiosity Nano microcontroller. The circuit receives a 9 V external power input and uses a voltage regulator to provide a 5 V supply for the gripper electronics, while the microcontroller is powered separately through USB.

The BOM includes component quantities, specifications, manufacturer information, supplier details, estimated prices, and spare components for prototyping and assembly.

The estimated purchasing subtotal is $44.30, excluding shipping and taxes, within the $60 subsystem budget. Separate purchase requests have been prepared for DigiKey and RobotShop USA.

## 
## Gripper Subsystem Bill of Materials

The Bill of Materials includes all components required for the Gripper and Object Handling subsystem, including components already owned and additional parts needed for prototyping and assembly.

[Download Gripper Subsystem BOM (Excel)](../Gripper_Subsystem_Design.xlsx)


### Gripper Subsystem Component List

| Reference | Component | Qty | Purchase Status |
|---|---|---:|---|
| C1 | 0.1 uF capacitor | 1 | Already owned |
| C2 | 10 uF capacitor | 1 | Already owned |
| C3 | 0.33 uF capacitor | 1 | Already owned |
| C4, C5 | 0.1 uF capacitors | 2 | Already owned |
| D1 | Debug LED | 1 | Already owned |
| F1 | 1 A blade fuse | 1 | Already owned |
| J1 | Kitronik Klaw Mk2 gripper kit | 1 | Purchase |
| J2 | 4-pin header | 1 | Already owned |
| J3 | 2-pin power connector | 1 | Already owned |
| J4 | 4-pin header | 1 | Already owned |
| JP1 | 2-pin jumper | 1 | Already owned |
| PIC18F57Q43 | Curiosity Nano board | 1 | Already owned |
| U1-CM1 | MCP6004 amplifier | 1 | Purchase |
| R1 | 10k resistor | 1 | Already owned |
| R2 | FSR 402 force sensor | 1 | Purchase |
| R3 | 330 ohm resistor | 1 | Already owned |
| R4 | 10k resistor | 1 | Already owned |
| SW1 | Pushbutton | 1 | Already owned |
| TP1, TP2 | PCB test pads | 2 | Fabricated on PCB |
| U1 | L7805 voltage regulator | 1 | Purchase |
| FH1 | Standard blade fuse holder | 1 | Purchase |
| SK1 | 14-pin DIP IC socket | 1 | Purchase |


### Purchasing Summary

| Supplier | Estimated Cost |
|---|---:|
| DigiKey | $12.56 |
| RobotShop USA | $31.74 |
| **Total** | **$44.30** |

The subsystem has a $60 budget, leaving $15.70 before shipping and taxes.


