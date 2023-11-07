Previous lecture: [[Graphs B (16)]]


Flow Networks
- Source node (s) and sink node (t)
- Each edge has a weight or "capacity"
- Min-cut problem
	- Group with the greatest outflow
- Max-flow
	- Given a network, the most amount of flow you can take from the source to the sink
	- Every node should output the same amount of flow it inputs
	- Greedy solutions don't work
	- Our solution - the residual network
		- Reversed version of all edges to flow water backwards
		- Allows us to correct our mistakes!
	- Ford-Fulkerson algorithm
		- Start greedy - Follow one path and pump as much as possible through (lowest capacity in path)
			- The residual flow for each will be the unused capacity per edge
			- You can use the residual graph's edges for this?
		- Edmond-Karp heuristics
			- The augmenting path is a shortest path from s to t in the residual graph
	- [['ACM Computer Factory']]
	
[['Not Escaping']]
[[TSP]]

Finding strongly connected components
- Strongly connected component- A subgraph where all nodes can get to every other node
- Tarjan's algorithm
	- O(V + E)
	- DFS - start at any node, label nodes with an increasing ID as you recur
	- Store low link value alongside any node
		- LLVAL = min(node's value, llval of children / node value of backlink nodes)
		- All nodes with the same low link val are strongly connected

[['Airports']]


Next lecture: [[Minimum Range Queries (18)]]