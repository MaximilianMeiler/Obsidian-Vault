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
- **Goal**: Given an array of $n$ integers, find a contiguous subarray whose sub is maximum
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
	- 