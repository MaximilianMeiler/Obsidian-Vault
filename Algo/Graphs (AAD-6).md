Previous lecture: [[Stable Matching (AAD-5)]]


![[Pasted image 20240125120057.png]]
![[Pasted image 20240125120502.png]]![[Pasted image 20240125120556.png]]

Definitions
- A **path** is a sequence of nodes where each consecutive pair is joined by a different edge $E$
- A path is **simple** if all nodes along the path are distinct
- An undirected graph is **connected** if for every pair of nodes $u$ and $v$, there is a path between $u$ and $v$
- A **cycle** is a path that starts and ends on the same node (n > 1)
	- A cycle is **simple** if all nodes are distinct (besides the first and last)
- A graph is a **tree** if it is connected and does not contain a cycle
- Theorem - Let $G$ be an undirected graph of $n$ nodes: Any two of these imply the third:
	- $G$ is connected
	- $G$ does not contain a cycle
	- $G$ has $n-1$ edges
- A **rooted tree** orients all nodes outward from one root

Problems
- **Connectivity**: Given two nodes $s$ and $t$, are they connected?
- **Shortest path**: Given two nodes $s$ and $t$, what is the length of the shortest path between them?

Breadth-First Search
- Explore outward from $s$, adding nodes one layer at a time
- **Theorem:** for each $i$, $L_i$ consists of all nodes at distance exactly $i$ from $s$. There is a path from $s$ to $t$ iff $t$ appears in some layer. *\[Proven by Induction]*
- **Property**: If $T$ is a BFS tree of $G = (V, E)$, with $(x, y)$ an edge of $G$, the levels of $x$ and $y$ differ by at most 1.
- **Theorem**: The above implementation of BFS runs in $O(m + n)$ time if the graph is given by its adjacency implementation ($O(1)$ lookup)
- **Theorem**: Upon termination of a DFS/BFS call that finds the nodes $R$, $R$ is the connected component containing $s$

Bipartite graphs
- An undirected graph $G = (V, E)$ is **bipartite** if the nodes can be colored blue or white, such that no two nodes of the same color are connected by an edge
- Many problems become easier if the underlying graph is bipartite
- **Lemma**: If a graph $G$ is bipartite, it cannot contain an odd-length cycle.
	- **Proof**: It's not possible to 2-color any odd-length cycle
- **Lemma**: Let $G$ be a connected graph, and let layers be produced by a BFS from node $s$. Exactly ONE of the following holds:
	- No edge of $G$ joins two nodes of the same layer ($G$ is bipartite)
	- An edge of $G$ joins two nodes of the same layer, and $G$ contains an odd-length cycle
	- **Proof** (by me lol): When coloring the edges, the layers alternate colors
		- Edges can only reach across 1 layer or along the same layer (otherwise nodes would be in adjacent layers anyways)
	- **Proof** (for first claim): 
		- Suppose no edge joins two nodes in the same layer
		- By BFS, each edge joins two nodes in adjacent levels
		- white nodes: on odd levels, blue nodes: on even levels
	- **Proof** (for second claim):
		- Suppose $(x, y)$ is an edge between $x, y$ in the same level $L_j$
		- Let $z = lca(x, y)$ be their lowest common ancestor
		- Let $L_i$ be the level containing $z$
		- The cycle between $z$, $x$, and $y$ is of length:
			- $1 + (j-i) + (j - i) = 1 + 2(j - i) = odd + even$, which is odd!
- **Corollary**: A graph is bipartite iff it contains no odd-length cycle
	- **Proof** (bipartite -> no odd-length cycles): It is not possible to 2-color a graph with odd-length cycles
	- **Proof** (no odd-length cycle ->  bipartite): Take the contrapositive of the second part of the previous lemma: 
		- If G does not contain an odd length cycle, then no edge of $G$ joins two nodes of the same layer $\Rightarrow$ $G$ is bipartite by the first part of the lemma

Directed graphs
- Strong component: Maximal subset of mutually reachable nodes

Directed acyclic graphs: \[Skipped]

Next lecture: [[Greedy Algorithms (AAD-7)]]