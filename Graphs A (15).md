Previous lecture: [[Midterm Review (14)]]


Types
- Directed/undirected
- Weighted/unweighted
- Multigraph
- Cyclic/Acyclic

Storage
- Adjacency Matrix
	- "True" if edge connects i and j, "False" if not
		- Weights may stand in for bools in weighted graphs
	- Properties
		- Memory: O(v^2)
		- Getting a vertex's out-edges: O(v)
		- Getting a vertex's in-edges: O(v)
		- Seeing if an edge exists: O(1)
		- Insert an edge: O(1)
		- Delete an edge: O(1)
	- Preferred when the graph is dense (E = O(v^2))
- Adjacency List
	- A collection of unordered lists representing a finite graph
		- For each node, list its edges
	- Properties
		- Memory: O(v + e)
		- Getting a vertex's out-edges: O(d) (edges applicable to the vertex)
		- Getting a vertex's in-edges: O(e)
		- Seeing if an edge exists: O(d) (check for element b in a's list)
		- Insert an edge: O(1)
		- Delete an edge: O(d)
	- Preferred when the graph is sparse (E = O(v))
- Edge list
	- Represents a graph as a list of its edges
		- For each edge, origin, destination, weight
	- Uncommon
	- Pros
		- Easily iterate over all edges
		- Memory: O(e)
	- Cons
		- Difficult to get edges incident to a specific vertex (O(e))

Graph modeling
- General steps
	- Identify the vertices (states)
	- Identify the edges (moving between states)
	- Identify the objective of the problem
- Implementation
	- Construct graph
	- Run graph algorithms
	- Reformat output
- [['Maze']]
- Traversal
	- To iterate effectively through all possible neighbors
		- Don't use a bunch of ifs!
		- Have an di and dj array, iterate through this instead
			- In Maze's case, di = \[0, 0, -1, 1], dj = \[-1, 1, 0, 0]
	- DFS - explore a single branch as far as possible before backtracking (stack, recursion)
		- Existing path between nodes
		- Complexity: O(v^2) for matrix, O(v + e) for list
	- BFS - explores all neighbors before moving on to the next depth (queue)
		- Shortest path between nodes
		- Complexity: O(v^2) for matrix, O(v + e) for list
- [['Connections']]
- [['Dominator']]
- [['8-puzzle']]

BFS vs DFS
- BFS - shortest path always
	- Storage can be very large due to queue used - (n-nary)^(height) used
- DFS
	- Stack never stores more than d\*p elements (p = longest path, d = highest out-degree)

Connected components
- [['Graph Connectivity']]
- Flood filling disconnected rooms

[[Water Jug Problem]]
[[Maze Problem]]


Next lecture: [[Graphs B (16)]]