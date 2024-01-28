Previous lecture: [[Benchmarking (ORG-4)]]
Discussion: [[ORG-D2]]


Registers
- ARM stores 32 registers, X0-X30 + XZR (constant zero)
- Each register stores 64 bits
	- 64 bit binary, or 16 vals of hex
- R-format instructions manipulate data within these registers (read/write)
- CPU has fast access to these

ARM basics
- ARM code all gets translated into 32-bit machine code
- RISC instruction sets contain 4 types of operations
	- R: Arithmetic and logic operations with registers
	- I: Arithmetic and logic with immediate values
	- D: Data transfer to and from memory
	- CB/B: Conditional branch and branch

Hex conversion
- Start on the right, split into groups of 4
	- Pad left with 0s if not completely filled
- Convert binary to digits
	- Anything greater than 9 takes letters (10=A, 11=B, up to F)
- Prefaced with "0x" (as opposed to 0b for binary)

ARM instructions
- R-format instructions
	- 11 bits: opcode
	- 5 bits: second source register
	- 6 bits: shift amount (all 0s if a non-shifting operation)
	- 5 bits: first source register
	- 5 bits: destination register
- I-format instructions
	- 10 bits: opcode
	- 12 bits: value of operand (immediate)
	- 5 bits: source register
	- 5 bits: destination register
- D-format instructions
	- 11 bits: opcode
	- 9 bits: address (shift from address in source register)
	- 2 bits: op2 (00 for us, always)
	- 5 bits: source register
	- 5 bits: destination register

Logical operations 
- LSL (logical shift left): Pad right side with 0s, remove left bits
	- Note - make sure to shift the *binary* value, not the *hex* value
	- Each left shift is a multiplication by 2
- LSR (logical shift left): Pad left side with 0s, drop right bits
- AND (^): 1 iff both inputs are 1
- OR (v): 0 iff both inputs are 0

D-format instructions
- Data has to be transferred into a register to be operated on, but there aren't enough registers to store all of a program's data!
- Note: in ARM, every byte (8 bits) has its own memory address
- ![[Pasted image 20240122214124.png]]
- Endian
	- When placing data from memory into a register, do we place the first-sequential memory address's data on the left or right of the register
		- Big Endian: Place the earlier memory on the left (most significant)
		- Little Endian: Place the earlier memory on the right (least significant)
- Note: when using load-byte commands (anything with under 32 bits), use "W#" instead of "X#" to address registers
	- When X is used instead of W, but not all bits of a register are filled, the last bit is sign extended (repeated into the rest of the bits)
- LDUR: Puts data from memory into a register
	- SDUR: Puts data from a register into memory
- Extensions on signed integers
	- Places 1s (negative -> FFFF) or 0s (positive -> 000) in the rest of the space in a register.
	- LDURSW (load signed word) only takes 32 bits from memory, the upper (left) 32 bits are padded with 0s or 1s instead (bit 31 extended / repeated in 32:63)


Next lecture: [[Signed Integers (ORG-6)]]