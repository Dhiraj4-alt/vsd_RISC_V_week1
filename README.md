## 📘 Day 1 – VLSI Lab: GoodMux Simulation & Synthesis

🔹 Lab Objective

Simulate and verify a Multiplexer (GoodMux).

Perform RTL simulation using Icarus Verilog and waveform viewing in GTKWave.

Synthesize the design using YoSys and map it to a standard cell library.

## 🔹 Pre requsites

1. Create a file called vlsi
   ```
   mkdir vlsi
   ```
2. git clone this repository
   ```
   git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop/tree/eb29a38c8125be9020b3577dfeabbe6843bca1fa/my_lib/verilog_model
   
   ```
3. U can check the files
   ```
   cd vlsi/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/
   ```   
![photo1](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/3a8fd6200c6ae98af0f54ad0f49e7e439e79f496/day%201%20photo%201.png
)
---

## 🔹 Step 1: RTL Simulation (Icarus Verilog + GTKWave)

1. Go to the VerilogFiles directory:
```
cd vlsi/sky130RTLDesignAndSynthesisWorkshop/DC_WORKSHOP/verilog_files/

```
2. Compile RTL and testbench:
```
iverilog good_mux.v tb_good_mux.v
```

3. Run the simulation (generates a.out):
```
./a.out
```

4. Open the generated VCD waveform in GTKWave:
```
gtkwave tb_good_mux.vcd
```
![photo2](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/5867a070a6850ff9883c05ac4719cfc006c3d29d/Screenshot_2025-09-22_17-44-23.png)
``
![photo3]()
``
![photo4]()
``
![photo5]()
``
![photo6](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/6e12b1957da53c83b52c2b19cf23b540a63b3b97/Screenshot_2025-09-21_19-58-18.png)
---

## 🔹 Step 2: Synthesis (YoSys)

1. Start YoSys in the same directory:
```
yosys
```

2. Read library and RTL files:
```
read_liberty -lib /home/dhiraj/vlsi/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib

read_verilog good_mux.v

```

3. Run synthesis (specify top module):
```
synth -top good_mux

```
it shows the elemsths like wires flipflops registers gates etc...

4. Map synthesized design to library:
if its a flip flop file
```
dfflibmap -liberty /home/dhiraj/vlsi/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib

abc -liberty /home/dhiraj/vlsi/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib

```
```
abc -liberty /home/dhiraj/vlsi/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib

```
5. Visualize the synthesized netlist:
```
show
```
After this step, you can inspect the gate-level design and confirm the structure matches expectations.


![photo7](https://github.com/Dhiraj4-alt/vsd_RISC_V_week1/blob/80e8a7d18e193100302495cd9471cc7eac3f83d5/Screenshot_2025-09-22_17-43-47.png)
``
---


### 🔹 Notes

Make sure the testbench signals match the RTL/netlist ports.

Compare RTL simulation waveform vs synthesized design waveform in GTKWave.

Screenshots and observations can be stored in a Screenshots/ folder for documentation.



---
