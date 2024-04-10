Previous lecture: [[Divide and Conquer (AAD-8)]]


## Overview
- Divide-and-conquer: Breaking up a problem into independent subproblems
- Dynamic programming: Breaking up a problem into overlapping subproblems, combining solutions

## Weighted interval scheduling
- Job $j$ starts at $s_j$, ends at $f_j$, and has weight $w_{j}> 0$
- We want to find the max-weight subset of non-overlapping jobs
- Say we have the jobs in ascending order of finish time
- **Def**: $p(j)$: largest index $i < j$ such that $i$ is compatible with $j$
	- Latest finish time that does not overlap with $j$
- **Def**: $OPT(j)$ = max weight of any subset of mutually compatible jobs for the subproblem consisting of jobs $1 ... j$ 
	- Case 1: $OPT(j)$ selects job $j$ -  $= w_{j}+ OPT(p(j))$
	- Case 2: $OPT(j)$ does not select job j - $= OPT(j-1)$ 
- ![[Pasted image 20240227113218.png]]
- $p(j)$ can be computed using binary search
- Top-down dynamic programming (memoization)
	- Notice that the program is very slow because the same subproblems are being calculated over and over again
	- When you calculate subproblem $j$, cache it in $M(j)$ and use it to avoid re-solving the same subproblem again
- **Claim**: Memoized version takes $O(nlogn)$ time
	- Sort by finish time - $O(nlogn)$ via mergesort
	- Compute $p[j]$ for each $j$ - $O(nlogn)$ via binary search
	- Computation takes $O(n)$ time - all values $1 ... n$ are only calculated once!
- How do we find the set from the optimal weight?
	- For an interval, check if the optimal solution contains it by seeing  if $w_{j}+ M(p(j))$ is greater than $M(j-1)$ (if so, take, otherwise, skip)
- Bottom-up dynamic programming (tabulation)
	- Move up through $M$
	- `M[j] = max(M(j-1), w[j] + M[p[j]])`

## Maximum Contiguous Subarray
- **Goal**: Given an array of $n$ integers, find a contiguous subarray whose sum is maximum
- Brute force: Try every pair of indices, add all values between each pair - $O(n^3)$
- Precompute cumulative sums, take difference of prefixes to find sum of subarray (`S[j] - S[i-1]`)
	- Improves runtime to $O(n^2)$
- **Kadane's algorithm**: 
	- **Def**: $OPT(i) =$ max sum of any subarray whose rightmost index is $i$
	- **Goal**: Max $OPT(i)$ over all $i$
	- ![[Pasted image 20240229115001.png]]
	- $O(n)$ runtime

## Knapsack problem
- **Goal**: Pack knapsack to maximize total value of items taken
	- $n$ items, each with a weight $w_i$ and value $v_i$
	- Knapsack has weight limit $W$
- **Def**: $OPT(i, w)$: optimal value of knapsack problem with items $1 ... i$ available and subject to weight limit $w$
- We either select an item and account for it's weight and value, or skip it: ![[Pasted image 20240229120228.png]]
- Retracing the actual item subset
	- ![[Pasted image 20240229121414.png]]
	- Check which of  $(i-1, w)$ and $(i-1, w-w_{i}) + v_i$ are equal to $(i, w)$
		- Former - item $i$ skipped, latter - item $i$ taken
- **Theorem**: The DP algorithm solves the knapsack problem in $\Theta(nW)$ time and $\Theta(nW)$ time

## Coin Change

## Sequence Alignment
- **Problem**: Solve for how similar two strings are
	- Gap penalty $\delta$, mismatch penalty $\alpha_{pq}$ (for letters $p$ and $q$)
- **Goal**: Given two strings, find a min-cost alignment
	- **Def**: An **alignment** $M$ constitutes the pair of indices that are matched up
		- Note - anything that isn't in a pair creates a gap
		- ![[Pasted image 20240229123059.png]]
- **Def**: $OPT(i, j)$: Min cost of aligning prefix strings $x_{1 ... i}$ and $y_{1 ... j}$
	- Case 1: Merge next letters
	- Case 2: Create a gap in j with the next letter in i
	- Case 3: Create a gap in i with the next letter in j
	- ![[Pasted image 20240305105910.png]]
- Traceback:
	- Start in the bottom-right corner of the table ($OPT(n,m)$)
	- Check the 3 surrounding cells corresponding to matches and gaps
	- Take the min of all 3 operations when simulated, see what matches up
	- $O(m+n)$

## Longest Common Subsequence
- Given two strings $x$ and $y$, find the common subsequence that is as long as possible (non-contiguous)
- **Def**: $OPT(i, j) =$ length of LCS for prefix strings $x_{1 ... i}$ and $y_{1 ... j}$
	- Case 1 - $x_{i} = y_{j}$: $OPT(i, j) = 1 + OPT(i-1, j-1)$
	- Case 2 - $x_{i} \neq y_j$: $OPT(i, j) = max(OPT(i-1, j), OPT(i, j-1))$
	- Base cases: return 0 if $i = 0$ or $j = 0$
- OR, reduce to finding a min-cost alignment of $x$ and $y$ with gap penalty $\delta = 1$ and mismatch penalty $\alpha = \infty$ 

## Bellman-Ford-Moore
- Shortest-path solver when edge lengths are negative
	- Negative cycles between source $s$ and destination $t$ mean there is no shortest path between the two
- Without negative cycles, the shortest path is simple 
- **Proof**
	- Among all shortest $v\rightarrow t$ paths, consider the one that uses the fewest edges
	- If that P contains a directed cycle W, we can remove W from P without increasing P's length
- Single-destination shortest path problem: Find the shortest path from every node in the graph to a destination node $t$ (edges can be neg, no cycles)
- Negative-cycle problem: Given a digraph, find if a negative cycle exists
- **Def**: $OPT(i, v)$ = length of shortest $v \rightarrow t$ path using $\leq i$ edges
- **Goal**: $OPT(n-1, v)$ for each $v$
	- Case 1: Shortest $v \rightarrow t$ path uses $\leq i-1$ edges
		- $OPT(i, v) = OPT(i-1, v)$
	- Case 2: Shortest $v \rightarrow t$ path uses exactly $i$ edges
		- $OPT(i, v) = min_{w = neighbors[n]}(l_{v,w} + OPT(i-1, w))$
	- Base cases: If $i = 0$: {If $v = t$, return 0. If not, return $\infty$}
- **Theorem**: This algorithm works in $\Theta(mn)$ time and $\Theta(n^2)$ space
- Traceback: Maintain a successor array / predecessor array
- Space optimization: Keep 2 1d arrays
	- d\[v] - length of shortest path we've found so far
	- successor\[v] - next node on a $v \rightarrow t$ path
- Performance optimization: On iteration $i$, ignore nodes $w$ that were not updated in iteration $i-1$
- Lemma 3: For each node $v$, $d[v]$ is the length of some $v \rightarrow t$ path
	- Lemma 4: $d[v]$ is monotone non-decreasing
- Lemma 5: After pass $i$, $d[v] \leq$ length of a shortest $v \rightarrow t$ path using $\leq i$ edges
- **Proof** *\[by induction on i]*
	- Base case: $i = 0$
	- Assume true after pass $i$
	- Let $P$ be any $v \rightarrow t$ path with $\leq i+1$ edges
	- Let $(v, w)$ be the first edge in $P$, and $P'$ the subpath from $w$ to $t$
		- At the end of pass $i$, $d[w] \leq l(P')$
	- $d[v] \leq l_{vw} + d[w] \leq l_{vw} + l(P') = l(P)$
- NOTE - THIS ALGO IS DUMB - RELAXES ALL EDGES N TIMES
- Lemma 6: Any directed cycle $W$ is a negative cycle
	- Positive cycles just won't be taken as an update (larger cost)
- **Theorem 3**: Assuming no negative cycles, BFM runs in $O(nm)$ time and $\Theta(n)$ space

#### Negative cycles
- **Lemma 7**: If $OPT(n, v) = OPT(n-1, v)$ for all nodes, then there are no negative cycles
	- Then values have converged, and a shortest $v \rightarrow t$ path exists
- **Lemma 8: ** If $OPT(n, v) < OPT(n-1, v)$** for some node $v$, then any shortest $v \rightarrow t$ path contains a negative cycle $W$
	- **Proof** *\[by contradiction]*
		- We know that the shortest path must have exactly $n$ edges over $n-1$
		- However, this means $n+1$ nodes are along that path, meaning a node is repeated. This forms a (negative) cycle.
- **Theorem 4:** We can find a negative cycle in $\Theta(mn)$ time and $\Theta(n^2)$
	- Add a sink node $t$, connect all nodes to it with a 0-length edge
	- Run Bellman-Ford for $n+1$ passes instead of $n-1$
		- If no $d[v]$ values are updated in pass $n+1$, then there are no negative cycles
	- We can find the cycle by making $t$ our destination, then we can trace back from it to find the repeated node


Next lecture: [[Network Flow (AAD-10)]]