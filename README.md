## 📘 Day 5 – If/Case Statements and Loops in Verilog


### 🔹 If Statements

Syntax
bash```
if (<condition>) begin
    ...
end else if (<condition2>) begin
    ...
end else begin
    ...
end
```
Key Points

Hardware synthesized from an if-else ladder is equivalent to multiplexers in series.

Limitations:

Inferred latches: If an if-else ladder is incomplete (no else for the last condition), the synthesizer may create a latch to hold the previous value.

Can be dangerous if unintended.

Can be used intentionally in designs like counters where the value should be retained until an enable signal is active.




---

🔹 Case Statements

Syntax
bash```
case (condition)
    2'b00: ...
    2'b01: ...
    default: ...
endcase
```
Key Points

1. Incomplete case:

If not all cases are specified, synthesis may infer latches automatically.

Always include a default to avoid unintended latches.



2. Partial assignments:

If a case statement has multiple outputs and one is not assigned in a condition, it may generate inferred latches.

Ensure all outputs are assigned in every case condition.



3. Overlapping cases:

Avoid having the same case conditions in multiple branches, as this may create ambiguity in hardware.





---

🔹 Loops in Verilog

1. for loop inside always block

Used for evaluating expressions in sequential or combinational logic.


Example: 32:1 MUX

always @(*) begin
    for (i=0; i<32; i=i+1) begin
        if (i == sel)
            Y = input[i];
    end
end

Example: 8:1 DEMUX

always @(*) begin
    Output_bus[7:0] = 8'b0;
    for (i=0; i<8; i=i+1)
        if (i == sel)
            Output_bus[i] = input;
end


---

2. generate for loop (outside always)

Used for hardware instantiation of multiple components.


Example: Instantiating 500 AND gates

generate
    for (i=0; i<500; i=i+1) begin : u_and_block
        and u_and(.a(a[i]), .b(b[i]), .y(y[i]));
    end
endgenerate

Useful for large repetitive hardware structures, like multiple ripple-carry adders.



---

🔹 Key Takeaways

Use else statements and default cases to avoid inferred latches.

Blocking (=) vs Non-blocking (<=) assignments are critical for correct sequential behavior.

For loops inside always are for logic evaluation.

Generate loops outside always are for hardware instantiation.

Efficient coding ensures smaller area, less power, and predictable hardware behavior.



---