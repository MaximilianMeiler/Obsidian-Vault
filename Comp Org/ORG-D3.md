
Anatomy of an ARM program
- . section .data
	- Used to declare constants and free up space
- .section .text
	- .global main: shows main to compiler
	- main:
	- exit: : contains supervisor calls to stop the program

Function calls
- All C functions are available to be called with bl, such as printf and scanf
	- Branch and link: perform a branch, then come back to calling address
- ldr allows for loading X0-X7 with argument data to be used for functions
	- X0-X7 will be automatically used, but are not preserved between calls

Functional notes
- We don't need to use the "i" for immediate instructions
- You can't use the register XZR with an immediate instruction
- "mov" can be used to transfer data into registers and copy it between registers
	- LDR occurs from memory to register, not register to register

Debugging
- In your compile statement, add -g to the end
- Launch with gdb \<progName>
- set breakpoints with b \<sectionName> / \<lineNum>
- type "n" or "next" to proceed
- use "i r" to look into registers
- "r" to restart
- "x/nfu to view memory" (?)
	- n - repeats
	- f - display type
	- u - storage type