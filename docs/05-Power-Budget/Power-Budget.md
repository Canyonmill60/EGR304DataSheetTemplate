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

## Power Budget Calculations

### Equation 1: Electrical Power

Electrical power is calculated using:

**P = V × I**

Where:

- P = Electrical power in watts (W)
- V = Supply voltage in volts (V)
- I = Current in amperes (A)

For the external 5 V power supply:

**P = 5 × I**

For example, if a component draws 0.5 A at 5 V:

**P = 5 × 0.5 = 2.5 W**

This is an example calculation, not a measured component current.

### Equation 2: Total Supply Current

The total current drawn from the external supply is the sum of the current drawn by the servo, logic power circuitry, sensors, and other connected loads:

**I_total = I_servo + I_logic_input + I_other_5V**

The logic input current must include the effect of any 3.3 V regulator and its efficiency or quiescent current. Currents on different voltage rails must not simply be added without accounting for the power conversion method.

### Equation 3: Peak Current Requirement

The external power supply must be capable of supporting the maximum expected simultaneous current draw:

**I_supply_rated >= I_total_peak**

A suitable design margin should be added after verifying the actual peak currents.

### Equation 4: FSR Voltage Divider Current

The FSR 402 is used as part of a voltage-divider circuit. Its current depends on the fixed resistor and the FSR resistance:

**I_FSR = 3.3 V / (R_fixed + R_FSR)**

The minimum expected FSR resistance must be considered when estimating maximum divider current.

### Calculation Status

The final total current and power requirements are pending confirmation of the MG90S servo current, PIC board power consumption, sensor module current, regulator configuration, and external power supply current rating.

## External Power Supply Selection

The robotic arm will use an external regulated 5 V DC power supply. The final current rating has not yet been determined.

A 5 V, 3 A regulated supply is being considered as a preliminary design candidate.

### Candidate Supply Calculation

**P = V x I**

**P = 5 V x 3 A = 15 W**

A 5 V, 3 A supply can provide up to 15 W of rated output power. This does not mean the robotic arm continuously consumes 15 W.

**Supply Status:** Candidate only; not yet selected or verified.

Before final selection, the combined peak current of all connected subsystems must be calculated, including the MG90S servo and microcontroller circuitry. Appropriate current margin, wiring capacity, and protection must also be considered.
