

## 📘 Gate-Level Simulation (GLS)

### 🔹 Overview


Gate-Level Simulation (GLS) is used to verify the logical correctness of synthesized designs. In GLS, a test bench is run with the netlist as the design under test (DUT).

The netlist is generated after synthesis and should align logically with the RTL code.

GLS ensures that timing constraints are met and the design works correctly under realistic gate delays.



---

### 🔹 Why GLS?


To verify logical correctness of the design after synthesis.

After synthesis, different timing setups exist in the netlist compared to RTL. GLS helps detect issues due to these timing differences.



---

### 🔹 GLS Setup


1. Combine:

RTL design or synthesized gate-level Verilog models

Test bench



2. Run simulation using Icarus Verilog (iverilog):

iverilog -o output.vvp design.v testbench.v
vvp output.vvp


3. Generate a VCD (Value Change Dump) file.


4. Open the VCD in GTKWave to visualize waveforms and verify functionality.




---

### 🔹 Common Synthesis & Simulation Mismatches


1. Missing Sensitivity List

Simulators trigger always blocks based on input activity.

If an always block is sensitive to only one signal, changes in other signals may not trigger updates → incorrect behavior.

Solution: Use always @(*) to make the block sensitive to all relevant signals.

Example: A simple multiplexer or adder where output depends on multiple inputs.


2. Blocking vs Non-Blocking Statements

Statement	Symbol	Behavior

Blocking	=	Executes line by line, like a C program.
Non-blocking	<=	Evaluates all RHS in parallel when the always block triggers, then updates LHS simultaneously.


Caveats: Using blocking statements in sequential designs (like FSMs or traffic light controllers) may lead to unintended behavior.

Best Practice: Use non-blocking (<=) statements for sequential logic to avoid race conditions.



---

### 🔹 Key Takeaways

GLS verifies both logical correctness and timing compliance after synthesis.

Always ensure proper sensitivity lists in always blocks.

Use non-blocking assignments for sequential logic to maintain predictable behavior.

Visualizing waveforms in GTKWave helps quickly identify functional mismatches.



---
