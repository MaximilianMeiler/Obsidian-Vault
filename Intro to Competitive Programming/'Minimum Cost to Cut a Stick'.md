https://leetcode.com/problems/minimum-cost-to-cut-a-stick/


- Cost of the first cut is always n

- Intuition is to always cut in the middle, but how would you implement this?

Assume a sorted input (ex. \[1,3,4,5])
- Call dp(i,j)  (ex. i = 1, j = 4)
Add a 0 to the start of the cut input, and n to the end
- This allows us to calculate section length easily
- Let dp(i, j) denote the min cost to cut the rod with cuts from cut\[i] to cut\[j]
- `dp(i,j) = min(dp(i,k-1) + dp(k+1, j) + cut[j+1] - cut[i-1])
	- See how adding the 0 and the n allows us to find full length in base case
	- dp(i, j) is 0 when i > j
	- maybe change i and j when calling recursive dp?


0 1 3 4 5 7
        x
          
