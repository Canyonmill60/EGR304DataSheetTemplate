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
