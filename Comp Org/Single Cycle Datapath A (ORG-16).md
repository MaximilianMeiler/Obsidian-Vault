Previous lecture: [[Floating Points (ORG-15)]]


Datapath design
- Combinations of gates (ex. ALU)
- Reads an instruction
- Executes instruction
- Writes registers
- Read registers are state values at previous clock cycle, written registers are the new state at the next clock cycle


Datapath components
- Control causes the correct actions to happen at the correct time
- PC stores address of current instruction
- Instruction memory stores the instruction
- ALU/ADDER calculates the next function's address
- Register file - has read/write ports (separate signals for register number and data)

R-Format datapath
- ![[Pasted image 20240301172525.png]]

D-Format datapath
- Address is sent to the data memory component
- Sign extender element replicates sign bit of 9-bit input for a 64-bit output
- ![[Pasted image 20240301173225.png]]

CB-Format datapath
- ![[Pasted image 20240301173309.png]]


Next lecture: [[Circuits for Datapaths (ORG-17)]]