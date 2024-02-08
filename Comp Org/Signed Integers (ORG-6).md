Previous lecture: [[ARM Programming (ORG-5)]]


Representing negatives in binary
- Why not just use binary normally for magnitude, then tack on an extra bit for pos/neg?
	- This leaves 2 representations for the number 0!
- Instead, compute "Two's complement binary numbers"
	- Invert the bits of a normal binary number (one's complement)
	- Then, add one!
- Converting complement -> decimal
	- Take the negative magnitude of the first 1 bit
	- Add the magnitude of each following 1 bit

Binary overflow
- Unsigned 8-bit binary can represent numbers 0-255 (11111111)
- 256 will overflow to 00000000
- Signed 8-bit binary can represent numbers -128 to 127 (10000000 to 01111111)
	- Note that the first bit always represents the cardinality! (+/-)
	- Cannot always add positives without overflowing (first bit may become 1!)
		- Arm stores V (signed) and C (…) flags on the register to check for such inconsistencies (i.e. adding 2 positives becomes a negative)


Next lecture: [[ARM Registers  (ORG-7)]]