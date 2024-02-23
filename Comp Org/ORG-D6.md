
### Examlet 2 review

When making nested calls, what do we need to put on the stack?
- Adjust stack first (SUB 8/register)
- All arguments and temporaries required after the call
- Frame pointer
- Return address
Know the purpose of all these instructions in code

ARM Procedures

Integer multiplication
- Steps
	- Given Multiplicand and Product | Multiplier:
	- Is the least significant multiplier bit a 1?
		- If so, add the multiplicand to the product (first half)
	- Shift the P|M right one bit
	- Repeat until all of the multiplicand is shifted out

Floating point
- IEEE754 format
	- 32 bit: 1 bit sign / 8 bit exponent / 23 bit mantissa
	- Exponents are biased (-127)
- Converting Hex -> IEEE
	- 0C000000
	- \[0]\[00011000]\[0...]
		- Sign: positive
		- Exponent = 24 - 127 = -103
		- Fraction = 0
	- $1 \times 2^{-103}$
- Converting IEEE -> Hex
	- -4.75
	- $2^{2}+ 2^{-1} + 2^{-2}$ = 100.11 = 1.0011$\times 2^{2}$
		- Exponent = 2 + 127 = 129
	- \[1]\[10000001]\[001100...]
	- \[1100]\[0000]\[1001]\[1000]\[0000]...
	- 0xC0980...
- Special values
	- ![[Pasted image 20240221173956.png]]
- 