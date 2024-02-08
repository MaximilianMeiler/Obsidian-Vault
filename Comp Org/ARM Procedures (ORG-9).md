Previous lecture: [[ARM Decisions and Loops (ORG-8)]]


ARM memory model
- Memory is a linear array of $2^{47}$ bytes
	- Each address is 64-bit / 8 bytes
- Each address points to 1 byte of data (8 bits)
- Address usage
	- Below ...40 000: reserved (used by OS)
	- ...40 000 - ...1000 0000: text (stores code for user programs)
	- ...1000 0000 + 
		- Static data: static variables (declared in .data section)
		- Dynamic data: stack/heap![[Pasted image 20240206151056.png]]
			- Stack starts at ...7f ffff fffc

Stored Program Concept
- Each instruction is 4 bytes (32 bits)
- The instruction's address is the address of the first byte
	- "Word aligned" - addresses are divisible by 4
- Program Counter (PC) - address of the current instruction being executed

Stack
- Stack frame: block of data that contains register content and variable values, saved for when a procedure is called
- Frame pointer: outlines the last stack call, above the stack pointer


Next lecture: [[ARM Procedures - Stack Frames (ORG-10)]]