Previous lecture: [[Integer Multiplication (ORG-14)]]
Discussion: [[ORG-D6]]


Floating point numbers
- Unsigned 64 bit: 0 - $2^{64} - 1$
- Signed 64 bit: $-2^{63}$ - $2^{63} - 1$
- Normalized numbers
	- One non-zero digit to the left of the decimal, and an exponent
- Binary floats - always a 1 to the left of the decimal point
	- Exponents are always base 2 instead of base 10
- IEEE-754 format
	- 32 bits (31-0)
	- Bit 31 is the sign (0 is positive, 1 is negative)
	- 30-23 are the exponent (8 total)
	- 22-0 are the fraction (23 total) - does not include the leading 1
- Overflow/Underflow
	- Can happen with both exponent and fraction
	- Swap to 64 bit - 11-bit fraction
- Exponents are *biased* with a value of 127 (1023 for double precision)
	- Whatever is in the exponent, subtract 127 to get your real exponent
	- This allows us to represent negative exponents
		- Range: (-126, 127)
	- 00000001 $\rightarrow 2^{-126}$
	- 01111111 $\rightarrow 2^0$
	- 11111110 $\rightarrow 2^{127}$
- ![[Pasted image 20240221173956.png]]
- Decimal -> float conversion
	- The fraction: ex. 011 means $1 + 0 \times 2^{-1} + 1 \times 2 ^ {-2} + 1 \times 2 ^ {-3}$ 
	- Then, take the exponent, convert to decimal, subtract 127, and multiply the fraction by $2^{exp}$ 


81300000
1000 0001 0011 0000 ...
1 00000010 0110000...