Previous lecture: [[Dynamic Programming (AAD-9)]]

A **flow network** is a tuple $G = (V, E, s, t, c)$
- Digraph with source $s$ and sink $t$
- Capacity $c(e) \geq 0$ for each $e \in E$

An **st-cut** is a partition $(A,B)$ for nodes with $s \in A$ and $t \in B$
- Its **capacity** is the sum of the capacities of edges from $A$ to $B$
- The max flow is equal to the smallest cut between $s$ and $t$
	- This is called the **min-cut**!

An **st-flow** $f$ is a function where:
- For each edges, flow is $\leq$ capacity
- For each node, flow in is equal to flow out
The **value** of a flow is (flow coming out of source) - (flow coming into source)
- Max-flow problem: Find a flow of max value 

### Ford-Fulkerson algorithm
- Find a path from $s$ to $t$, pump as much flow through that path as you can, repeat
	- Bottlenecks are found by minimizing $capacity(edge) - flow(edge)$
	- Between each repetition, only traverse through edges that are not already at full capacity while finding a path
	- If there is no longer a path from $s$ to $t$, we are finished!
- This doesn't entirely work because it never decreases the flow of an edge
- We'll create a **residual network** to bypass this issue
	- Instead of storing a flow and a capacity, we store capacity remaining in an edge and flow in the "opposite" edge
	- Essentially "how much flow can I still send" / "how much flow can I undo"
- Now, just run the previous greedy algorithm with this "double network"!
- The max flow calculated is always equal to the min cut's capacity!
- **Theorem**: F-F may not terminate OR converge to a value not equal to the max flow (with certain irrational capacity values)

- **Flow value lemma** : The overall value of a flow equals the net flow across any cut $(A, B)$ 
	- $val(f) = \sum_{\text{e out of A}}^{f(e))} - \sum_{\text{e in to A}}^{f(e)}$
	- (previously, we took the source as this cut, but it works for any cut)
	- **Proof**: 
		- The flow value is equal to the net flow out of the source
		- For any node, input and output is equal
		- Thus, by adding a node to a set containing the source, we do not alter the flow value
- **Weak duality**: For any flow $f$ and any cut $(A, B)$, $val(f) \leq cap(A, B)$
	- **Corollary**: If $val(f) = cap(A, B)$, $f$ is a max flow and $(A, B)$ is a min cut
- **Augmenting path theorem**: A flow $f$ is a max flow iff there are no augmenting paths
	- These 3 values are equivalent:
		- i - There exists a cut with value $f$
		- ii - $f$ is a max flow
		- iii - There is no augmenting path with respect to $f$
	- i -> ii is proved by the weak duality corollary
	- To prove ii -> iii, we prove ~iii -> ~ii
		- Suppose there is an augmenting path. We can improve the flow by following this path. Thus, $f$ is not a max flow.
	- Proving iii -> i
		- There is no augmenting path. All nodes we can reach from $s$ form a set $A$, the other nodes form the set $B$. 
		- In this case, the edges from A to B are flowing at full capacity, with residuals of 0. Thus, flow equals capacity out.
- **Theorem**: Given any max flow $f$, we can compute a min-cut in $O(m)$ time
	- $A$ is just all the nodes reachable from $s$

#### Ford-Fulkerson capacity scaling
- Assume all edge capacities are integers
- Throughout FF, all edge flows and residual capacities are integers
	- We start w/ 0 flow
	- We increment flow by a min edge capacity (integer)
		- Compute edge operations with this integer as well
- **Theorem**: FF terminates after at most $val(f*) \leq nC$ augmenting paths (where $f*$ is a max flow)
	- Flow is capped by $nC$, and each augmentation increases flow by at least 1
	- **Corrolary**: FF runtime is $O(mnC)$

### Matchings
- Given a graph, a subset of edges $M$ is a **matching** if eat node appears in at most 1 edge in $M$
- For **bipartite** graphs, lead one set of nodes from a source and the others into a sink. 
	- All edges would have weights of 1 (middle edges can have any weight)
	- **Theorem**: There is a 1-1 correspondence between matchings of cardinality $k$ and integral flows of value $k$ on the adjusted graph
		- Let $M$ be a matching with cardinality $k$
		- A flow $f$ would send 1 unit across all $k$ paths
		- ///
		- Let $f$ be a flow of value $k$
		- Each node in $L$ and $R$ participates in at most 1 flowed middle edge
			- Apply flow-cut lemma to prove $|M| = k$
		- **Corollary**: There exists a max flow that solves the max-cardinality matching
	- A **perfect matching** is where each node appears in one edge in $M$
		- Let $S$ be a subset of nodes, and $N(S)$ all the nodes adjacent
			- $|N(S)| \geq |S|$ is true for all sets iff a bipartite matching exists

### Other applications
- Two paths are **edge-disjoint** if they have no edges in common
	- Finding the max amount of disjoint paths - just assign 1 to all edges and run max flow
		- Every node has a flow-conservation value of 1, which means it can only be connected to one input and one output of a path
		- This is also the number of edges that have to be deleted in order to disconnect $t$ from $s$

Next lecture: [[TBD (AAD-11)]]