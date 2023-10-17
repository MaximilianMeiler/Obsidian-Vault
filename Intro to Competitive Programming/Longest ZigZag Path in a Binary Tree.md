https://leetcode.com/problems/longest-zigzag-path-in-a-binary-tree/


Abstract through dp\[node]\[dir]: longest path from a node w a given direction
- `dp[node][left] = dp[node->left][right] + 1`
- `dp[node][right] = dp[node->right][left] + 1`
- do not take the max!