Previous lecture: [[Turing Machines (AAD-12)]]


**P**
	- Say we have a language $X$, and one string $s$ from it
	- Say we have a machine $A$ that recognizes $X$
- $A$ will terminate in at most $p(|s|)$ steps, where $p$ is a polynomial function
- $P$ is the set of decision problems for which a poly-time algo exists

**NP**
- Set of decision problems for which an algorithm can be proven to have output correctly in polynomial time
	- There exists a **certifier** where for every string $s$, there exists a **certificate** string $t$ (answer) where $C(s, t) = \text{yes}$
- Hamiltonian path
	- Given an undirected graph, does there exist a simple path that visits every node?
	- $s$ = the graph, $t$ (certificate) = the sequence of nodes
	- Certifier: Check that $t$ contains each node in the graph exactly once, and that the graph contains an edge between adjacent nodes
- SAT
	- Given a bool formula, does it have a consistent truthful output?
	- 3-SAT: where each sub-clause has exactly 3 literals
	- Certificate: an assignment of boolean values
	- Conjecture: No poly-time algorithm for 3-SAT

**EXP**: problems for which there exists an exponential-time algorithm
- P $\subseteq$ NP
- NP $\subseteq$ EXP
	- Run all possible certificates into the certifier,  see if any work
	- Ex. Hamiltonian path of $V$ nodes -> $Vlog(V)$ binary string of path -> $2^{Vlog(V)}$ total operations

Reduction
- Problem $X$ **reduces** to problem $Y$ if arbitrary instances of problem $X$ can be solved using:
	- Polynomial number of calls to an algorithm that solves problem $Y$
	- Polynomial number of separate calculations
	- $X \leq_{p} Y$ - if one can be solved in polynomial time, the other can too.
		- If $X \leq_{p} Y$ and $Y \leq_{p} X$, then $X \equiv Y$ 
- Independent set $\equiv_p$ Vertex cover
	- Independent set: Is there a subset of $k+$ vertices in a graph where no 2 are adjacent?
	- Vertex cover: Is there a subset of $k-$ vertices where each edge is incident to at least 1 vertex in the subset?
	- **Proof**: We show $S$ is an independent set of size $k$ if $V-S$ is a vertex cover of size $n-k$
		- Let $S$ be any independent set of size $k$ (IS $\leq_{p}$ VC)
		- Show that all edges have at least 1 endpoint in $V-S$
			- Since $S$ is independent, each edge has one end in  $S$ and one in $V-S$ (or both in $V-S$)
		- Let $V-S$ be any vertex cover of size $n-k$ (VC $\leq_{p}$ IS)
			- Every edge must have at least 1 endpoint in $V-S$, meaning no edge has both ends in $S$. Thus, $S$ is also an independent set
- Set cover: Given a collection of subsets $S$ of elements $U$, are there $k-$ of these subsets whose union is equal to $U$?
	- Vertex cover $\leq_p$ Set cover
		- Say you're given a graph with edges $E$
		- $U$ = $E$
		- $S$ = all the nodes -> sets containing all edges adj to those nodes
		- $k$ is the same
	- ~~Set cover $\leq_p$ Vertex cover~~
		- ~~Make a graph where each set is a node, and edges connect all sets with a shared element~~
- 3-SAT $\leq_p$ Independent set![[Pasted image 20240418121827.png]]
	- $G$ contains 3 nodes for each clause, one node per each literal
	- Connect all literals in one clause together
		- You can never select 2 nodes from the same clause
	- Connect each literal to its negation
		- You can never select 2 nodes that contradict themselves
	- The equation is satisfiable iff $G$ contains an independent set of size $k$, equal to the number of clauses
		- One literal from each clause must be selected!
- If $X \leq_{p} Y$ and $Y \leq_{p}Z$, then $X \leq_{p} Z$

NP-complete
- A problem is NP-complete if every other NP problem can be reduced to it.
- If an NP-complete problem is shown to be in P, P=NP
- To prove that a problem is NP-complete, just reduce a np-complete problem to that problem

$\text{|}$ 