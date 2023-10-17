https://open.kattis.com/problems/presidentialelections


This is Knapsack, but you have to get it into a parseable state!
- Weight - number of voters you need to persuade to win the state
	- Discard any state impossible to win (but still count their delegates for total!)
- Value - number of delegates in the state
- Minimize the target of (total delegates) / 2 

1d Dp
- For all states, for all delegates:
	- `dp[w] = min(dp[w], leftToConvince[i] + dp[w-delegates[i]]`
- Then, choose the lowest value that gets you the delegates needed

