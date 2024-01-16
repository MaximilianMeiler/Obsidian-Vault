Previous lecture: [[Summary of Topics (AAD-2)]]


Undirected Graphs
- *G = (V, E)
	- *V* = vertices/nodes
	- *E* = edges
	- n = |*V*|, m = |*E*|
- A **path** is a sequence of nodes, where each consecutive pair is joined by an edge
	- A path is **simple** if all nodes are distinct
	- A **cycle** is a path that begins and ends at the same vertex
		- A cycle is **simple** if all nodes are distinct
- A **tree** is an undirected graph that is connected and does not contain a cycle
- Theorem - Let *G* be an undirected graph of *n* nodes: Any two of these imply the third:
	- *G* is connected
	- *G* does not contain a cycle
	- *G* has n-1 edges

Logical Statements
- **Logical statements**:  abstract statements into logical "variables"
	- *p: G* is connected
	- *q: G* does not contain a cycle
	- *r: G* has *n*-1 edges
- **Proposition** - (*p ^ q => r*): If *G* is a connected graph w/o cycles, then *G* has *n*-1 edges
- **Contrapositive** - (*~r => ~p v ~q*): If *G* does not have *n*-1 edges, then *G* is either not connected or does not contain a cycle (logically equivalent to our original proposition!)
- **Converse** - *(r => p ^ q)*: If *G* has *n*-1 edges, then *G* is connected and does not contain a cycle (this is not logically equivalent to our original proposition and does not tell us anything)

Direct proof
- Proposition - (*p ^ q => r*): If *G* is a graph that is connected and does not contain a cycle, then G has n-1 edges
- Direct proof - given that *p* and *q* are true, prove that *r* is true
	- **Lemma** - smaller building blocks of proofs
	- Lemma 1 - *G* has at least *n*-1 edges
		- Split *G* into a group of edges X and Y
		- *G* being connected implies that an edge must connect two nodes between X and Y
			- Start with X1, containing a single vertex *u*
			- Take the node *v* that X1 contains to into the new X2
			- Keep adding these edges until *n*-1 new nodes/edges are included
	- Lemma 2 - G has at most *n*-1 edges
		- Proof by contrapositive: Prove *~s => ~p v ~q*
			- Assume that *G* has more than *n*-1 edges
			- If G is disconnected, we are done
			- Otherwise, *G* contains a subgraph *T* that is a tree, and whose vertex set is *V*
				- *T* has *n*-1 edges
			- Since *G* has more than *n*-1 edges, there exists an edge in *E* that is not in *T*
			- This new edge forms a cycle
	- Proof - the claim follows from lemmas 1 and 2

Inductive proof
- Proposition - (*p ^ q => r*): If *G* is a graph that is connected and does not contain a cycle, then G has n-1 edges
- We will perform strong induction on *n* = |*V*|
- Base case: smallest value for *n* such that *G* satisfies *p* and *q* (*n* = 1)
- Inductive Hypothesis: Assume the claim is true when *n* <= *k*, for any *k* >= 1
- Inductive step: prove the claim when *n* = *k*+1
	- Remove an edge from the graph
	- Since the graph is connected w/o cycles, this splits it into 2 subgraphs *G1* and *G2*
		- *G1* has *j* vertices
		- *G2* has *n-j* vertices
		- Both subgraphs are able to assume the inductive hypothesis
			- *G1* and *G2* are both connected, as *G* was connected
			- *G1* and *G2* don't have cycles, as *G* had no cycles
	- *G1* has *j*-1 edges, *G2* has *n-j*-1 edges
		- Add up the edges and the one we removed: G has *j*-1+*n-j*-1+1 = n-1 edges

Proof by contradiction
- How to prove *p* => *q* through contradiction:
	- Assume *p* and *~q* are true
	- Argues this implies some proposition of the form *r ^ ~r*
		- This implies that *q* must instead be true
- Proposition: Any graph $G = (V, E)$ with $|V| \geq 2$
- Proof
	- Assume $|V| \geq 2$, but no two of its vertices have the same degree
	- Let $n = |V|$ and let $deg(u)$ be the degree of any vertex in $V$
		- Observe $0 \leq deg(u) \leq n-1$
	- Since there are only n vertices and n possible degrees, this implies one vertex exists with  degree 0, and one exists with degree $n-1$
		- This a contradiction! The latter node can't connect to every other node in the graph if one of the nodes is not connected to any other nodes in the graph!





Lemma 1
Assume G is connected, and does not contain a cycle
- Additionally, assume that every vertex of G has a degree of at least 2
- This means that each vertex is connected to at least 2 other vertices
- Assume we construct a graph, adding nodes one-by-one. Every time a vertex is added, it starts connected to where it is attached (degree one). To get a degree of two, it cannot attach to another previous node (as the graph being built is connected, and this would form a cycle using the vertex's two edges), and thus instead must connect to another node attached later.
- The *n*th node attached, however, must attach to two previous nodes (as there are no other proceeding nodes to attach to it), which is guaranteed to form a cycle.
	- Note that in a graph with node of *exclusively* degree 2, this would be forced to connect with the initial node (as the initial node has nothing to connect too and thus never formed it's second degree), but a cycle is guaranteed to form regardless of specifics.
- Thus, a graph where all vertices have a degree of at least 2 is bound to either be unconnected or contain a cycle.
By the contrapositive, we can prove that if G is connected and does not contain a cycle, some vertex of G has degree one (for n >= 2)

Proposition 1
Assume G is connected and does not contain a cycle
- By Lemma 1, we know that it contains (at least) 1 vertex of degree 1 (which is only connected to the rest of G through 1 edge)
- If that edge is removed, we are left with a graph of n-1 nodes, and e-1 edges (e = original # of edges)
- This remaining graph is still connected and does not contain a cycle
- Therefore, we repeat until we have removed n-1 nodes, and e-n+1 edges
	- Here, 1 node remains. As there are no cycles, there are no self-loops, and thus 0 edges remain in the graph
- Gence, e-n+1 = 0, or e (original # of edges) = n-1
Therefore, if G is connected and does not contain a cycle, then G has n-1 edges


Next lecture: [[Algorithm Analysis (AAD-4)]]