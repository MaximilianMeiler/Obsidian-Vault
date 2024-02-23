Previous lecture: [[Greedy Algorithms (AAD-7)]]


Divide-and-conquer definition
- Divide a problem into subproblems
- Solve subproblems recursively
- Combine subproblem solution into overall solution

Merge sort
- Merging two sorted lists
	- Iterate through, adding least element of either list at a time
	- $O(n)$ complexity
- **Proposition**: Mergesort sorts any list of n elements *\[Proof by Strong Induction]*
	- Base case: $n = 1$
	- Induct hypothesis: assume true for $1 ... n-1$
	- By inductive hypothesis, mergesort sorts both left and right halves
- Finding time complexity
	- Finding number of comparisons $T(n)$
		- $T(n) = T(\frac{n}{2})+ T(\frac{n}{2})+ n$ 
	- **Proposition**: the complexity of this is $nlogn$ *\[by Induction on $n$]*
		- Base case: when $n=1$, $T(1) = 0 = nlogn$
		- Inductive hypothesis: Assume $T(n) = nlogn$
		- Show $T(2n) = 2nlog(2n)$
			- $T(2n) = 2nlogn + 2n = 2n(log(2n) -1) + 2n = 2n(log(2n))$ 
				- Note: $log(2n) = log(2) + log(n)$
		- This works if $n$ is a power of 2
			- Through log properties, this evaluates to $n\lceil(log(n)\rceil)$  
- Digression: How to we prove a lower bound for all (comparison) sorting algorithms?
	- Comparison trees: assume you can access elements through pairwise computations
	- ![[th-3364477348 3.jpeg]]
		- Height of tree = worst-case number of compares
	- **Theorem**: all comparison-based sorting algorithms must make $\Omega (n(logn))$ comparisons in the worst case
		- Binary tree of height $h$ has $\leq 2^h$ leaves
		- $n!$ different orderings $\Rightarrow n!$ reachable leaves
		- $h \geq log(n!) \geq nlogn - \frac{n}{ln(2)}$ 
			- Thus, we have to make over $nlogn$ comparisons in the worst case!

Linked list shuffling
- Just run merge sort, splitting bit by bit
- How do we merge 2 shuffled lists randomly?
	- Choose from either list with probability proportional to size remaining
		-  n1 / (n1 + n2)

Counting inversions
- **Inversion**: Indices $i$ and $j$ are inverted if $i < j$, but $a_{i}> a_j$ 
- Brute force algorithm: Check all $n^{2}$ pairs
- Divide-and-conquer algorithm
	- Split the list in two
	- Add up the number of inversions on the left, number on the right, and number when merging
- How to count number inversions between two array "halves"?
	- Start by sorting A and B
	- ![[Pasted image 20240220112304.png]]
		- 3 is an inversion with 2, thus everything else also forms and inversion
		- Use binary search for each element in B to find "insertion position", then keep looking ahead for other elements

Quicksort
- Given an array A and pivot P, partition so that:
	- Elements smaller than p end up in the left subarray L
	- Elements larger than p end up in the right subarray R
	- Elements equal to p end up in the middle subarray M
- Randomized quicksort
	- Pick a pivot at random
	- Partition the array accordingly
	- Recursively sort the left and right subarrays
	- Expected runtime: $O(nlogn)$, worst runtime: $O(n^2)$
- **Proposition**: Quicksort sorts any array of $n$ elements *\[Proof by Induction]
	- Base case: $n = 1$ (already sorted)
	- Assume qs sorts a list of size $n-1$, show it can do $n$
	- Choose a pivot, reorient accordingly
		- The pivot will always be in the correct final position
		- Inductive hypothesis means L and R can get sorted correctly
	- Thus, the whole list is sorted
		- All vals less than p are sorted on its left, all vals greater than p are sorted on its right!
- **Proposition**: The expected number of compares to quicksort an array of $n$ elements is $O(nlogn)$
	- **Proof**: consider BST representation of pivot elements
	- $a_i$ and $a_j$ are compared once iff one is an ancestor of the other
		- If a pivot between 2 elements is chosen, those two elements will not be compared with one another
		- Note - given sorted elements $a_1...a_n$, what is the probability that:
			- $a_n$ and $a_{n-1}$ are compared: 1
				- There is no pivot to divide the two from being compared
			- $a_1$ and $a_n$ are compared: $\frac{2}{n}$
				- The only way for this to happen is for either of them to be chosen as a pivot before they are "split" by a different pivot
	- Probability that $a_i$ and $a_j$ are compared = $\frac{2}{{j-i+1}}$ where $i < j$
	- Expected total number of comparisons: $\sum_{i=1}^{n}\sum_{j=i+1}^{n}\frac{2}{j-i+1}$
		- Add up all probabilities of all element comparisons!
		- This summation is $O(nlogn)$
- Say you have a pile of $n$ nuts and $b$ bolts
	- Design an $O(nlogn)$ algorithm to fit them together
	- Take a bolt as a pivot
	- Compare all nuts, pivot the nuts around the nut that fits that bolt
		- With that nut, then pivot the bolts!
	- Repeat on subarrays until completely sorted

Medians and selection
- **Selection**: Given $n$ elements from an ordered universe, find the $k^{th}$ smallest
	- Min: $k = 1$, Max: $k = n$
	- Median: $k = \lfloor{\frac{{n+1}}{2}}\rfloor$ 
		- Solvable in $O(nlogn)$ with sorting, or $O(nlogk)$ with max heap
- Randomized quickselect
	- Pick a random pivot $p$
	- Partition the array
	- Recur in *one* subarray - the one containing the $k^{th}$ smallest element!
		- Pivot is the $i^{th}$ smallest element - compare this to $k$!
	-  $T(n) \leq 4n$ (\# of compares) - $O(n)$
- Selection in linear time
	- **Goal**: pick a pivot $p$ that divides a list so that neither side has $> 7n/10$ elements
	- Finding ~median in linear time:
		- Recursively compute median of sample of $\leq 2n/10$ elements
		- Divide elements into $\lfloor \frac{n}{5}\rfloor$ groups of $5$ elements each
			- Find the median of each of those groups
		- Find the median of each of those medians - use that as a pivot
	- Analysis
		- At least half of the 5-elements medians will be less than $p$
		- At least $3\lfloor{\frac{n}{10}}\rfloor$ elements will be less than (or equal to?) $p$
		- (Same line of logic works for elements greater than $p$)
		- Thus, select is called recursively on at most $n - 3\lfloor{\frac{n}{10}}\rfloor$ elements!