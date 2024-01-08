Previous lecture: [[Sets, Maps, and Hash Tables (7)]]
Discussion: [[Graphs (D10)]], [[Graph Algorithms (D11)]]


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
		- Specify a source vertex S
		- Initialize two arrays and two sets
			- Set S - contains vertices for which we have computed the shortest distance
			- Set V-S - contains the vertices we still need to process
			- d\[v] contains the shortest distance from S to v
			- p\[v] is the predecessor of v in the shortest path from S to v
		- Add the edge closes to S to the computed set
			- Push in it's adjacent edges
			- Update parent+distance array if current distance is less than stored dist (relaxation - do this to each adjacent edge)
			- Mark the edge as computed
			- Repeat for all edges
- Bellman-Ford
	- Single-source to all vertices, negative weights allowed but no negative cycles
- Floyd-Warshall
	- All-pairs shortest paths
- A* search

Spanning trees
- Connects all vertices, with only edge between each vertex
- V-1 edges
- Min spanning tree: has the least total weight across edges
	- Prims algorithm
		- Divides vertices into two sets:
			- S, verts in the tree
			- V-S, verts not in the tree
		- Choose the edge with the smallest weight that connects an S-vertex w a V-S vertex, add it to the MST and update sets
	- Kruskals algorithm
		- Sort edges by weight
		- Add them to the MST if they don't form a cycle
			- Cycle detection
				- Modified DFS for back-edge detection
					- Store parents of each node you iterate thru
						- If a child v of node u is already visited and v is not u's parent, there is a cycle!
				- Disjoint sets (Union/Find)
					- find(i) - identifies the set that contains i
					- union(i, j) - merges the sets that contain i  and j
					- One array - stores the parent of a particular vertex
						- Each is originally -1
						- Find 
							- Returns i if arr\[i] is -1
							- Otherwise, calls find() on arr\[i] (the parent)
							- May be smart to cache - arr\[i] = find(arr\[i])
							- You may want to store size of each tree, move left under right if size/rank of left is less than that of right

Topological sort
- Ordering of vertices such that if there is an edge vi -> vj, vj comes after vi
- Algorithm
	- Find vertices with no edges, print, then remove them and repeat
	- Modified DFS
		- Iterate through unvisited nodes one by one
					- For any parents, iterate through children
					- If no children / once children are searched, place node on stack
					- Keep track of visited nodes and skip them as not to duplicate them


Next lecture: [[Algorithm Paradigms (9)]]