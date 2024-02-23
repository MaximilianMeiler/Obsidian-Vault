Previous lecturer: [[Buffer Overflow (ORG-13)]]


When we multiply 2 N-bit numbers, the result requires 2N-bits of prevision
- If we need over 64 bits, we will not be able to fit something in a register
- MUL - outputs the lower half of quotient bits
	- MULH - outputs the upper half of quotient bits

Multiplication takes a while!
- $O(n^2)$
- Bit algorithm:
	- For every 1-bit in one number, add the other number left shifted per place
	- Ex $0010 \times 1011 = 1010 + 00100 + 000000 + 0010000 = 0010110$ 
- ![[Pasted image 20240221133025.png]]

Smarter multiplication
- Uses less hardware
	- Previous (64 bit multiplication): 64 bit multiplier, 128 bit multiplicand, 128 bit ALU, 128 bit product
- Intuition
	- Store product and multiplier in the same register, then multiplicand in separate
- ![[Pasted image 20240221134447.png]] ![[Pasted image 20240221134751.png]]


Next lecture: [[Floating Points (ORG-15)]]