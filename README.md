📘 VLSI Lab -Hierarchical vs Falatten work flow

🔹 YoSys Synthesis and Netlist Generation

Below is a generalized YoSys script for synthesizing any RTL design and generating a clean gate-level netlist:
you can also refer the [day_1]() for detailed work flow 
```
# Start of YoSys script

# 1️⃣ Read the standard cell library
read_liberty -lib <library_file>.lib

# 2️⃣ Read your Verilog RTL design
read_verilog <rtl_file>.v

# 3️⃣ Synthesize top module
synth -top <top_module_name>

# 4️⃣ Map synthesized design to the library using ABC
abc -liberty <library_file>.lib

# 5️⃣ Insert D flip-flops using the library (if needed)
dfflibmap -liberty <library_file>.lib

# 6️⃣ Flatten the hierarchy (optional)
flatten

# 7️⃣ Write the final netlist to Verilog with no attributes
write_verilog -noattr <output_netlist>.v

# 8️⃣ Show the design in YoSys GUI
show
```

---

🔹 Notes on Important Commands

write_verilog -noattr:

Exports the synthesized design into a clean Verilog file.

Removes unnecessary attributes/metadata like (* keep = 1 *), making it easier to read and simulate.


flatten:

Combines all modules into a single hierarchy, removing sub-module boundaries.

Useful to analyze the full gate-level netlist and for synthesis comparisons between hierarchical vs flattened designs.




---

🔹 Example Table for Lab Observations

File / Module	Synthesis Type	Notes / Observations

multiple_modules.v	RTL Simulation	Verified behavior with GTKWave
submodule1.v	Single Sub-module Synth	Synthesized separately to check area/power
hierarchy_synth.v	Hierarchical Synthesis	Compared hierarchical vs flattened design
flattened_synth.v	Flattened Synthesis	Verified waveform & area with hierarchy



---

