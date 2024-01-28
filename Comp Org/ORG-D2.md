
Examlet 1 topics:
- ARM instructions (R-format, D-format + endianness)
- Parts of a computer
- Computer Performance
- Benchmarking

How code is executed
- Source code is compiled into machine code
- Machine code is then turned into binary

Assembly instructions
- Commands are equal to opcodes, binary strings that tell the computer which operation to execute
- Registers store data in memory, these are the "variables" assembly interfaces with

R-format instructions
- Any math, bit shifts and logic operations
- 11-bit opcode (which instruction is run)
- 5-bit rm (second source register)
- 6-bit shamt (shift amount)
- 5-bit rn (first source register)
- 5-bit rd (destination register)

ARM instructions
- ADD X9, X10, X11
	- essentially X9 = X10 + X11
	- opcode = ADD, X9 = rd, X10 = rn, X11 = rm

D-format instructions
- Used for data/memory operations
- 11-bit opcode (which instruction is run)
- 9-bit address (address in main RAM memory)
- 2-bit op2 (00 for us)
- 5-bit rn (first source register)
- 5-bit rt (destination register?)
- LDUR X9, \[X10, \#40]
	- The value in X10 is a memory address, add 40 to this address, place the value found at that new address into X9
	- "Adding 40" means moving 40 addresses / 40 bytes forward (each address stores 8 bits / 1 byte)
- STUR X7, \[X12, \#0]
	- Place the data in register X7 at the address found in register X12

W0 instead of X0 - right (lower) half of the register X0
- Used for anything that addresses less than half a register (not a word, but half-words)

Endianness
- Big endian: first bytes are written in the most significant place (leftmost)
	- This ONLY fills the space that the word/half-word takes
	- ex. 00....5A4B for a half-word given registers {..., 5A, 4B, ...}
- Little endian: first bytes are written in the least significant place (rightmost)
	- It's not big endian reversed - chunks are still "in order"

Negative binary numbers
- Two's complement used to represent negatives
	- Most significant bit represents sign, others represent magnitude
- To convert to and from two's complement:
	- Flip all bits
	- Add 1
- Positive 4: 0100 / 00000100
- Negative 4 : 1100 / 11111100

Sign extension
- Certain instructions force-fill the whole register (?)
- Look at the first bit of the first value (little endian), and extend that 
	- 1 -> all F's
	- 0 -> all 0's

Parts of a computer
- Data is input as 1s and 0s
- A processor is made of 2 parts
	- Control: reads the opcodes, routes data respectively
	- Datapath: executes the operation desired by the control, writes the result to memory
- Output reads back from the memory

Performance
- Processor operates on a clock
	- Cycle time: length of a cycle (sec/cycle)
	- Clock rate: cycles/second (Hz)
- CPI: cycles per instruction
- speedup: relative speed between 2 computers
- 