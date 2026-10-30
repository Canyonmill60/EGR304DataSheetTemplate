---
title: Power Budget
---
## Overview

This page documents the electrical power budget for Team 107's Simple Educational Robotic Arm, focusing on the Gripper and Object Handling subsystem.

The purpose of the power budget is to estimate the operating and peak current requirements of the subsystem, determine its electrical power consumption, and evaluate whether the selected power supply and voltage regulator can safely support the connected components.

The gripper subsystem includes the following major electrical components:

- PIC18F57Q43 Curiosity Nano microcontroller
- Kitronik Klaw Mk2 servo-operated gripper
- Interlink Electronics FSR 402 force sensor
- MCP6004 operational amplifier
- L7805 linear voltage regulator
- Debug LED and associated resistors
- Power connectors and supporting circuitry

The subsystem uses a nominal 9 V external power input, which passes through a fuse and an L7805 regulator to produce a nominal 5 V rail for the external circuitry. The PIC18F57Q43 Curiosity Nano is powered separately through USB.

The calculations will account for operating current, peak current, voltage regulator power dissipation, and supply capacity. Values that have not yet been verified will be identified as estimates or pending measurements.

The final power supply suitability will be determined after verifying the servo's peak current and the regulator's thermal limitations.

## Electrical Component Power Requirements

**Table 1: Gripper Subsystem Power Budget**

| Component | Quantity | Supply Voltage | Operating Current | Peak Current | Power Source |
|---|---:|---|---|---|---|
| Kitronik Klaw Mk2 servo | 1 | 5 V nominal | TBD | TBD (stall) | External 5 V rail |
| PIC18F57Q43 Curiosity Nano | 1 | USB (5 V input) | TBD | TBD | USB |
| MCP6004 operational amplifier | 1 IC | 5 V nominal | TBD | TBD | External 5 V rail |
| FSR 402 and 10 kΩ resistor | 1 circuit | 5 V nominal | TBD | TBD | External 5 V rail |
| Debug LED and 330 Ω resistor | 1 circuit | 5 V nominal | TBD | TBD | External 5 V rail |
| L7805 voltage regulator | 1 | 9 V input / 5 V output | TBD | TBD | External 9 V supply |

**Note:** The FSR 402 is a variable resistor. Its current depends on the resistance of the sensor and its voltage-divider resistor.

**Current Status:** The table reflects the updated schematic. Operating and peak currents must be calculated or verified before finalizing the power budget.


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

### Equation 4: FSR 402 Voltage Divider Current

The FSR 402 is connected in a voltage-divider circuit with a
10 kΩ resistor and a nominal 5 V supply.

The current is calculated using:

I_FSR = V / (R1 + R_FSR)

Assuming the FSR resistance approaches 0 Ω under maximum force:

I_FSR,max = 5 V / (10,000 Ω + 0 Ω)

I_FSR,max = 0.0005 A = 0.5 mA

Maximum divider power:

P_FSR,max = V × I

P_FSR,max = 5 V × 0.0005 A

P_FSR,max = 0.0025 W = 2.5 mW

Therefore, the FSR voltage-divider circuit draws no more than
approximately 0.5 mA from the nominal 5 V supply, assuming
the stated 10 kΩ series resistance.


### Debug LED Current and Power Calculation

The debug LED uses a 330 Ω current-limiting resistor.

Assuming a 5 V supply and an LED forward voltage of 2 V:

I_LED = (V_supply - V_LED) / R3

I_LED = (5 V - 2 V) / 330 Ω

I_LED = 0.00909 A = 9.09 mA

The total circuit power consumption is:

P_LED = V_supply × I_LED

P_LED = 5 V × 0.00909 A

P_LED = 0.0455 W = 45.5 mW

The estimated debug LED circuit current is 9.09 mA
when the LED is on, assuming a 5 V drive voltage.

This is a preliminary estimate. The actual current
and power source depend on the PIC output voltage
and the LED forward voltage.


### MCP6004 Operational Amplifier Power Calculation

The MCP6004 is a quad operational amplifier used to
condition the FSR 402 force sensor signal.

For this preliminary calculation, the typical supply
current is estimated as 100 µA per amplifier.

Total estimated current:

I_MCP6004 = 4 × 100 µA

I_MCP6004 = 400 µA = 0.4 mA

Power consumption at 5 V:

P_MCP6004 = V × I

P_MCP6004 = 5 V × 0.0004 A

P_MCP6004 = 0.002 W = 2 mW

The MCP6004 is estimated to consume approximately
0.4 mA and 2 mW under typical conditions.

These values are preliminary estimates and must be
checked against the component datasheet. The final
power budget must also consider worst-case supply
current and output loading.


### Kitronik Klaw Mk2 Servo Power Calculation

Manufacturer: Kitronik
Part Number: 25104
Included Motor: Mini 180-degree servo
Specified Operating Voltage: 3 V to 6 V
Design Supply Voltage: 5 V

The servo operates the robotic gripper by opening
and closing its jaws.

Electrical power is calculated using:

P = V × I

Operating power:
P_operating = 5 V × I_operating

Peak stall power:
P_stall = 5 V × I_stall

The manufacturer confirms the operating voltage
range but does not specify operating or stall
current in the published kit specifications.

Operating Current: TBD
Stall Current: TBD
Operating Power: TBD
Peak Power: TBD

The current requirements must be verified before
confirming the suitability of the L7805 regulator.

Source:
https://kitronik.co.uk/products/25104-klaw-mk2-robotic-gripper-kit


### L7805 Voltage Regulator Power Dissipation

The gripper subsystem uses an L7805 linear voltage
regulator to convert the external 9 V supply to a
nominal 5 V output.

Input Voltage = 9 V
Output Voltage = 5 V

Voltage drop:

V_drop = 9 V - 5 V = 4 V

Approximate regulator power dissipation:

P_regulator = (V_in - V_out) × I_load

P_regulator = 4 V × I_load

Example calculations:

| Load Current | Regulator Power Dissipation |
|---|---|
| 100 mA | 0.4 W |
| 250 mA | 1.0 W |
| 500 mA | 2.0 W |
| 750 mA | 3.0 W |
| 1000 mA | 4.0 W |

The L7805 dissipates the voltage difference between
its input and output as heat.

The regulator's thermal suitability depends on the
total load current, ambient temperature, package,
and available heatsinking.

The servo's operating and stall current must be
verified before the regulator can be approved for
the final design.

These values are examples, not measured load currents.


### Total Subsystem Current and Power

The total current requirement is calculated by
combining the loads connected to the external
regulated 5 V supply.

Preliminary known loads:

MCP6004 amplifier = 0.40 mA
FSR 402 voltage divider = 0.50 mA maximum

Combined estimated current:

I_known = 0.40 + 0.50

I_known = 0.90 mA

Combined estimated power:

P_known = 5 V × 0.0009 A

P_known = 0.0045 W = 4.5 mW

The servo current has not yet been verified.

Total external current:

I_external = I_servo + I_other_external_loads

The debug LED supply connection must be verified
before including it in the external load total.

The PIC18F57Q43 Curiosity Nano is powered
separately through USB and is not included
in the external 9 V supply current.

The external supply current and regulator power
dissipation cannot be finalized until the servo's
operating and peak current requirements are known.

The 0.90 mA value is a preliminary subtotal,
not the complete subsystem current requirement.



### Calculation Status

The final total current and power requirements are pending confirmation of the MG90S servo current, PIC board power consumption, sensor module current, regulator configuration, and external power supply current rating.


## External Power Supply Selection

The Gripper & Object Handling subsystem is designed
to use an external 9 V DC power supply.

The external 9 V input passes through a 1 A fuse
before reaching the L7805 linear voltage regulator.

The L7805 provides a nominal 5 V output for the
external gripper and sensor circuitry.

The PIC18F57Q43 Curiosity Nano is powered separately
through its USB connection.

### Power Supply Requirements

External Input Voltage: 9 V DC
Regulated Output Voltage: 5 V DC
Input Fuse Rating: 1 A
External Supply Current Rating: TBD
Servo Operating Current: TBD
Servo Stall Current: TBD

### Supply Power Calculation

The available input power is calculated using:

P_supply = V_supply × I_supply

P_supply = 9 V × I_supply

For illustration, a 9 V supply rated at 1 A
would provide up to 9 W of rated input power.

This is an example, not confirmation that the
selected power supply has a 1 A rating.

### Voltage Regulator Considerations

The L7805 drops approximately 4 V between its
input and output.

P_regulator ≈ 4 V × I_load

The regulator dissipates this power as heat.

The regulator's output current capability depends
on its thermal conditions and component ratings.

The 1 A input fuse does not guarantee that the
regulator or servo is protected against all
overcurrent or overheating conditions.

### Current Status

The 9 V input and 5 V regulated output match the
intended schematic architecture.

However, the external supply current rating,
servo peak current, and regulator thermal
performance still require verification.

The final power supply suitability cannot yet
be confirmed.


### Candidate Supply Calculation

**P = V x I**

**P = 5 V x 3 A = 15 W**

A 5 V, 3 A supply can provide up to 15 W of rated output power. This does not mean the robotic arm continuously consumes 15 W.

**Supply Status:** Candidate only; not yet selected or verified.

Before final selection, the combined peak current of all connected subsystems must be calculated, including the MG90S servo and microcontroller circuitry. Appropriate current margin, wiring capacity, and protection must also be considered.


## Power Budget Excel File

The preliminary power budget spreadsheet contains
the component current estimates, power calculations,
and regulator power requirements for the Gripper
and Object Handling subsystem.

[Download Gripper Power Budget Excel File](Team107_Gripper_Power_Budget_Preliminary.xlsx)


## Conclusions

The updated power budget documents the electrical
requirements of Team 107's Gripper & Object
Handling subsystem.

The design uses an external 9 V DC supply and an
L7805 linear voltage regulator to provide a
nominal 5 V rail for the gripper and associated
electronics.

The PIC18F57Q43 Curiosity Nano is powered
separately through USB.

The preliminary calculations indicate:

- FSR voltage-divider maximum current: 0.50 mA
- MCP6004 estimated typical current: 0.40 mA
- Combined preliminary current: 0.90 mA
- Combined preliminary power: 4.5 mW
- Regulator voltage drop: 4 V
- Regulator dissipation: approximately 4 W per
  ampere of 5 V load current

The debug LED current has been estimated separately,
pending confirmation of its actual drive voltage.

The Kitronik Klaw Mk2 servo is expected to be a
major electrical load. Its operating and stall
current requirements remain unverified.

Before the design is finalized, the servo current,
external power supply rating, regulator thermal
performance, and actual wiring connections must
be confirmed.

Final Status: Preliminary power budget calculations
completed. Final supply and regulator suitability
remain pending verification.

**Final Status:** Preliminary power budget completed; numerical current verification and final supply selection remain pending.
