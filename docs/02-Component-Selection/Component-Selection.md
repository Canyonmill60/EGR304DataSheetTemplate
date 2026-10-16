---
title: Gripper Component Selection
---
---
**Overview**
Component Selection Process
This page describes the process used to select components for the Gripper & Object Handling subsystem of Team 107's Simple Educational Robotic Arm.

This subsystem relies on a PIC18F57Q43 Curiosity Nano microcontroller to control a servo-mechanized gripper and detect any object through infrared detection and to sense gripper strength through a Force Sensitive Resistor (FSR).

The objective here is to choose low-cost components which would be able to effectively detect and grasp any object as well as to ensure their safe handling.

Total budget for the chosen components is $60. The PIC18F57Q43 Curiosity Nano is already owned and doesn’t need to be purchased.

The following section provides a comparison of alternatives to components in question.
## Component Selection 1: Gripper Servo Motor

The gripper requires a servo motor that can open and close its fingers while remaining compact, affordable, and compatible with the PIC18F57Q43 microcontroller. Three TowerPro servo motors were compared.

### Table 1: Servo Motor Comparison

| Solution | Advantages | Disadvantages | Price |
|---|---|---|---|
| **TowerPro SG90** | Lightweight (9 g); inexpensive; PWM controlled; suitable for small grippers | Plastic gears can wear or strip; limited torque for heavier objects | $4.60 |
| **TowerPro MG90S** | Metal gears improve durability; compact (13.4 g); approximately 1.8 kg·cm stall torque at 4.8 V; PWM controlled | More expensive than SG90; limited torque for heavy objects | $9.00 estimated |
| **TowerPro MG996R** | Metal gears; approximately 9.4 kg·cm stall torque at 4.8 V; suitable for heavier gripping loads | Larger (55 g); requires more current; adds weight to the robotic arm | $11.20 |

### Servo Motor Pictures

| SG90 | MG90S | MG996R |
|:---:|:---:|:---:|
| ![TowerPro SG90](SG90.png) | ![TowerPro MG90S](MG90S.png) | ![TowerPro MG996R](MG996R.png) |

### Product Links

- [TowerPro SG90 Digital Servo](https://torqpro.com/product/sg90-digital/)
- [TowerPro MG90S Servo](https://towerpro.com.tw/product/mg90s-3/)
- [TowerPro MG996R Servo](https://torqpro.com/product/mg996r/)

### Selected Component: TowerPro MG90S

**Manufacturer:** TowerPro

**Part Number:** MG90S

**Operating Voltage:** Approximately 4.8–6 V

**Control:** PWM

**Selection Explanation:**

The TowerPro MG90S was selected for the Gripper & Object Handling subsystem because it offers a suitable balance of size, cost, durability, and gripping capability. Its metal gears provide better resistance to mechanical wear than the plastic gears of the SG90. Although the MG996R produces significantly more torque, its larger size and weight make it less suitable for a compact educational gripper.

The MG90S can be controlled using a PWM output from the PIC18F57Q43 microcontroller. A separate regulated servo power rail will be used, with a common ground shared with the microcontroller.

The MG90S is the preferred choice pending verification that its torque is sufficient for the intended gripper mechanism and object weight.

## Component Selection 2: Object Detection Sensor

The gripper requires an object detection sensor to determine when an object is positioned near the gripping fingers. Three sensors were compared based on cost, detection capability, circuit complexity, and compatibility with the PIC18F57Q43.

### Table 2: Object Sensor Comparison

| Solution | Advantages | Disadvantages | Reference Price |
|---|---|---|---|
| **Vishay TCRT5000** | Compact; low-cost reflective infrared sensing; compatible with a simple transistor interface; suitable for close-range object detection | Detection depends on object reflectivity and distance; requires resistors and signal conditioning | $3.39 (TCRT5000-based module) |
| **Vishay CNY70** | Very inexpensive; compact; simple phototransistor output; low component count | Very short sensing distance; sensitive to object surface and alignment | $0.95 |
| **ST VL53L0X with Adafruit breakout** | Measures distance rather than reflected intensity alone; longer detection range; digital I²C interface | More expensive; requires additional firmware; changes the interface used in the existing block diagram | $14.95 |

### Object Sensor Pictures

| TCRT5000 | CNY70 | VL53L0X |
|:---:|:---:|:---:|
| ![TCRT5000 Infrared Sensor](TCRT5000.png) | ![CNY70 Reflective Sensor](CNY70.png) | ![VL53L0X Distance Sensor](VL53L0X.png) |


### Product Links

- [TCRT5000 infrared sensor module](https://longan-labs.cc/products/2030007)
- [Vishay CNY70 reflective sensor](https://www.addicore.com/products/reflective-optical-sensor-cny70)
- [Adafruit VL53L0X distance sensor](https://www.adafruit.com/product/3317)

### Selected Component: Vishay TCRT5000

**Manufacturer:** Vishay

**Part Number:** TCRT5000

**Sensor Type:** Reflective infrared proximity sensor

**Microcontroller Connection:** RB5 GPIO input through signal-conditioning circuitry

**Selection Explanation:**

The Vishay TCRT5000 was selected because it provides a compact and economical method of detecting objects near the gripper fingers. Its reflective infrared sensing method is appropriate for short-range detection, while its phototransistor output can be interfaced with the PIC18F57Q43 using suitable resistors and a pull-up circuit.

The CNY70 is less expensive but has a shorter practical sensing range. The VL53L0X offers more advanced distance measurement but introduces additional cost and firmware complexity.

The TCRT5000 is therefore the preferred choice for this educational robotic gripper. The final sensor position and detection threshold will be tested with the intended objects.

**Price Note:** The $3.39 reference is for a TCRT5000-based sensor module, not necessarily the bare Vishay TCRT5000. The final bill of materials will use the price of the exact version purchased.




 

