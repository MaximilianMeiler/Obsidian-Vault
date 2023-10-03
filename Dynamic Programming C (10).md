Previous Lecture: [[Dynamic Programming B (9)]]

0-1 Knapsack
- Given a set of items w/ weights and values, fill a sack with a weight limit
- Here, you can no longer take parts of items!
- Use a 2d array to memoize
	- Call recursive dp function with current item index & remaining capacity
	- You can actually only use two rows - dp\[i % 2, w]
		- Since you only access one row above at once, you can just keep looping one row to the next
		- You can even just use one row 
			- `for i = 1:n
				  `for w = W:w1
					  `dp[w] = max(dp[w], vi + dp[w-wi])
-  Finding items used - don't be memory inefficient! Just use backtracking!
	- Add item if `dp[i, k] != dp[i-1, k]`
- [[Partition Equal Subset Sum]]
- [['Last Stone Weight II']]


Next lecture: [[Dynamic Programming D (11)]]