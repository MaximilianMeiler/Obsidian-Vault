https://leetcode.com/problems/partition-equal-subset-sum/

- subsetSum = totalSum / 2
	- Always false if totalSum is odd
- Use Knapsack 0-1 to find a set of numbers that equal subsetSum
	- Use array elements as item weights
	- Return true if dp\[n]\[subsetSum] is true
