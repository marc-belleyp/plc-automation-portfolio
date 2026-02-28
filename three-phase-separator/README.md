# Three-Phase Separator Control System  
### PLC Programming & SCADA Demonstration Project  

**[→ Watch the demo video](https://www.youtube.com/watch?v=2MAICU6E-38)**

<p align="center">
  <img src="./screenshots/1-main-view-idle-state.jpg" alt="Separator HMI - main view idle" width="85%" />
  <br><br>
  <em>Idle state. Pressure, levels and valves all at zero.</em>
</p>

***

## Overview

This project demonstrates a simulated three-phase oil separator controlled using PLC logic and visualized through Ignition SCADA.

The system regulates:

* Separator Pressure  
* Oil–Water Interface Level  
* Oil Level 

The objective is to maintain stable separation using PID control and structured state-machine logic.

The control logic was developed in Connected Components Workbench (CCW) using Structured Text. The same control logic was then manually implemented inside Ignition Designer using a Gateway Timer Script to simulate PLC–SCADA integration.

No direct PLC communication (e.g., EtherNet/IP or Modbus TCP) was used in this demonstration.

***

## Process Description

The separator uses gravity separation inside a pressurized horizontal vessel.

* Gas exits at the top.  
* Water remains in the primary compartment below the oil layer.  
* Oil overflows over a weir into a secondary compartment.  
 
Pressure and liquid levels must remain stable to prevent phase carryover and ensure proper separation.

***

## Control Strategy

### Pressure Control
Maintains vessel pressure at setpoint using a modulating gas outlet control valve. Direct-acting PID with gains: **Kp=2.0, Ki=0.1, Kd=0.5**. Includes stronger anti-windup protection to prevent integral saturation.

### Interface Level Control
Maintains the oil–water interface at 50% using a modulating water discharge valve. Direct-acting PID with gains: **Kp=7.5, Ki=0.20, Kd=0.10**. Moderate response tuning allows the interface to settle smoothly. Includes integral clamping.

### Oil Level Control
Maintains oil level at 70% using a modulating oil discharge valve. Direct-acting PID with gains: **Kp=11.0, Ki=0.20, Kd=0.10**. High proportional gain enables rapid level adjustment with controlled settling. Includes integral clamping.

***

## System Structure

### PLC Development
* Developed in Connected Components Workbench (CCW)
* Structured Text programming
* State machine sequencing
* PID control loops
* Alarm logic

### SCADA Implementation (Ignition Maker Edition)
* HMI visualization
* Real-time trending
* Start / Stop / Reset controls
* Manual reimplementation of PLC logic using a Gateway Timer Script

***

## Project Structure

### /demo
Contains:
* youtube-link.txt  
  YouTube link to project walkthrough video

***

### /diagrams
Contains:
* separator-p&id.pdf  
  Process and instrumentation diagram showing vessel with streams, control valves, and instrumentation.

* separator-p&id-description.docx  
  Written explanation of p&id.

***

### /logic
Contains:
* 1-separator-state-machine.txt  
  Implements startup, shutdown, and operational sequencing using a state machine approach.

* 2-separator-pid.txt  
  Contains PID control logic for pressure, oil level, and interface level loops.

* 3-separator-simulation.txt  
  Simulates process dynamics for testing control performance.

* variables.xml  
  List of PLC variables with definitions.

***

### /screenshots
Contains visual documentation of:

* HMI operational states (Idle, Startup, Running, Shutdown)
* Alarm activation and acknowledgment
* Control loop stabilization trends
* Tag browser during runtime

***

## Design Highlights

✓ **State Machine Design** — Clear four-state sequencing (Idle, Startup, Running, Shutdown)

✓ **Safety Interlocks** — Pressure trips trigger automatic shutdown from any state

✓ **Anti-Windup Protection** — Prevents integral saturation and excessive windup in PID loops

✓ **Shutdown Sequencing** — Ordered valve closure on system shutdown

✓ **Process Simulation** — Test control strategy without hardware

***

## Available for Contract Work

If you're looking for PLC and SCADA automation expertise, I'm available for contract projects.

**Contact:** marcbelleyp@gmail.com | [LinkedIn](https://www.linkedin.com/in/marc-belleyp) | [GitHub](https://github.com/marc-belleyp)

**Typical scope:** Control logic development, PID implementation, troubleshooting, and HMI design.