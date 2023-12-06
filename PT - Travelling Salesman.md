Previous lecture: [[PT - Bipartite Graphs]]


Visit all nodes, and come back to the starting node
- Naive: O(n!)
- Bitmask DP solution
	- For each subset of vertices to visit and a fixed ending vertex, we only need to store the min cost for visiting that subject and ending at that index
	- This means that we have to break down every possible value at all points
		- ex. 3 possibilities, each with 2, each with 1
		- Store all visited nodes at any point and recur based on that
		- O(2^n \* n^2)

Bitmasking
- How do we store what elements are in our set at any point?
- Use an integer! 00000000 - no nodes are visited
	- Size n\*2^n required
	- Setting nodes to visited: `m = m | (1 << i)`
	- Check if a node is visited: `(m >> i) & 1`