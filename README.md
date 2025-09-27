# vsd_RISC_V_week1 Day 1
---

## Day 1 – Simulation and Synthesis Notes


### 1. Simulator

Purpose: To check if the design adheres to the given specifications.
Working:
Upon every change in input, the output is re-evaluated.
At least one input must change to observe new outputs.

Block Diagram
Tool Used: iverilog

---

### 2. Design

A set of Verilog codes written to meet the required specifications.

---

### 3. Testbench

Ensures that the design obeys the specifications.
Test vectors (stimulus) are applied to verify design behavior.
No direct inputs or outputs are assigned to testbenches.

---

### 4. Simulation Flow

Design + Testbench ──▶ iverilog ──▶ VCD (Value Change Dump) file ──▶ GTKWave

iverilog → compiles design + testbench.
Generates .vcd file (waveform dump).
gtkwave → used to view waveforms.

---

### 5. Synthesizer

Purpose: Converts RTL description into a netlist.
Tool Used: yosys

Flow

Design (read_verilog) + .lib (read_library) ──▶ yosys ──▶ Netlist (write_verilog)

.lib file: collection of standard cells (pre-defined gates and flip-flops).
Rich enough to implement required logical functions.

---

### 6. Verification of Synthesis Output

Netlist + Testbench ──▶ iverilog ──▶ VCD ──▶ GTKWave

Waveform must match RTL testbench results.
Confirms correctness after synthesis.

---

### 7. RTL Design

Behavioral representation of required specifications written in Verilog.
Converting RTL to gate-level logic is called Synthesis.

---

### 8. Why Many Different Gates (Library Cells)?

Example Block

Flip-Flop 1 ──▶ Combinational Circuit ──▶ Flip-Flop 2

Total Time = FF1 delay + Combinational delay + Setup time
To reduce combinational delay, pre-defined library cells are used.

Key Points

Standard cells are not always the fastest – they are chosen for timing balance.
Faster cells → used for performance paths.
Slower cells → used to satisfy hold time requirements.

---

✅ Day 1 Completed – Notes on Simulation, Synthesis, Verification, and Library Cells


