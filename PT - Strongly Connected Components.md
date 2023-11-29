Previous lecture: [[PT - Toposort]]


Finding regularly connected components
 - Use a bfs/dfs on all nodes, marking them as visited
	 - All nodes reachable from one "spread" are connected

Directed graphs instead have strongly connected components
- For nodes u and v, we can find a path from u to v and vice versa 
- Kosaraju's algorithm
	- G is a graph, L is an empty list
	- For each vertex in G, dfs from v, appending every connected one to L
		- (This is just toposort)
	- Reverse the edges of G, reverse the order of L
	- For each vertex v in L, perform assign(v, k) (another dfs)
		- Assign v as belonging to k
		- For each unassigned neighbor, run assign(u, k)
	- O(n + m)


Next lecture: [[PT - 2-SAT]]