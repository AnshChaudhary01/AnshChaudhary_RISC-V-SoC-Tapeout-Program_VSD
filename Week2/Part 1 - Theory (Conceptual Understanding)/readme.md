# VSDBabySoC - Learning System-on-Chip (SoC) Fundamentals

## Overview
VSDBabySoC is a compact, educational System-on-Chip (SoC) prototype based on the RISC-V architecture. It is intentionally simple and modular so learners can explore core SoC concepts — CPU operation, clocking, analog interfacing, and data flow — without the complexity of a commercial SoC. This README summarizes SoC fundamentals and explains how BabySoC fits into the learning journey.

---

## What is a System-on-Chip (SoC)?
A **System-on-Chip (SoC)** integrates the major components of a computer system (processor, memory, peripherals, and interconnect) onto a single silicon die. SoCs reduce board area, improve energy efficiency, and lower cost by minimizing off-chip communication and combining functionality into a single package. 

They are ubiquitous in mobile devices, wearables, IoT endpoints, and many embedded systems.

---

## Components of a Typical SoC
A typical SoC can be understood as four broad functional groups:

### 1. CPU (Central Processing Unit)
- Executes program instructions and controls system behavior.
- Ranges from simple microcontroller cores (low power, limited features) to high-performance multi-core processors.
- In BabySoC, the **RVMYTH RISC-V core** represents the CPU used for instruction execution and data processing.

### 2. Memory
- **RAM**: Volatile storage for runtime data and stacks.
- **ROM/Flash**: Non-volatile storage for boot code, firmware, or persistent data.
- Memory hierarchy and bandwidth are critical to system performance.

### 3. Peripherals
- Functional blocks that provide I/O and specialized processing (e.g., GPIO, UART, SPI, I²C, GPU, DSP, ADC/DAC, timers).
- Peripherals allow the SoC to interact with the outside world or offload compute from the CPU.
- BabySoC includes a **10-bit DAC** as a simple analog output peripheral to demonstrate digital-to-analog interfacing.

### 4. Interconnect (On-chip Network)
- The communication fabric that connects CPU, memory, and peripherals (e.g., buses, AXI/AMBA, NoC).
- Responsible for arbitration, bandwidth allocation, and routing of requests and responses.
- Proper interconnect design is vital for predictable latency and throughput.

---

## Why BabySoC is a Good Learning Model
BabySoC intentionally reduces system complexity to expose fundamental ideas that are often hidden in full-scale SoCs:

- **Small scope**: Fewer modules mean learners can trace signals, inspect register contents, and follow data paths end-to-end.
- **Open components**: RVMYTH (RISC-V) and the 10-bit DAC are simple, open-architecture blocks that can be examined and modified.
- **Clocking and timing**: Inclusion of an 8× PLL highlights real clock generation, synchronization, and the need for stable timing.
- **Analog/digital boundary**: The DAC and OUT file demonstrate how digital values are converted into analog signals for real devices.
- **Hands-on validation**: BabySoC can be used to validate IP cores together (CPU, PLL, DAC) before scaling up.

These attributes make BabySoC ideal for coursework, demos, and early prototyping where the goal is understanding, not production performance.

---

## Role of Functional Modelling (Before RTL and Physical Design)
Functional modelling is the stage where the **behavioral correctness** and **high-level architecture** are validated before committing to Register-Transfer Level (RTL) implementation and physical layout. 

### **Key benefits:**
- **Early verification of algorithms and interfaces:** Models (C/Matlab/SystemC or cycle-accurate simulators) show whether components interact correctly.
- **Faster iteration:** Behavioral models are quicker to change than RTL, enabling design space exploration (clock domains, buffer sizing, protocol choices).
- **Reduce costly rework:** Catch architectural or protocol bugs early to avoid expensive RTL fixes or silicon respins.
- **Performance estimation:** Use models to estimate throughput, latency, and power tradeoffs before detailed design.

BabySoC is particularly well-suited for functional modelling since its simplified blocks let students and designers rapidly verify system behavior (e.g., CPU updating r17, DAC output generation, PLL lock behavior) before moving to detailed RTL or layout.

---

## How to Use BabySoC in a Learning Workflow
1. **Behavioral/Functional Model:** Build or run a high-level simulation that exercises the CPU, memory, and DAC. Verify data sequences and analog output behavior.  
2. **Unit Tests for IPs:** Individually validate RVMYTH, PLL, and DAC using targeted testbenches.  
3. **Integration Tests:** Combine the cores in a system-level simulation and verify timing interactions, data flow, and file-based outputs (e.g., OUT file for DAC output).  
4. **RTL Implementation:** Once the functional model is stable, translate to RTL (Verilog/VHDL) and synthesize for FPGA or ASIC flows.  
5. **Physical Design Considerations:** Address clock distribution, floorplanning, and power domains during place & route — informed by earlier functional observations.

---

## Conclusion
VSDBabySoC provides a compact, practical platform to **learn core SoC design principles**. By focusing on CPU behavior, interconnects, clocking, and a simple analog peripheral, BabySoC makes the fundamental tradeoffs and interactions **visible and testable**.

This staged approach — starting with functional modelling and moving to RTL and physical design — is the recommended path for reliable, efficient SoC development.

---

## File
- **OUT** — File where DAC analog output is stored (used for playback or visualization).


---
