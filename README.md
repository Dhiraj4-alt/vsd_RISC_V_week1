## 📘 VLSI Lab -Hierarchical vs Falatten work flow

### 🔹 YoSys Synthesis and Netlist Generation

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

### 🔹 Notes on Important Commands

write_verilog -noattr:

Exports the synthesized design into a clean Verilog file.

Removes unnecessary attributes/metadata like (* keep = 1 *), making it easier to read and simulate.


flatten:

Combines all modules into a single hierarchy, removing sub-module boundaries.

Useful to analyze the full gate-level netlist and for synthesis comparisons between hierarchical vs flattened designs.

---

### Prerequsites 

This is day 5 of Labs in the program and it has Files Taken directly from the github repo 
```
https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop/tree/eb29a38c8125be9020b3577dfeabbe6843bca1fa/my_lib/verilog_model
```
For steps of Execution You can refer 
the [day1_Labs](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day1_Labs/README.md) of this main Repo


---

### 🔹 Table for Lab Observations

| File / Module       | Synthesis Type          | Notes / Observations                        |
|--------------------|------------------------|--------------------------------------------|
| multiple_modules.v  | RTL Simulation         | Verified with Yosys                       |
| submodule1.v        | Single Sub-module Synth| Synthesized saperatly only 1 module out of whole design|
| multiple_modules_.v   | Hierarchical Synthesis | Compared hierarchical vs flattened design |

![photo1]()
![photo2]()
![photo3]()
![photo4]()
![photo5]()
![photo6]()


---

