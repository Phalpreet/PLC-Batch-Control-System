# System Architecture & State Diagrams

## 📌 Overview
Before writing any ladder logic in Studio 5000, a robust control system requires thorough architectural planning. This directory contains the foundational design documents used to map out the chemical plant batching system.

## 📄 Documentation Breakdown

### 1. Sequential State Machine (`Seq.pdf`)
This flowchart details the exact step-by-step logic required to execute the multi-pass batching process. It defines the transition conditions between states (e.g., waiting for specific high-speed counter volumes or DP transducer thresholds) and maps out the strict interlock paths for the reverse functionality to ensure process safety.

### 2. System Block Routing Diagram (`Block.pdf`)
This diagram outlines the macro-level hardware and software routing. It maps the physical I/O (Turbine meters, pressure transducers, valves, and pumps) to their respective sub-routines within the PLC memory, ensuring a clean, modular approach to the final ladder logic.
