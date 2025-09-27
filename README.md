## 📘 Day 3 – D Flip-Flop & Optimization Study

### 🔹 Topics Covered

1. Asynchronous D Flip-Flop

Captures input immediately when triggered by asynchronous signals (reset or set), independent of the clock.



2. Synchronous D Flip-Flop

Captures input only on the clock edge.

Ensures stable sequential behavior and avoids glitches between clock transitions.


### 🔹 Simulation & Synthesis Flow

1️⃣ Icarus Verilog (RTL Simulation)
```
# Step 1: Compile design and testbench
iverilog <design_file>.v <testbenchfile>.v

# Step 2: Run simulation to generate VCD waveform
./<output_executable>

# Step 3: View waveform in GTKWave
gtkwave <output_file>.vcd
```
2️⃣ YoSys (Synthesis & Optimization)
```
# Start YoSys
yosys

# Read library
read_liberty -lib <library_file>.lib

# Read design
read_verilog <design_file>.v

# Synthesize top module
synth -top <top_module_name>

# Opt clean 
opt_clean -purge

# Map to library and optimize
abc -liberty <library_file>.lib

# Insert DFFs (if required)
dfflibmap -liberty <library_file>.lib

# Flatten hierarchy (optional)
flatten

# Write final netlist(for netlist genertaion )
write_verilog -noattr <output_netlist>.v

# Show design in YoSys GUI
show
```


---

### 🔹 Files Executed

1️⃣ D Flip-Flops

Files simulated using Icarus Verilog and YoSys:

| File Name   | Flip-Flop Type        | Simulation Tool         | Notes / Observations                        |
|------------|---------------------|------------------------|--------------------------------------------|
| DSFCONST1.v | Asynchronous DFF    | Icarus Verilog, YoSys  | Verified async reset/set behavior          |
| DSFCONST2.v | Asynchronous DFF    | Icarus Verilog, YoSys  | Observed waveform for glitch-free capture |
| DSFCONST3.v | Synchronous DFF     | Icarus Verilog, YoSys  | Stable capture on clock edge               |
| DSFCONST4.v | Synchronous DFF     | Icarus Verilog, YoSys  | Verified timing and waveform consistency  |
---

2️⃣ Optimization Check Files

These files demonstrate logic optimization techniques in YoSys.


File Name	Purpose / Observation

| File Name     | Purpose / Observation                         |
|--------------|-----------------------------------------------|
| OPT1.v        | Basic logic optimization applied              |
| OPT2.v        | Further reduction of area & delay            |
| OPT3.v        | Boolean simplification using K-map / Quine-McCluskey |
| OPT4.v        | Sequential optimization and state reduction |
| OPT5.v        | Final optimization: area/power trade-off    |
| OPT_CHECK.v   | Verification of optimizations applied        |


---


---

🔹 Notes

Asynchronous vs Synchronous DFF: Asynchronous responds immediately to reset/set; synchronous waits for clock edge.

---

