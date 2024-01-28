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
- Upper bound
- f(n) is O(g(n)) if, for all n > n0, f(n) <= c\*g(n)
- Ex. f(n) is O(n^2) if it runs less than 3n^2 operations when n>=4
- Properties
	- Reflexivity: f is O(f)
	- Constants: if f if O(g) and c > 0, then c*\f is also O(g)
	- Products: if f1 is O(g1) and f2 is O(g2), then f1f2 is O(g1g2)
	- Sums: if f1 is O(g1) and f2 is O(g2), then f1+f2 is O(max(g1, g2))
	- Transitivity: If f is O(g) and g is O(h), then f is also O(h)

Big-Omega notation
- Lower bound
- f(n) is $\Omega$(g(n)) if, for all n $\geq$ n0, f(n) $\geq$ c\*g(n) $\geq$ 0
- Ex. f(n) is $\Omega$(n), $\Omega$(n^2) if f(n) = 32n^2 + 4n
- Usage: bounding algorithms, any comparison-based sorting algorithm takes $\Omega(nlogn)$ comparisons in the worst case

Big-Theta notation
- Tight bound
- f(n) is $\Theta(g(n))$ if it is $O(g(n))$ and $\Omega(g(n))$
- **Proposition**: if $\lim\left(\frac{f(n)}{g(n)}\right)= c$  for a constant $0 < c < \infty$ , f(n) is $\Theta(g(n))$
	- If the limit is 0, then f(n) is only $O(g(n))$
	- If the limit is $\infty$, then f(n) is only $\Omega(g(n))$
	- Proof: ![[Pasted image 20240118112558.png]]
- Common functions
	- Polynomials: $\Theta(n^{highest\ term})$
	- Logarithms: $log_a(n)$ is $\Theta(log_b(n))$ for every $a > 1$ and $b > 1$
	- Logs and polynomials: $log_a(n)$ is $O(n^d)$ for every $a > 1$ and $d > 0$
	- Exponentials and polynomials: $n^d$ is $O(r^n)$ for every $a > 1$ and $d > 0$
	- Factorials: $n!$ is $2^{\Theta(nlogn)}$

Runtime examples
- Constant time ($O(1)$)
	- Conditionals, basic math, variable creation, pointer "use", array access, comparing elements, etc.
- Linear time ($O(n)$)
	- Linear search
- Logarithmic time ($O(logn)$)
	- Binary search
- Linearithmic ($O(nlogn)$)
	- Comparison sorts
- Quadratic ($O(n^2)$)
	- Naive closest points in grid
- Cubic ($O(n^3)$)
	- Naive 3-sum
- Polynomial time ($O(n^k)$)
	- Independent set of size k
- Exponential time ($O(2^{n^k})$)
	- Euclidian TSP


Next lecture: [[Stable Matching (AAD-5)]]