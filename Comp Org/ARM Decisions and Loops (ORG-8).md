Previous lecture: [[ARM Registers  (ORG-7)]]


ARM B/CB format
- Flow control: Control the flow of program execution
- Program Counter: register that holds the address of the current instruction being executed
- Instructions are 32 bits / 4 bytes long

Conditionals
	``If \<predicate>
	`then <jump to branch address>
	`else <execute next instruction>
- ![[Pasted image 20240202172503.png]]
	- CBNZ: "Conditional Branch if Not Zero"
- If X22 and X23 are equal, subtract them:![[Pasted image 20240202173434.png]]
- CB Binary setup
	- 8-bit opcode
	- 19-bit address
	- 5-bit rd
- B Binary setup
	- 6-bit opcode
	- 26-bit address

Loops
- Combinations of conditionals and branches: ![[Pasted image 20240202175037.png]]
- Loop with an array:![[Pasted image 20240202175649.png]]

Using Flags
- SUBS: normal subtraction, but also leaves one of four flags:
	- N: negative result
	- Z: result is 0
	- V: result produced overflow (signed)
	- C: result produced carryout (unsigned overflow)
- B.\<XX> used to evaluate the flags
	- EQ: if result is zero (equal)
	- NE: if result is not zero (not equal)
	- LT: if result is negative (lesser)
	- GT: if result is positive (greater)
- Just add "S" to one of many operations!

Branching instructions
- B \<label>: branches to a label
- B.XX: conditional flag
- B \#\<num>: branches \<num> instructions forward
- BL \<label>: uses X30 to come back to where BL was called from after going to the label
- BR X30: Branch the address of an instruction in a register


Next lecture: [[ARM Procedures (ORG-9)]]