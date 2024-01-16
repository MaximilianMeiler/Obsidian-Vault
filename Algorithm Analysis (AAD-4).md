Previous lecture: [[Proofs Review (AAD-3)]]


Models of Computation
- Turing machine
	- Set of states and transitions between them
	- Input is fed through a tape of 1s and 0s
		- Tape and be read, written onto, and moved left and right
	- Runtime - number of steps
	- Memory use - length of tape used
	- No random access memory
		- Requires n^2 steps to detect n-bit palindromes
- Word RAM
	- Each memory location, input/output cell stores a w-bit integer
	- Primitive operations: math/logic operations, read/write memory, array indexing, pointers, conditionals
	- Runtime - number of primitive operations
	- Memory - number of cells used
	- Stuff like multiplying integers needs a more refined model

Algorithmic designs
- Brute force
	- Checks every possible solution to arrive at the correct one
	- Typically takes 2^n steps (or worse) for size *n* inputs
	- Ex. stable matching: test all *n*! perfect matchings
- Polynomial running time
	- Desirable scaling - when input doubles, algorithm should slow by a *multiplicative* constant **C**
	- Polynomial-runtime algorithms are called **efficient**. (This definition is insensitive to model of computation)

Algorithm analysis
- Worst-case analysis
	- Run-time *guarantee* for any size-n input
	- Generally captures efficiency in practice
- Probabilistic (expected) analysis
	- Ex. quicksort: 2nlogn
- Amortized
	- Worst-case running time for any sequence of n operations

Big-O notation
- f(n) is O(g(n)) if, for all n > n0, f(n) <= c\*g(n)
- Ex. f(n) is O(n^2) if it runs less than 3n^2 operations when n>=4
- Properties
	- Reflexivity: f is O(f)
	- Constants: if f if O(g) and c > 0, then c*\f is also O(g)
	- Products: if f1 is O(g1) and f2 is O(g2), then f1f2 is O(g1g2)
	- Sums: if f1 is O(g1) and f2 is O(g2), then f1+f2 is O(max(g1, g2))
	- Transitivity: If f is O(g) and g is O(h), then f is also O(h)
	- 