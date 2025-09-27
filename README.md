##📘 Day 1 – VLSI Lab: GoodMux Simulation & Synthesis

🔹 Lab Objective

Simulate and verify a Multiplexer (GoodMux).

Perform RTL simulation using Icarus Verilog and waveform viewing in GTKWave.

Synthesize the design using YoSys and map it to a standard cell library.



---

🔹 Step 1: RTL Simulation (Icarus Verilog + GTKWave)

1. Go to the VerilogFiles directory:
'''
cd VerilogFile
2. Compile RTL and testbench:



iverilog GoodMux.v GoodMux_tb.v

3. Run the simulation (generates a.out):



./a.out

4. Open the generated VCD waveform in GTKWave:



gtkwave GoodMux.vcd


---

🔹 Step 2: Synthesis (YoSys)

1. Start YoSys in the same directory:



yosys

2. Read library and RTL files:



read_liberty your_library.lib
read_verilog GoodMux.v

3. Run synthesis (specify top module):



synth -top GoodMux

4. Map synthesized design to library:



abc -liberty your_library.lib

5. Visualize the synthesized netlist:



show

After this step, you can inspect the gate-level design and confirm the structure matches expectations.



---

🔹 Notes

Make sure the testbench signals match the RTL/netlist ports.

Compare RTL simulation waveform vs synthesized design waveform in GTKWave.

Screenshots and observations can be stored in a Screenshots/ folder for documentation.



---

If you want, I can also make a “Day 1 Labs” section for your main README with direct links to files, screenshots, and branches, so your repo looks fully professional and navigable.

Do you want me to create that next?

