
Compilation Process
- Processor contains control and datapath
- How does a computer use binary to execute instructions?

Single Cycle Datapath
- ADDI
	- Reads address of instruction, sends opcode to control
	- Sends Rn (to be read) and Rd (to be written) to the registry
	- ALU adds immediate from instruction to read data
	- MUX takes ALU-computed data and writes it to Rd
- LSL
- CBZ
	- Forgot to write these down

Control Signals
- Check the notes for these specifics

Pipelining

Speedup/Amdahl's Law
- $speedup(f, n) = \frac{1}{(1-f + \frac{f}{n})}$
	- f: fraction of program that is parallelizable
	- n: number of stages
- If infinite number of instructions: $\frac{n}{f}$ (f == 1)