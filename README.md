# Chemical Plant Batch Control System (Studio 5000)

## 📌 Project Overview
This repository contains the ladder logic and architectural documentation for a comprehensive, automated chemical plant batching system. Developed using **Studio 5000**, the project evolved from basic fill/drain cycles into a robust, multi-pass automated system featuring bi-directional state machines, analog instrumentation scaling, and strict safety interlocks.

## 🛠️ Technologies & Tools
* **Environment:** Studio 5000 Logix Designer
* **Language:** Ladder Diagram (LD)
* **Design & Architecture:** Sequential State Diagrams, Block Logic Routing
* **Instrumentation:** High-Speed Counters (Turbine Meters), Analog Differential Pressure (DP) Transducers

## 🚀 Key Engineering Highlights

### 1. Bi-Directional State Machines & Safety Interlocks
Industrial processes require foolproof safety mechanisms, especially when dealing with reversible physical processes. 
* **Implementation:** Designed a complex sequential state machine to handle both forward batching and reverse system flushing. Critically, I engineered strict hardware and software interlock logic within the motor control sequences to ensure that the forward and reverse operations could absolutely never interfere with or trigger each other, preventing catastrophic hardware faults.

### 2. Real-World Instrumentation & Scaling
Raw electrical signals must be reliably translated into actionable process variables.
* **Implementation:** Developed logic to capture and process high-speed pulse trains from a turbine flow meter to calculate exact fluid volumes. Simultaneously, scaled raw 4-20mA signals from a Differential Pressure transducer to continuously monitor and display precise tank levels, integrating both data sources into the main control loop.

### 3. Multi-Pass Batch Automation
Advanced manufacturing often requires looped operational cycles without operator intervention.
* **Implementation:** Engineered a "Three Pass Fill" system utilizing advanced loop counting and state-tracking logic to ensure precise chemical batching across multiple automated cycles before returning the system to a safe standby state.

## 📂 Repository Structure
* `/src` - Exported Studio 5000 logic routines and tag databases.
* `/docs` - System architecture, including Block logic diagrams and Sequential State flowcharts for the forward/reverse functionality. 
* `/specs` - Original operational requirements and process parameters.
