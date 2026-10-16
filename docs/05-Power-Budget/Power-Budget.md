---
title: Power Budget
---
## Overview

This page documents the power budget for Team 107's Simple Educational Robotic Arm, focusing on the Gripper & Object Handling subsystem.

The purpose of the power budget is to determine the voltage and current requirements of the electrical components and verify that the external power supply can safely support the subsystem during operation.

The gripper subsystem includes the following major electrical components:

- Microchip PIC18F57Q43 Curiosity Nano microcontroller
- TowerPro MG90S servo motor
- Vishay TCRT5000 infrared object detection sensor module
- Interlink Electronics FSR 402 force-sensitive resistor and voltage-divider circuit
- Power regulation, signal-conditioning circuitry, and connectors

The robotic arm uses an external regulated **5 V DC power supply**. The servo operates from the 5 V supply, while the microcontroller and sensor interfaces require a compatible logic power arrangement.

The calculations in the following sections will account for component operating current, peak current, regulator requirements, and available power supply capacity. Values that have not yet been verified will be identified as pending rather than treated as measured specifications.

## Electrical Component Power Requirements

### Table 1: Gripper Subsystem Power Budget

| Component | Quantity | Supply Voltage | Operating Current | Peak Current | Power Source |
|---|---:|---|---|---|---|
| TowerPro MG90S servo | 1 | 5 V DC | TBD | TBD (stall current) | External 5 V rail |
| PIC18F57Q43 Curiosity Nano | 1 | Board-approved supply configuration | TBD | TBD | Logic power arrangement |
| TCRT5000 infrared sensor module | 1 | Verify module operating voltage | TBD | TBD | Sensor power rail |
| Interlink FSR 402 voltage divider | 1 | 3.3 V | TBD | TBD | 3.3 V logic rail |
| 3.3 V regulator or onboard power circuitry | 1 | 5 V input, 3.3 V output if required | TBD | TBD | External 5 V supply |
| Signal-conditioning circuitry | 1 set | 3.3 V | TBD | TBD | 3.3 V logic rail |

**Note:** The FSR 402 is a variable resistor, not an independently powered electronic module. Its circuit current depends on the voltage-divider resistor values and the applied force.

**Current Status:** This table records the intended power architecture. Current consumption and regulator losses must be verified before calculating the final supply requirement.
