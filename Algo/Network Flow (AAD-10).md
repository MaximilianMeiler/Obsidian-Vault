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
- Now, just run this with the "double network"!