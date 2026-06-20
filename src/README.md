# Studio 5000 Ladder Logic Source

## 📌 Overview
This directory contains the finalized, cumulative ladder logic routines for the batch control system. The logic is divided into modular routines to separate continuous instrumentation scaling from the main sequential state machine.

## 🚀 Key Logic Implementations

### 1. Instrumentation Scaling & High-Speed Counters
* **Turbine Flow Meter:** Logic is implemented to capture high-speed pulse trains, applying a K-factor to calculate precise real-time volumetric flow during the multi-pass filling stages.
* **Differential Pressure (DP) Transducer:** Raw 4-20mA analog inputs are scaled within the PLC to provide continuous, accurate tank level readouts, which act as the primary transition triggers for the state machine.

### 2. Bi-Directional Motor Control & Safety Interlocks
* To support the system's "Reverse Functionality" (used for flushing/draining), the ladder logic features hard-coded software interlocks. These critical rungs guarantee that the forward batching sequence and the reverse sequence cannot energize simultaneously, protecting the physical pumps and valves from catastrophic mechanical failure.

### 3. Multi-Pass Loop Tracking
* The main routine utilizes counter instructions integrated directly into the state transitions to track batch cycles, allowing the system to automatically execute a "Three Pass Fill" before safely returning to an idle standby state.
