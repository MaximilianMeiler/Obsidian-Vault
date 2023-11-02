Previous lecture: [[Graphs A (15)]]


Directed acyclic graph (DAG)
- Directed, no cycles
- Every rooted directed tree is a DAG
- A directed graph is a DAG iff it can be topologically ordered
- What can we represent?
	- Family trees
	- Road maps
	- Airline routes
	- Class prereqs
	- Social media friends (sometimes)
	- Methods in a program
- Topological sort
	- A list of all vertices such that each vertex *v* appears before all vertexes reachable from *v*
	- Usually not unique per DAG
	- Applications
		- Scheduling project tasks
		- Finishing a degree
		- Recalculating spreadsheet cells
		- Compiling files with dependencies
		- Theoretical DP problems!
	- Algorithm 1
		- Store the number of incoming edges per node when creating list
		- Start with nodes that have no inputs
			- Decrease each child's incoming edges by 1 and repeat
			- O(v + e)
	- Algorithm 2
		- Modified DFS
		- Iterate through unvisited nodes one by one
			- For any parents, iterate through children
			- If no children / once children are searched, place node on stack
			- Keep track of visited nodes and skip them as not to duplicate them
	- [['Course Schedule']]
- Cycle detection
	- In a cycle, the first and last vertices are equal
	- "Back edges" connect nodes to their ancestors
		- Ancestor nodes are already in the stack
- Shortest path problems
	- BFS
		- Only works with non-weighted edges
	- Dijkstra's: single source, positive edges, O(E + VlogV)
		- [[Djikstra's]]
		- Set distance to all vertices to INF, except source, which is 0
		- A heap/prioQueue stores the edges away from the nodes we have already searched
		- For every edge on a popped node, set the child's weight to min (current weight, weight from following new edge)
	- Bellman-Ford: single source, all edges, O(VE)
		- If there is a negative cycle, there is no solution
		- Otherwise, a shortest path has at most V-1 edges
		- Solved using DP
			- Find all shortest paths for paths with 1 edge, with 2, etc
		- Improved version - Shortest Path Faster Algorithm
			- Similar to BFS but updates to account for edge weights (?)
			- Works on graphs w negative weights, but not with negative cycles
			- Works well on random sparse graphs
	- Floyd-Warshall: all-pairs, no negative cycles, O(V^3)
		- Uses DP
		- d(i, j, k) is the shortest weight from i to j using the first k nodes
		- dp(i, j, k) = min(dp(i, j, k-1), dp(i, k, k-1) + dp(k, j, k-1))
			- Choose to include a certain node k or not in path
		- Origin of paths also stored
		- Starts by filling table with given edge data
			- Then, update paths between edges by adding weights


Next lecture: [[Graphs C (17)]]