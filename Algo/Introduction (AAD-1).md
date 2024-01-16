Previous lecture: N/A


Course scope:

Algorithms
- Take input and output (possibly) - like a mapping between 2 sets
Algorithm abstraction
- Turning one problem into another
	- Ex. Stable Matching Problem
		- Given sets *A* and *B*, and functions 
			- f(A): *A* x *B* -> **R** (how highly a ranks b)
			- f(B) *B* x *A* -> **R** (how b ranks a)
		- Find a bijective function *M*: *A* -> *B* where there do not exist pairs (a, b) & (a', b'):
			- a,a' in A, b,b' in B
			- a != a', b != b'
			- M(a) = b
			- f(A)(a, b) < f(A)(a, b') and f(B)(b, a) < f(B)(b, a')
Algorithm complexity
- Big-O notation
Algorithm types:
- Graph-based
- Greedy
- Divide and conquer (non-overlapping subproblems)
- Dynamic programming (overlapping subproblems)
- Network flow
Problem complexity
- Finding the complexity lower-bound for all algorithms that solve a given problem
	- (comparative) Sorting - Omega(nlogn)
	- Searching - Omega(nlogn)
- EXPTIME-complete problems (ex. Omega(2^n))
	- Deciding if an algorithm halts in  a fixed number of steps
	- Evaluating a generalized (any-size) chess, checkers, or go board
- P vs NP
	- P: set of problems solvable in polynomial time
	- NP: set of problems for which a solution can be verified in polynomial time
	- Hamiltonian cycle: visting every node in a graph, forming a cycle
		- in NP: A completed path can just be traced in n-time
		- in P?
	- How to cope with NP-complete problems:
		- Approximations: find a solution SOL that is close enough to the optimal solution OPT
			- Want to bound the ratio of val(SOL) / val(OPT)
			- Doesn't always work - TSP cannot reach certain approximation bounds


Next lecture: [[Summary of Topics (AAD-2)]]