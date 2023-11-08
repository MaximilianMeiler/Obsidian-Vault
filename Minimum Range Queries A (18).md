Previous lecture: [[Graphs C (17)]]


Sum queries
- Given an array and two indices, find the sum of all vals between the indices
- Simplest question -> just compute prefix sum to get new subsums in O(1) time
	- sum(i, j) = sum(0,j) - sum(0, i-1)
	- Make sure to add a 0 to the front of the prefix sum array
		- sum(0, j+1) - sum(0, i) perhaps?
- [['Find All Good Indices']]
- [['Subarray Sums Divisible by K']]
- [['Range Sum Query 2D - Immutable']]

Range minimum queries
- Given an array and two indices, what is the smallest element between the indices?
- Naive - iterate through each query
	- O(1) precomputation, O(n) query time
- DP table precomputation
	- if i == j, the val there is just the min
		- Extrapolate from there - `dp[i,j] = min(dp[i][j-1], dp[i-1][j])`
	- O(n^2) precomputation + space, O(1) query time
- Is there any way to meld the time complexities of the dp and naive solutions?
- Block-based approach
	- Break the array into blocks, manually find the min of each block
	- For each query that full encompasses a block, just use that block's min in calculations
	- O(n) precomputation + space, O(2b + n / b) query time
		- If b = sqrt(n), query time is O(sqrt(n))
- Sparse table
	- For all indexes i, compute the rmq for ranges at i of size 1, 2, 4, 8, 2^k
		- Compute all 1s, then combine into 2s, 4s, etc
			- Each iteration will compute less and less as 2^k outpaces n-i
		- nlogn storage and time
	- Taking queries
		- Find the largest k where first starts at i, last ends at j
			- j - i = 7 - 2 = 5, use k = 2 (length of 4)
				- k = floor(log(j - i + 1))
			- Take min of precomputed 4-vals from i=2 and i=4 (7 - 4 + 1)
				- O(1) time!

Next lecture: [[Minimum Range Queries B (19)]]