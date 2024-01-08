Previous lecture: [[PT - 2-SAT]]


Flow networks
- Each edge has a capacity and is directed
- Source: edge w no incoming edges
- Sink: edge w no outgoing edges
- Flows
	- Amount of flow from source = amount of flow from sink

Ford-Fulkerson algorithm
- Residual network
	- The opposing variant of each edge, which carries how much flow can still be pushed rather than how much was pushed (cap - edge flow)
- Algorithm
	- Set all flows to 0
	- While there is a path from the source to the sink (even thru the residual graph):
		- Find the bottleneck (lowest val along the path)
		- Update the edges (and their opposers) correspondingly

Dinic's algorithm
- Pathfinding algorithm to get from source to sink
- Constructs a level graph GL, which is repeatedly reconstructed
	- Level graph - assigns each node from its distance from s
		- Only includes edges (u, v) where dist(v) = dist(u) + 1
- Algorithm
	- Construct level graph
	- Flow everything possible s->t through this level graph 
	- Construct a new level graph (fully-flowed edges no longer connect nodes!)
		- Residual edges can be included if they aren't full anymore too!
	- Keep reflowing and reconstructing until distance to the sink is INF


Next lecture: [[PT - Bipartite Graphs]]