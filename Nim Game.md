https://leetcode.com/problems/nim-game/


You could think of this through DP
- `dp[i] = !dp[i-1] || !di[i-2] || !dp[i-3]`
- ^ this checks if any possible move leads to a fail case

But think about it again...
- If n is 1, 2, or 3, you win
- If n is 4, you lose (forced into giving opp a winning state)
- Thus, a 5,6,7 wins
- ...and 8 loses...
- etc

- n % 4 != 0


https://web.mit.edu/sp.268/www/nim.pdf