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

### 🔹 Table for Lab Observations

| File / Module               | Synthesis Type         | Photos          |
|-----------------------------|------------------------|-----------------|
| multiple_modules.v(Yosys)   | Synthysis         | Photo1()Photo2()|
| submodule1.v(Yosys)         | Single Sub-module Synth| Photo3()Photo4()|
| multiple_modules_.v         | Hierarchical Synthesis | Photo5()Photo6()|

![photo1](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day2_Labs/Screenshot_2025-09-23_20-31-42.png)
![photo2](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day2_Labs/Screenshot_2025-09-23_20-34-22.png)
![photo3]()
![photo4](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day2_Labs/Screenshot_2025-09-23_20-47-25.png)
![photo5](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day2_Labs/Screenshot_2025-09-23_20-40-51.png)
![photo6](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/day2_Labs/Screenshot_2025-09-23_20-36-04.png)

---

