https://vjudge.net/contest/582508#problem/C


Let dp(i, j) denote the min number of moves to remove a section
- If i and j are the same, dp(i, j) = dp(i + 1, j -1)
	- This does not count as an extra removal, it will just be added to another one
- If not, return ` 1 + min(dp(i, j - 1), dp(i + 1, j))
- If not return `min(dp(i, k) + dp(k + 1, j)` where i <= k < j

