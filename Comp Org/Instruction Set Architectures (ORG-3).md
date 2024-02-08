Previous lecture: [[Bits, Binary, Digital Logic (ORG-2)]]

Parts of a computer (definitions):
- Input: Writes data and instructions to memory
- Datapath: Executes instructions
- Control: Sends signals that determine the operations of datapath, memory, input, and output
- Memory: Stores instruction and data
- Output: Presents results to user

What is an ISA?
- Defines instruction formats (structure, instruction fields)
- Defines how memory is organized (registers, bytes)
	- Registers: fast cpu memory
	- Cache: middle ground (not defined by ISA)
- Defines how memory is addressed (relative/physical address)
- Defines how exceptions are handled (interrupts, exceptions)

Accumulator architecture
- ALU (arithmetic logic unit) outputs to the accumulator
- One ALU operator comes from the accumulator, the other from memory
- Types of architecture
	- General Purpose Register-Memory Architecture![[Pasted image 20240117173536.png]]
	- Stack Architecture ![[Pasted image 20240117173604.png]]
	- High Level Language Architecture (no machine instructions!) ![[Pasted image 20240117173703.png]]
	- Reduced Instruction Set Computer (RISC) ![[Pasted image 20240117173726.png]]
	- Inherently Parallel Instruction Execution Schemes
	- Compute Unified Device Architecture (CUDA) ![[Pasted image 20240117173922.png]]
		- Instantiates programs on many parallel threads

CISC vs RISC
- Complex instruction set computer: translation from high-level language is shorter but more costly to decode instruction formats
- Reduced instruction set computer: longer translation from high-level language (less instructions) but hardware decoding is simpler

ISA families
- Upwardly compatible - new, higher performance models can run older, lower code

ARM instruction set (RISC)
- R: Arithmetic and logic operations with registers
- I: Arithmetic and logic with immediate values
- D: Data transfer to and from memory
- CB/B: Conditional branch and branch


Next lecture: [[Benchmarking (ORG-4)]]