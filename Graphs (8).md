Previous lecture: [[Sets, Maps, and Hash Tables (7)]]
Discussion: [[Graphs (D10)]]


Graphs 
- An ordered pair of a set of nodes and a set of edges (V, E)
- Terminology
	- Weights: associated with edges
	- Adjacent vertices: B is adj to A if an edge points from A to B
	- Simple graphs: no loops and multi-edges
	- Path: sequence of vertices, with each successive one adjacent to its predecessor
		- Simple path: no repeated intermediary vertices
		- Cycle: simple path where first/last vertices are the same
		- Connected vertices: vertexes with a path between them
		- Connected graph: graph with a path between all vertices
- Types
	- Directed vs Undirected
	- Weighted vs Unweighted
	- Connected vs Unconnected
	- Cyclic vs Acyclic
	- Dense vs Sparse
		- Dense: E ~= V^2
		- Sparse: E ~= V

\[Lecture skipped - I was playing 5d chess]
\[More other stuff skipped]

Shortest weighted s-t path
- Dijkstra's algorithm
	- Single-source to all vertices, no negative weights
	- Algorithm
		- 
- Bellman-Ford
	- Single-source to all vertices, negative weights allowed but no negative cycles
- Floyd-Warshall
	- All-pairs shortest paths
- A* search