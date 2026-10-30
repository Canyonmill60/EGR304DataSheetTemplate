---
## title: Individual Block Diagram

tags:
- Block Diagram
- Gripper
- Object Handling
- PIC18F57Q43
- Robotic Arm

## Overview
The block diagram below is the block diagram showing the Gripper and Object Handling subsystem of the Simple Educational Robotic Arm. In this subsystem, the Gripper servo and the sensors’ input signals are controlled by the PIC18F57Q43 Curiosity Nano microcontroller. The block diagram includes the power supply lines, signal conditioning, microcontroller I/O ports, and other interfaces of the subsystem with the Arm Motion Control and User Controls & Safety subsystems.




## Block Diagram 

![Updated Gripper and Object Handling Block Diagram](Gripper_Block_Diagram_Updated.png)

## Block Diagram Design Explanation

The Gripper and Object Handling subsystem is designed to control the robotic arm's gripper while monitoring the force applied to an object. The block diagram separates the design into power distribution, force sensing, microcontroller control, servo operation, and communication.

**Power Distribution:** A 9 V external supply provides power through a 1 A fuse to an L7805 linear voltage regulator. The regulator produces a nominal 5 V supply for the external electronics, including the servo gripper and force-sensing circuit. The PIC18F57Q43 Curiosity Nano is powered separately through USB.

**Force Sensing:** The FSR 402 force sensor produces a resistance change when pressure is applied. The MCP6004 operational amplifier buffers the resulting voltage signal before it reaches the PIC's RA0 analog input. This allows the microcontroller to monitor gripping force.

**Gripper Control:** The PIC18F57Q43 generates a servo control signal to operate the Kitronik Klaw Mk2 gripper. This allows the subsystem to open and close the gripper to handle objects.

**Communication:** UART connections are provided for communication with the Arm Motion Control and User Controls & Safety subsystems. These connections are intended to allow coordinated operation between the different sections of the robotic arm.

**Debugging and Testing:** A debug LED, pushbutton, and test points provide additional interfaces for monitoring and troubleshooting the subsystem.

**Design Decisions and Product Requirements:** The design uses a servo-operated gripper because it provides straightforward position control without requiring a separate H-bridge motor driver. The FSR 402 adds force-sensing capability, while the MCP6004 provides signal buffering. Separating the power supply, sensor, and control functions makes the design easier to understand and troubleshoot. Together, these features support the robotic arm's requirements for controlled gripping, object handling, and communication between subsystems.


