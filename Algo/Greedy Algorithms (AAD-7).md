Previous lecture: [[Graphs (AAD-6)]]


# Coin change
- Given denominations of US currency, devise a method to pay someone with the fewest number of coins
- Cashier's algorithm - take the largest denomination possible at each step
	- This only works for specific sets of coins
	- How do we know which ones these are?
- Properties of optimal solutions
	- Contain <5  pennies, <2 nickel, <4 quarters
	- Number of nickels + number of dimes < 3
		- <2 nickels means 3 coins will always be collapsed into at least 2 dimes
			- Adding a nickel here lets us turn it all into at least a quarter
- **Theorem**: Cashier's algorithm is optimal for US coins *\[Proof by Induction]*
	- Base case: 1 cent is given, a penny is used (obviously optimal)
	- For an amount $x$ we want to pay, where $c_{k} \leq x < c_{k+1}$ ,
		- We will take coin $c_k$ , claiming that every optimal solution must do the same
			- If this was not the case, x must be formed by coins $c_{1} ... c_{k-1}$ 
				- However, this will often violate our optimal properties listed above! (insert table when available)
		- Thus, we know this coin will always be taken
	- Assume we have the optimal solution for $x = i, i \geq 1$ (base case)
		- Make change for $i + 1$ coins: 
			- Choose the largest coin $\leq x$, which we've proven is optimal
			- Now, $x - c_{k}\leq i$, so we can prove that we've solved for the entire optimal solution using the Cashier's algorithm 
	- ![[Pasted image 20240201115216.png]]

# Interval scheduling
- A job $j$ starts at $s_j$ and ends at $f_j$
	- They are **compatible** if they do not overlap
- Goal: Find the max subset of mutually compatible jobs
- Greedy algorithm: sort jobs by finish time, keep taking the next available job
- **Theorem**: The early-finish time algorithm is optimal *\[Proof by contradiction]*
	- Assume the greedy algorithm is not optimal!
		- Let $i_{1} ... i_k$ be the jobs the greedy algorithm takes, and $j_{1} ... j_m$ be the job the "optimal" solution takes
		- Forget about all jobs they agree on, consider the first place they disagree on
			- Here, greedy takes $i_{r+1}$ , and "optimal" takes $j_{r+1}$
			- BUT, it's implied that the finishing time of the greedy job must be less or equal to the finishing time of the "optimal" job!
		- We could just repeatedly replace the "optimal"'s $j_{r+1}$ with the greedy's $i_{r+1}$ until they are completely the same (no contradictions will be created since the new job finishes earlier than the old job)
			- This ties the total jobs taken for both, creating a contradiction!

## Interval partitioning
- Lecture $j$ starts at $s_j$ and ends at $f_j$
- Goal: find the minimum number of classrooms to schedule all lectures provided
	- Note: no two lectures can happen in the same classroom at the same time
- Greedy algorithm: Sort lectures by start time and insert them wherever possible
	- $O(nlogn)$
- The **depth** of a set of intervals is the max number of intervals that contain any given point (overlap at once)
- **Observation**: The earliest-start algorithm never schedules two incompatible lectures in the same classroom
- **Theorem**: Earliest-start algorithm is optimal
	- Let $d$ =  number of classrooms the algorithm allocates
		- $d$ is opened because we needed to schedule a lecture $j$, which is incompatible w all other classrooms
	- Thus, all $d$ lectures end after $s_j$
		- Additionally, none of the $d-1$ lectures start after $s_j$
	- Thus, $d$ lectures overlap at $s_{j}+ \epsilon$ , and all schedules use $\geq d$ rooms

## Minimizing lateness
- Job $j$ requires $t_j$ unites of processing time and is due at time $d_j$
	- $j$ finishes processing at time $s_{j} + t_{j}$ if it is started at $s_j$
- Lateness = $max\{0, f_{j}- d_j\}$ 
- Goal: schedule all deadlines to minimize deadlines
- Greedy algorithm: Sort lectures by due time, do the earliest due lecture first

# Weighted shortest path
- **Problem**: Given a digraph $G = (V, E)$, edge lengths, a source and destination $s, t \in V$, find the shortest-weighted path from $s$ to $t$ in $G$
	- What about a shortest path from $s$ to every node in $G$?
- **Greedy approach:** Maintain a set $S$ of nodes for which we know the shortest path to for
	- $s$ starts with length 0
	- We repeatedly take the shortest edge out of this set (plus the distance to the node it originates from) until all nodes are found
- Implementation
	- Consider vertices in increasing order of distance from $s$
	- Add that vertex to the tree, relax all edges pointing from that vertex
- **Proof** *\[By induction on |S|]
	- **Invariant**: For each node in $S$, $d[u]$ stores the shortest path from $s$ to $u$
	- **Base case**: $|S| = 1$ is easy, as $d[s] = 0$
	- **Inductive hypothesis**: Assume true when $|s|  \leq k$ for $k \geq 1$  
	- Let $v$ be added next to $S$ with edge $(u, v)$
		- Consider any other $(s, v)$ path $P$, we show it is no shorter than $\pi(v)$
			- In this path, consider the last node in $S$ in the path $x$, and $y$ the first node in the path that is not in $S$
				- The edge from $x$ to $y$ is edge $e$
				- The path from $s$ to $x$ is $P'$
			- Note: $y \neq v$ 
		- Claim: The length of $P$ is already $\geq \pi(v)$ as soon as it reaches $y$
		- Length of $P'$ is the shortest path to $x$
		- The algorithm selected $v$ instead of $y$ for the edge coming out of $S$. Thus,
		- $l(P) \geq l(P') + l(e) \geq d[x] + l(e) \geq \pi(y) \geq \pi(v)$  
- Optimization 1: For each node, store $\pi(v)$ 

# Minimum spanning trees
- A **cut** is a partition of nodes into two nonempty subsets $S$ and $V-S$
- The **cutset** of a cut $S$ are the set of edges with exactly one endpoint in $S$
	- Removing the cutset would split the graph into multiple connected components
	- **Proposition**: a cycle and cutset intersect on an even number of edges
- **Spanning tree**: $H$ is a subgraph of $G$ that contains all vertices, but not always all edges. H is a spanning tree if it is both acyclic and connected.
	- Will always have $V-1$ edges, etc
- **Minimum spanning tree**: Given a weighted graph, an MST is the spanning tree with the lowest possible sum of edge weights
- **Fundamental cycle**: Adding an edge to an MST makes 1 cycle
	- This means that we can "swap out" edges of higher weight to make an MST
- **Fundamental cutset**: 
	- For a spanning tree, removing one edge will create 2 connected components
	- For any other edge in that cutset, we can "swap out" the previous edge for it
- **Greedy algorithm**; Apply red and blue rules until all edges are color. When $V-1$ edges are blue, they are the MST
	- Red rule: Let $C$ be a cycle with no red edges. Select the uncolored edge of max cost and color it red.
	- Blue rule: Let $D$ be a cutset with no blue edges. Select the uncolored edge of min cost and color it blue.
- Color invariance - There exists an MST containing every blue edge and no red edge *\[Proof by Induction]*
	- Base case: no edges colored, every MST satisfies invariance
	- Induction step: Suppose color invariance is true before blue rule
		- Let $D$ be the chosen cutset, and let $f$ be the edge colored blue
			- If $f$ is in the tree, the inductive hypothesis still holds
			- If $f$ is not in the tree, it can be swapped out through the fundamental cycle (created when $f$ is added) with an uncolored edge $e$ (Why?) that has a greater cost
				- It's in the tree, so it can't be a red edge
				- It was in a blue rule cutset, so it can't be a blue edge
			- Thus, the old tree with $e$ replaced by $f$ satisfies the invariant
	- Induction step: Suppose color invariance is true before red rule
		- Let C be a chosen cycle (thus, containing no red edges), let $e$ be the edge colored red
		- If $e$  is not in the tree, we're done
		- If it is, remove it from the tree. Swap this edge with another edge $f$ that is also in the cycle
		- Claim: $f$ is uncolored
			- It's not in the tree, so it can't be clue
			- It's in the cycle $C$, so it's not red either
		- Claim: $f$'s cost is less than that of $e$ (red rule chose $f$ over it)
		- Thus, swapping $e$ with $f$ satisfies the invariant
			- We can always do this since $f$ is never in the tree (this would make a cycle)
- Theorem: The greedy algorithm terminates, and blue edges form an MST
	- Proof: Show that, if an uncolored edge exists, we can apply either the red or blue rules
		- Observation: The blue edges form a forest
			- Case 1: both endpoints of $e$ are in the same blue tree
				- Apply red rule to cycle formed by adding $e$ to this tree
			- Case 2: both end points of $e$ are in different blue trees
				- Apply blue rule to cutset induced by either blue tree
			- Case 3: there are no blue edges in the graph - $e$'s endpoints are both uncolored
				- We can apply the blue rule (e's edges would not be in different trees if there was a blue edge in the cutset)
			- Notice: If there is a blue forest, we can always find an edge adjacent to at least one node in the forest that is uncolored
				- They can't be all red (an MST has to be able to cross between forests), so one must be uncolored 
- **Prim's algorithm**
	- Walkthrough
		- Repeat n-1 times: Add to MST a min-cost edge with only one endpoint in S, and add the other endpoint to S.
	- This is just applying the blue rule over and over!
	- Can be implemented in $O(mlogn)$ time
- **Kruskal's algorithm**
	- Walkthrough
		- Consider edges in ascending cost, add lowest to tree unless it forms a cycle
	- Ruleset
		- If both endpoints are in the same blue tree, color the edge red (red rule)
		- If both endpoints are in different trees, color the edge blue (blue rule)


Next lecture: [[Divide and Conquer (AAD-8)]]