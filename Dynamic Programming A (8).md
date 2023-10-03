Previous lecture: [[Greedy B (7)]]


Remember the coin change question?
- Take a coin system with denominations of 1c, 7c, and 10c
	- Greedy will no longer work!
	- But brute force is too slow...
	- Instead, work upward
		- Each representation is each coin + (val - that coin)

Used for optimization problems and counting problems
- Brute force combined with memoization
- Steps
	- Characterize structure of optimal solution
		- Define this recursively
	- Compute optimal subproblems top-down or bottom-up w/ a memo table
- Top-down
	- Backtrack, but previously computed solutions are already stored
	- Easier
- Bottom-up
	- Prep a table with a size of the amount of distinct problem states
	- Fill the table with bases, and then work your way up to the required value
	- Faster - no recursive calls
	- Doesn't always use max memory

Sum (1d problem)
- Find the number of different ways to write a given n using 1,3,4
- D(n) = D(n-1) + D(n-3) + D(n-4)
	- Only works if different orders are considered distinct!

- [[Nim Game]]
- [[`Predict the Winner`]]
- [[Largest Sum Contiguous Subarray]]
- [[Decode Ways]]
- [[Word Break]]


Next lecture: [[Dynamic Programming B (9)]]