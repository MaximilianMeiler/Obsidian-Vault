Previous lecture:  [[PT - Tries]]


Tree for storing intervals or segments
- Allows for querying on which of the stored segments contain data points that satisfy a specific requirement

Given some elements, we want...
- logn update and query
- Iterate down tree following left + right bounds, add stored values
- ![[segment-tree1-1391694816.png]]

Construction
- Use an array to store tree node values
	- Left child - 2i
	- Right child - 2i + 1
- Open 4n spaces in array

Querying
- Case 1: node's range includes range provided
	- Return node's sum
- Case 2: node's range includes too much data
	- Traverse to both children and re-check
- Case 3: node's range is outside of queries range
	- Return 0

Updates - logn, bubble up the tree and adjust all values encountered


Next lecture: [[PT - Aho-Corasick]]