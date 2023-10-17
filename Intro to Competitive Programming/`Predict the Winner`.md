https://leetcode.com/problems/predict-the-winner/


Keep track of the difference between ur num and ur opps num, maximize this
- `dp[i,j] = dp[i+1][j] + add nums[i] || dp[i][j-1] + nums[j]`
	- i, j are indexes of the subsection in play
	- Use a 2d array to store solved memos of i and j
		- When i == j, you are forced to take the value
		- When |i - j| == 1, take max - min (|dp\[i]\[j-1] - dp\[i+1]\[j]|)
		