Previous lecture: [[Graphs (AAD-6)]]


Coin change
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

Interval scheduling
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

Interval partitioning
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

Minimizing lateness
- Job $j$ requires $t_j$ unites of processing time and is due at time $d_j$
	- $j$ finishes processing at time $s_{j} + t_{j}$ if it is started at $s_j$
- Lateness = $max\{0, f_{j}- d_j\}$ 
- Goal: schedule all deadlines to minimize deadlines
- Greedy algorithm: Sort lectures by due time, do the earliest due lecture first

Weighted shortest path
- **Problem**: Given a digraph $G = (V, E)$, edge lengths, a source and destination $s, t \in V$, find the shortest-weighted path from $s$ to $t$ in $G$
	- What about a shortest path from $s$ to every node in $G$?
- **Greedy approach:** Maintain a set $S$ of nodes for which we know the shortest path to for
	- $s$ starts with length 0
	- We repeatedly take the shortest edge out of this set (plus the distance to the node it originates from) until all nodes are found
- Implementation
	- Consider vertices in increasing order of distance from $s$
	- Add that vertex to the tree, relax all edges pointing from that vertex
- **Proof** *\[By induction on |S|]*
	- **Inductive hypothesis**: Assume true when $|s|  = k$ for $k \geq 1$  
	- Let $v$ be  added next to $S$ with edge $(u, v)$
		- Consider any other $(s, v)$ path $P$, we show it is no shorter than $\pi(v)$
		- 