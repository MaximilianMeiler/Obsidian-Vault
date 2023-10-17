Previous lecture [[Dynamic Programming F (13)]]


Matching problems to solution techniques:
- Dp: counting, optimization
	- May be greedy in simple scenarios
- Divide and Conquer: combine results from smaller subproblems 
	- No duplicate cases! If so, it would be Dp

Development
- Dp
	- Characterize the optimal substructure of an optimal solution
		- A problem exhibits optimal substructure iff an optimal solution to the problem contains the optimal solutions to subproblems
	- Recursively define the value of an optimal solution
	- Compute the optimal value in a bottom-up fashion
- Greedy
	- Convert into a problem where we make a choice and lead to ONE subproblem
	- Prove that the greedy choice is always the safe one
	- Prove that the remaining subproblem can also be solved greedily
- Two pointer
	- Converts a nested loop into a single loop
	- Slow-runner, fast-runner

Examples
- Dp
	- Kadane's Algorithm - [[Largest Sum Contiguous Subarray]]
		- `localMax(i-1)  = max(A[i], A[i] + localMax(i-1))`
	- Coin change
		- `solve(x) = min(solve(x-c1),...,solve(x-cn))`
	- Longest increasing subsequence: [['Nested Dolls']]
		- .
	- [[Longest Common Subsequence]]
	- Edit distance
	- Path in a grid
	- Knapsack 0-1 - [[Dynamic Programming C (10)]]
	- Bounded/Unbounded Knapsack - [[Dynamic Programming D (11)]]
	- [[Longest Palindromic Substring]]
	- [['Presidential Elections']]
- Greedy - [[Greedy B (7)]]
	- Meeting Scheduling
		- Pick ones w earliest finishing time
	- Multiple meeting rooms
	- Dijkstra's algorithm
	- Kruskal's algorithm
	- Prim's algorithm
	- Fractional Knapsack
- Two pointer
	- Remove duplicates from sorted array
	- Subarray sum
		- 