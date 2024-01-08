https://onlinejudge.org/external/119/11902.pdf


Task
- Reachability tests from vertex 0
	- If a node is dominant, you can't reach the nodes it dominates when it is removed
- Note: v < 100, meaning O(v^3) is acceptable

Adjacency matrix passed in
- Run dfs(0) to check what vertices can be reached
- For each vertex,
	- Temporarily turn off all outgoing edges of that vertex
	- Rerun dfs(0)
		- Stop the traversal if that vertex is re-traversed
	- Analyze dominance
