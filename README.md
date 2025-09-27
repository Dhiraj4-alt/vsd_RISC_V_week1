## 📘 Day 2 – Understanding the Sky130 Library

### 🔹 Theory Study: SKY130 .lib File

The .lib file in the Sky130 Process Design Kit (PDK) contains detailed information about standard cells. Each cell definition provides insights into power, area, timing, and input/output behavior.

PVT (Process, Voltage, Temperature) Variations

Process → Variations due to fabrication.

Voltage → Variations due to supply voltage.

Temperature → Variations due to operating temperature.


Example: sky130_fd_tt_025C_1v08

tt → Typical process corner.

025C → Temperature at 25°C.

1v08 → Supply voltage of 1.08V.


Cell Definitions in .lib

Different flavors of gates and cells are provided.

Includes area numbers, power consumption, leakage power, and pin definitions.

Input pins include information about transition power and load effects.

Larger cells → more area, less delay, but higher power.

Smaller cells → less area, more delay, but lower power.


---

### 🔹 Lab Exercise: Synthesizer Basics

The command synth -top is used to synthesize the top-level design.

The command read_liberty -lib <library_name> loads the standard cell library for synthesis.

Yosys uses this library to map RTL Verilog into actual logic gates.



---

### 🔹 Key Takeaways

Combinational circuits may produce glitches due to propagation delays.

Glitches → short, unwanted pulses where the output changes temporarily before stabilizing.

If output should stay at logic 1, glitches may cause it to momentarily drop to 0.

Flip-Flops are used to avoid glitches:

They store a stable value and capture input only on clock edges.

Transient glitches between clock edges are ignored.

Reset/Set pins initialize flip-flops (synchronous or asynchronous).


Overall → Sequential circuits remain stable and free from unwanted fluctuations.



---

