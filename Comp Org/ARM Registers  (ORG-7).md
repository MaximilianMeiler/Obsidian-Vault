Previous lecture: [[Signed Integers (ORG-6)]]
Discussion: [[ORG-D3]]

To do 32-bit operations instead of 64-bit operations, use "W" instead of "X"
- W responds to the lower 32 bits of X

CMP
- Comparison operator - sees if inputs are greater/lesser
	- ex. CMP X22, X23
- B.GT \<label>: Jumps to \<label> if input is not greater (X23 >= X22)
	- B \<label>: Jumps to a label later in the program
	- Label usage: "\<label>:"

MOV
- Copies second operand to first
	- Can be used to place values into registers: "MOV X9, \#0"


Next lecture: [[ARM Decisions and Loops (ORG-8)]]