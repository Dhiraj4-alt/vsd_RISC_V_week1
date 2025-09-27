## 📘 Day 3 – D Flip-Flop & Optimization Study

### 🔹 Topics Covered

1. Asynchronous D Flip-Flop

Captures input immediately when triggered by asynchronous signals (reset or set), independent of the clock.



2. Synchronous D Flip-Flop

Captures input only on the clock edge.

Ensures stable sequential behavior and avoids glitches between clock transitions.

---

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

# command to do all the propogatin and all optimization
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

1. Optimization Check Files
These files demonstrate logic optimization techniques in YoSys.


File and execution

| File Name              | Screenshot                 |
|------------------------|----------------------------|
| opt_check.v            | [Photo1](#opt1-screenshot) |
| opt_check2.v           | [Photo2](#opt2-screenshot) |
| opt_check3.v           | [Photo3](#opt3-screenshot) |
| counter_opt.v          | [Photo4](#opt4-screenshot) |
| multiple_module_opt.v  | [Photo5](#opt5-screenshot) |
| multiple_module_opt2.v | [Photo6](#opt6-screenshot) |


2. D Flip-Flops

Files simulated using Icarus Verilog and YoSys:

| File Name     | Screenshot                 |
|---------------|----------------------------|
| dff_const.v   | [Photo1](#dff1-screenshot) |
| dff_const2.v     | [Photo2](#dff2-screenshot) |
| dff_const3.v      | [Photo3](#dff3-screenshot) |
| dff_const4.v      | [Photo4](#dfft4-screenshot) |
| dff_const5.v     | [Photo5](#dfft5-screenshot) |
| dff_async.v     | [Photo6](#dff6-screenshot) |



---

🔹 Notes

Asynchronous vs Synchronous DFF: Asynchronous responds immediately to reset/set; synchronous waits for clock edge.

---

