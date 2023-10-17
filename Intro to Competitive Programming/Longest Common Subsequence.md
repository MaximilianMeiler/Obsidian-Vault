2d dp - can be optimized to only 2 1d arrays

Let LCS(i, j) be the length of the LCS of S1\[1:i] and S2\[1:j]
- Return 0 if i=0 or j=0
- Take LCS(1, j)
	- returns 0 if any char up to j is equal to S1\[1]
	- Do the same for LCS(i, 1)
- Now consider LCS(2, j)
	- If the two chars are not the same, just return `max(LCS(i-1,j), LCS(i,j-1))`
	- If there is a match, return the max of the above case and `LCS(i-1, j-1) + 1`

Example: [['Edit Distance']], [['Interleaving String']], [['Wildcard Matching']]