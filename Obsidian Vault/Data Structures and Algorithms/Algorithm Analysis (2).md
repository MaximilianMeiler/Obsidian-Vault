Previous lecture: [[C++ review (1)]]


Algorithm
- A step-by-step procedure for solving a problem

Algorithms
- Design-oriented
- Pseudocode
- Corrected w proofs
vs Programming
- Implementation-oriented
- C++, …
- Corrected w unit tests

There are always multiple ways to solve a problem!

We focus on time complexity - space is cheap!

Approaches to test programs
- Timing - relation between element run / time taken displays type of relationship to input
- Counting - count the number of operations
	- We will assume that all operations are equal
	- 3n + 4![[Pasted image 20230824154332.png]]
- Asymptotic analysis - remove all insignificant variables
	- Big O
		- T(n) is O(f(n)) if T(n) <= c\*f(n) for all n >= n0
		- "Upper bound"
	- Big Omega
		- T(n) is Om(g(n)) if T(n) >= c\*g(n) for all n >= n0
		- "Lower bound"
	- Big Theta
		- T(n) is Th(g(n)) if both O(n) and Om(n) apply
		- Exact order of growth
	- Rules for analysis:
		- Separate code snippets add and are independent: O(n + n) -> O(2n) -> O(n)
			- \* only simplify this if inputs of both code parts grow at the same rate
		- Drop constants
		- Drop lowest order terms
		- These series may help for special cases:![[Pasted image 20230831151117.png]]
- Complexities are separate from best/average/worst cases

Ex: Array peak finding
- From a point in the array, head towards the adj index with a higher value than that of the current index
- Runs in log(n) time instead of n time
- "Reduce and conquer" approach

Computing space complexity: either....
- Count auxiliary space allocated proportional to input size
	- Or add input space to this
- Note that calling functions also takes memory - recursions is usually not O(1)

Writing Pseudocode
- Get rid of jargon and library syntax
- Make indentation consistent
- Keep keywords
- Keep method signatures
- Note abbreviations


Next lecture: [[Lists, Stacks, Queues (3)]]