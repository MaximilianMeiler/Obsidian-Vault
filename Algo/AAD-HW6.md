## Chapter 8

#### Problem 1
a) This problem can be solved greedily in polynomial time. Thus, it is in $P$, and thus also in $NP$. Because of this, it can be reduced all $NP$-complete problems (like interval scheduling).
b) If Independent Set (an $NP$-complete problem) can be reduced to Interval Scheduling, then $P = NP$

#### Problem 2
If an NP-complete problem reduces to it, all NP problems will.
Independent set: nodes that don't share an edge
Turn each node into a person, if they share an edge set a column corresponding to that edge to 1 for both of them.
- When a diverse subset is selected, none of the nodes that share an edge will be selected!

#### Problem 4
a) This is NP-complete and can be reduced into by Independent Set. 
- For an independent set, make each edge a resource and correspond processes to it which are the nodes that share that edge.
b) A simple $n^2$ algorithm works here - check each pair of nodes and see if they share processes. If none of them do, a 2-set exists
c) Can you do this in P? Maybe you just swap the two sides of the independent set reduction in a
d) This should equal the independent set reduction in part A. Thus, I really hope this is also NP-complete.

#### Problem 17
- This problem is not solvable in polynomial time. Is it in NP?
	- Say we have a certifier which takes a certificate, a series of nodes that form a 0-weight-cycle. We'd just have to check that these nodes do indeed both form a cycle in the graph, and that this cycle has a weight of 0. This is how we would prove a correct solution in polynomial time.
- We now have to reduce an NP-complete problem to this problem
	- Subset sum: For a subset $\{1, 2, 3, 4\}$, convert it to a graph as such (slashes on edges mean multiple edges, each with a unique weight): ![[Pasted image 20240428170656.png]]
	- Each graph has up to $n$ nodes and $(\frac{n}{2})^2$ edges. This makes it a polynomial conversion, and thus reduction.