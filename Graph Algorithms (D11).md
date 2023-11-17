
Shortest Path
- From a single source to all vertices
- BFS
	- O(V + E)
	- Unweighted
- Dijkstra's
	- O((V+E)\*logV) --- e + vlogv?
	- No negative edges
	- Relaxation per iteration
		- Originate from the unvisited vertex that has min distance to the source vertex
		- `d[v] = min(d[v], d[u] + w(u, v))
	- Implementation
		- V - tracks if a vertex has been visited
		- dist - a map that stores all distances to the source node
		- P - a map that stores the predecessor of each node on the path
	- ![[Pasted image 20231115141723.png]]
- Bellman-Ford
	- Negative edges
	- O(V\*E)
	- Relaxes all edges at each iteration
		- Iterates V times, ith iteration finds any shortest paths with i edges
		- (for i: 0->V) (for E: u->v) {relax u->v}

MST
-  (Undirected)
- Prim's 
	- Repeatedly add the adjacent vertex not in the graph that is connected with the smallest edge to the nodes in the graph
- Kruskal's
	- Add the least weighted edge that doesn't form a cycle