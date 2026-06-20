# Chemical Plant Simulation: System Specifications

## 📌 Overview
This document outlines the physical hardware parameters, instrumentation details, and operational constraints of the Chemical Plant simulation model used as the target hardware for this batch control system. 

The system simulates a closed-loop industrial fluid batching process, requiring the PLC to manage multiple actuators, high-speed pulse trains, and analog signal scaling to achieve precise volumetric control.

## 🏭 Physical Plant Architecture

### Fluid Routing & Actuation
* **Transfer Pumps:** The system utilizes dual transfer pumps (Pump A and Pump B) to move fluid from supply reservoirs into a central mixing tank.
* **Directional Control:** Fluid routing is managed via a network of electrically actuated solenoid valves. The logic must account for valve actuation delays and ensure correct routing paths before energizing the pumps to prevent dead-heading.
* **Bi-Directional Operation:** The piping architecture allows for both forward batching (filling the mix tank) and reverse flushing (draining back to supply). This necessitates strict software interlocks to prevent conflicting pump and valve states.

## 🎛️ Instrumentation & I/O Mapping

To achieve closed-loop control, the system relies on two primary forms of sensory feedback:

### 1. High-Speed Flow Measurement (Turbine Meters)
* **Function:** Installed on the supply lines to measure the exact volume of fluid transferred.
* **Signal Type:** The meters generate high-frequency discrete pulse trains proportional to fluid velocity.
* **PLC Implementation:** Requires the use of High-Speed Counter (HSC) modules or dedicated high-speed timer logic to capture pulses. These raw counts must be multiplied by a specific K-Factor to determine precise real-time volumetric flow in liters.

### 2. Analog Level Measurement (DP Transducers)
* **Function:** Continuously monitors the fluid level within the central mixing tank.
* **Signal Type:** Differential Pressure (DP) transducers output a raw analog signal (e.g., 4-20mA or 0-10V) proportional to the hydrostatic head pressure of the fluid.
* **PLC Implementation:** The raw analog integer from the I/O card must be mathematically scaled within the continuous task routine to output a human-readable volume (liters) or percentage (0-100%). This scaled value serves as the primary trigger for state machine transitions (e.g., stopping a fill sequence when the tank reaches 80% capacity).

## ⚠️ Operational & Safety Constraints
* **Failsafe States:** In the event of an emergency stop (E-Stop) or sequence abort, all pumps must immediately de-energize, and all routing valves must return to their closed (safe) states to isolate the fluid.
* **Interlock Requirements:** Forward and reverse logic paths must never be capable of executing simultaneously. Hardware and software interlocks must be hard-coded into the motor control subroutines.
