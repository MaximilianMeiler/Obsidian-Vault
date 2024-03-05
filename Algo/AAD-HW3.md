## Chapter 4
### Problem 1
The statement is **true**.
Say there exists an MST without the edge included.
Including the edge would form a cycle.
Here, we could remove the lowest-cost edge in this cycle and still maintain a spanning tree.
This swaps out a higher-cost edge for $e*$, meaning this new tree is more optimal and thus contradicts our original assumption.

### Problem 8
Any deviation from the "true" tree presents a problem as in the exercise above, where we would be forced to swap from the best edge to one of greater weight.

### Problem 9
Not every min-bottleneck tree is an mst. ![[Pasted image 20240301105128.png]]
Here, the double-5-edged tree would be a min-bottleneck tree, but not an mst.

Every mst is a min bottleneck tree. 
We know from problem 8 that a tree with distinct edge costs leads to a distinct mst.
Kruskal's algorithm takes lowest-cost edges first until a spanning tree is formed, creating an mst but also inherently a mbst.

### Problem 11
Intuitively, we can just reorder the sequence in which same-weight edges are fed into Kruskal's to alter the final tree (essentially give "preference" to which edges are doomed to form loops when executing).
Perhaps you can prove this through induction on # of edges? Let's try:
With no edges or just 1, Kruskal's obviously finds all MSTs.
So, let's assume that Kruskal's can find all MSTs on a graph of $m-1$ edges.
What happens when the $m$th edge is added?
- It may connect a new node 
	- Kruskal's will select the unique edge, hypothesis still holds
- It may connect previously connected nodes 
	- This new edge will be in all MSTs iff it is weighted less than the next biggest edge in its fundamental cycle. 
		- Kruskal's will kick out the largest edge upon execution, including the new one instead if possible, hypothesis still holds
	- The edge will be in *some* MSTs iff it is weighted the *same* as the next biggest edge in its fundamental cycle.
		- Kruskal's can be configured to choose this edge instead of what it previously chose (different valid execution sequence), which would expand the possible MSTs it outputs, hypothesis still holds
Thus, it *seems* to be true in all possible cases.

## Chapter 5
### Problem 2
Very similar to the initial inversion algorithm.
Inherently, we want to split the list in two, count the number of inversions on each side, then the amount between each list (sum is answer)
- If we can find the amount between, number of inversions on each side is trivial through a recursive "divide-and-conquer" approach
Counting significant inversions between two lists
- Start by sorting each list ($O(nlogn)$)
- Take the first element in left list, iterate through right to see what elements it conflicts with.
	- Each element to the right of the first element in the left list will also conflict with the 
- Move forward one index at a time in left, iterating through right to find conflicts
This is $O(nlogn)$. Why? Because the normal inversion algorithm is $O(nlogn)$ >:(

### Problem 3
Assume that you have an array split into two.
In each half, you know *if* there exists an equivalent group of size greater than (n/2)/2.
- If neither half exhibits this, the total array cannot. We are finished.
- For every half that exhibits this, check this majority ID with every element in the other array, checking if it makes a total majority (note - it's easy to keep track of this ID since each half can only possibly have 1 majority)
How do we determine if each half has a group greater than size n/2
- Run the algorithm recursively on each half!
- Base case - if each half has 1 element, that element automatically holds a majority
Time complexity is nlogn
- We split the array in half until groups of one are reached - this takes logn iterations
- To merge two halves, we check each possible majority with every element in the other array - this is (n/2) + (n/2) in the worst case (and could probably be optimized during coding too)
