## Chapter 5

#### Problem 1
Start by taking the median (n/2) of each database. Drop all values below the lower median, and all those above the greater median. Here, we've essentially narrowed down our median search by dropping an equal amount of the highest and lowest values. Adjust bounds respectively and repeat. Repeated halving gives us $log(n)$ operations total
.
#### Problem 6
Start at the root and probe its value. Probe both children, and move to a child if they are less than the root. If neither are less, the "current node" is the min. Repeat until no children are left, in which case the current node is a minimum.

## Chapter 6

#### Problem 1
- 2-3-2
- 3-2-2-3
- House-robber type situation.
	- `OPT(n) = max(OPT(n-1), OPT(n-2) + w[n])`
	- Base cases: 1 node = take, 2 nodes = take greater

#### Problem 3
- The correct answer is as listed (and what the algorithm finds). However, we can disprove it w/ the following adjacency list: \[2/3, 5, 4, 5, x]
- DP
	- Recurrence: iterate through all connections of a node, maximize the optimal outcome for all

#### Problem 19
- Base case: Return true if s = s.size
- Both y+x indexes match the s-index
	- `OPT[x][y][s] = OPT[x+1][y][s+1] || OPT[x][y+1][s+1]
- Otherwise, just take the opt of the one string that matches
	- `OPT[x][y][s] = OPT[x+1][y][s+1]
	- `OPT[x][y][s] = OPT[x][y+1][s+1]
- If no strings match, return false
- Return `OPT[0][0][0]`

#### Problem 22
- Run Bellman-ford to find the shortest path from source to target (this handles negative edges)
- Instead of having an array of parents, store a nested array of many possible parents (for each path of same weight leading in)
- When you're iterating backwards, 
	- Assign source node weight 1
	- When you're iterating backwards, add the sum of `weight[neighbor] * #edges to that neighbor`
		- Make this the weight of that node
	- Diagram attached for convenience: ![[Pasted image 20240323213804.png]]