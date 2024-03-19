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