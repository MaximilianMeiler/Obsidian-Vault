Previous lecture - [[Minimum Range Queries B (19)]]


Range queries with updates
- Naive
	- Precomputing sums - O(n^2)
	- Updating - O(n)
	- Querying - O(1)
- Segment trees!
	- A generalizable log(n) update + query structure
	- Structure
		- Leaf nodes - represent one element
		- Internal nodes - represent an interval \[i,j]
			- Root node - interval \[0,n-1] (ex. sum of all elements)
			- Left child: \[i, (i+j)/2]
			- Right child: \[(i+j)/2 + 1, j]
	- Updating
		- Change value of leaf node
		- Work upwards, changing the values of ancestors if needed
		- log(n) complexity
	- Storage
		- Stored in binary tree, similar to heap
			- Note: indices are 1-indexed
			- Parent: floor(k/2)
			- Children: 2k, 2k+1
	- Construction
		- Allocate 2n space
		- Place original elements in last half of space
		- Go back to front, updating parent elements
			- Will be a spare element if n is even, but not if n is odd (?)
	- Querying
		- Say you have a query for range \[a, b], and are at node \[l, r]
			- If \[l, r] is part of \[a, b], return value of current node
			- If not, recur then combine answer from children
				- m = (l + r) / 2
				- If \[l, m] has an overlap with \[a, b], recur to left child
				- If \[m+1, r] has an overlap with \[a, b], recur to right child
			- Note - never update \[a, b] when recurring (I don't know why you would)
		- But there's a better way!
			- Note - this uses 1-based indices
			- Say your range in the original array is \[10, 15]
				- Go to parents, new range - \[5, 7]
				- Keep going...?
			- 10 in binary - 1010, 15 in binary - 1111
				- 1: in a right subtree, 0 - in a left subtree
				- Move right pointer up if on right subtree (mod 2 = 1)
				- Move left pointer up if on left subtree (mod 2 = 0)
					- If you ever don't move up, that is the final val you *add* to ur *sum*
					- Terminate this iteration when r < l
	- Updating
		- Update p's node, update parents if needed
	- Lazy Propagation
		- What if we need to update all elements in an interval \[l,r]?
		- Store updates made to elements in a corresponding lazy array
			- This isn't immediately applied
			- Only change stuff that is queried
			- If a change is already stored at a val, just push it down the tree
				- When this is applied to a leaf, work upwards to change parent vals too 

Application
- Finding min/max on a range
	- And the number of times it appears!
- Computing GCD/LCM
- Search for first element greater than a given amount
- Find the kth instance of a value

Examples
- [['Range Sum Query - Mutable']]
- [['Interval Product']]


Next lecture: [[Trees B (21)]]