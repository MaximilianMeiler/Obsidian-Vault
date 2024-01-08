Previous lecture: [[Strings B (24)]]


Sweeping line algorithm
- Sweeping line is used to traverse Euclidian space
- Store all points in a priority queue ordered by x-coordinate
	- For each point, update the line and insert newly discovered points into Q
- Intersection problem (overlapping intervals)
	- R1 - iterate over intervals sorted by x, merging if adjacent intervals overlap
		- [['My Calendar']]
		- Length of unified segments - Klee's algorithm
			- Sort coordinates of all segments
			- Store indices of all left and right bounds
			- Sweep from left to right, using a running counter
				- L - add 1, R - subtract 1
				- 1 - one curr interval, 0 - no curr interval, 1+ - overlapping intervals
			- [['Teemo Attacking']]
			- [['My Calendar II']]
	- R2

Bit operations
- Finding the lowest bit set: `x & -x` or `x & ~(x - 1)`
	- Useful for Fenwick trees!
	- Used to represent subsets using bitmasks
- Exponentiation
	- You can calculate a^n using only log(n) multiplications!
		- a^256 = a^2^2^2^2^2^2^2^2
		- What about something like a^255? a^n = 
			- 1 if n == 0
			- a^(n/2)^2 if n > 0 and even
			- a\*a^(n-1/2)^2 if n > 0 and odd
			- Or, multiply up powers of 2, store them, and solve for 255
- Multiplication
	- Numbers X and Y are both multiples of a common base
		- sum(x\*B + y\*B)
	- Karatsuba multiplication
		- Split bit numbers in half: X = X0 + BX1, Y = Y0 + BY1
		- New product: (X0 + BX1)(Y0 + BY1)
			- X0Y0 + B(X0Y1 + X1Y0) + B^2(X1Y1)
				- [Optimized middle term calculation]
	- O(n^1.5), or O(nlogn) using FFT
	- [['My Calendar III']]


Next lecture: [[Final Review (26)]]