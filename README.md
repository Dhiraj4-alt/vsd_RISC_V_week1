Got it 👍 I’ll polish your Day 2 README section so that it’s very clear, structured, and professional. Here’s the refined version you can directly paste:


---

📘 Day 2 – Understanding the Sky130 Library

🔹 Theory Study: SKY130 .lib File

The .lib (Liberty) file in the Sky130 Process Design Kit (PDK) contains detailed descriptions of standard cells. It defines their functionality, timing, power, and area information, which are essential for synthesis.

Key Points

1. PVT Variations (Process, Voltage, Temperature):

2. Process → Variations due to fabrication.

3.Voltage → Variations due to supply voltage.

4. Temperature → Variations due to operating conditions.


Example: sky130_fd_tt_025C_1v08

tt → Typical process corner.

025C → Operating temperature at 25°C.

1v08 → Supply voltage of 1.08V.

---

### Cell Definitions in .lib

Describes gates (cells) and their names.

Contains different versions (“flavors”) of the same cells.

Provides information on:

Area numbers.

Leakage power.

Power consumption.

Number of pins and transition power for each input.

---

### Impact of Cell Size

Larger cells → more area, less delay, but higher power.

Smaller cells → less area, more delay, but lower power.




---

### 🔹 Lab Exercise: Synthesizer Basics

synth -top → Synthesizes the top-level design.

read_liberty -lib <library_name> → Loads the Sky130 standard cell library into Yosys.

The synthesis process maps RTL Verilog into actual logic gates using the provided .lib.



---

### 🔹 Key Takeaways

Combinational circuits can produce glitches due to propagation delays.

Glitches → Short unwanted pulses where the output changes temporarily before settling.

Example: An output expected to stay at logic 1 may briefly drop to 0.


Flip-Flops are used to eliminate glitches:

They capture values only on clock edges (rising or falling).

Transient glitches between clock edges are ignored.

Reset/Set pins initialize flip-flops.

Synchronous → Controlled by the clock.

Asynchronous → Independent of the clock.



✅ This ensures sequential circuits remain stable and reliable.



---
