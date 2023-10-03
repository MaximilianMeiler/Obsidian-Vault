Previous lecture: [[Dynamic Programming C (10)]]


Unbounded Knapsack
- Assume you now have an unlimited number of instances of each item
- Dp through the items, choosing to take any number between 0 and the max possible
	- `dp(i, w) = max(dp(i - 1, w - k*wi))` where 0 <= k*\wi <= W
	- You also have to iterate in the other direction apparently

Bounded Knapsack
- Assume you have a limited number of each item
	- "k" value is now capped by the max number of copies

 [['Making Change']]

Interval dp
- Optimal value of each interval is obtained by optimizing values between all sub-segments
	- `dp[i, j] = optimize(dp[i, k] + dp[k+1, j] + w[i,j])`
- [['Palindrome Removal' aka 'Zuma']]
- I

[['Valid Palindrome III']]