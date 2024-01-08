https://leetcode.com/problems/maximum-students-taking-exam/


Note that columns are bipartite - taking alternating cols will always work
- However, this won't always maximize the answer

Maximum matching through exclusivity
- Connect grid "5" in B with 1, 3, 4, 6 in A - these are all exclusive
- Further connection
	- Seats 7 and 8 would also be exclusive with seat 5, as they can cheat off 5

Then, take the inverse of this max flow (nodes - result)
- Max flow is the number of students that have to be "removed" from the total