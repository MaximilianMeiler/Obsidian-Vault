Previous lecture: [[PT - Fast Fourier Transform]]


Can be run on DAGs to determine node order
- For each directed edge (u, v), u will come before v in the ordering
- Algorithm
	- Modified DFS
	- After we visit all of a node's neighbors, add the node to the front of the list
	- Thus, everything that depends on that node come after it


Next lecture: [[PT - Strongly Connected Components]]