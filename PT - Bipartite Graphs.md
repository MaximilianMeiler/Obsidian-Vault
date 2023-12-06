Previous lecture: [[PT - Max Flow]]


Definition
- A graph where edges can be colored red and blue, where no two edges of the same color are adjacent

Checking
- DFS
- Start at a point, make it blue, make its neighbors red and swap
- If we color a vertex the same color as one of its neighbors, the graph is not bipartite

Maximum matchings
- Matching - subset of edges with no shared vertices
- Maximum matching - matching with maximum size
- Finding maximum bipartite matchings
	- Connect all blue nodes to red nodes with edges of weight 1
	- Connect all blue nodes to a source, red nodes to a sink
		- These also have edge weight 1
	- Run max flow

Vertex cover
- Subset of vertices that includes at least one endpoint of every edge
- Minimum vertex cover
	- Smallest possible vertex cover (least nodes)
	- König's theorem: max matching and min vertex cover have equal size


Next lecture: [[PT - Travelling Salesman]]