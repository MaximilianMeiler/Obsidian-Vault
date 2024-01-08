Previous lecture: [[Trees A (20)]]


Fenwick trees (AKA Binary Indexed Tree)
- Efficient prefix sum updating+retrieval
- Integers are represented in binaries and 1-based
	- Odd numbers - just the value (xxx1)
	- Evens
		- Multiples of 2: store last 2 vals (xx10)
		- Multiples of 4: store last 4 vals (x100)
		- Multiples of 8: store last 8 vals (1000)
		- etc...
		- Check rightmost binary 1 to find this
	- To obtain: (`k & -k`)
		- -k: all bits of k inverted + 1
		- Tree at node k: `sum(k - p(k) + 1, k)` (using prefix sum)
- Querying
	- c(13) = c(1101) = tree(1101) + tree(1100) + tree(1000)	
		`while (k >= 1) { `<- repeat until all 1s are removed
			 `s += tree[k]
			 `k -= k & -k` <- this line removes the rightmost 1
		`}
- Updating
	- Push the update "up" the tree's sums
		- This code increases the "2-pow factor" of the input k:
		`while (k <= n) {
			`tree[k] += x
			`k += k & -k
		`}
	- This code can just be used for construction (nlogn)
- Working backwards
	- How do we infer the original array with the tree constructed?
		- arr(12) = tree(12) - tree(11) - tree(10)
			- tree(1100) - tree(0111)  - tree(0110)
- vs Seg tree
	- Requires O(n) memory, not O(2n)
	- Easier to use and code
	- O(nlogn) construction, not O(n)
- This works for problems where you can add/subtract subproblem values (???)

Tree diameter
- Longest path between 2 nodes in a tree
- Run BFS from an arbitrary node s to find the furthest node u
- Then, run BFS at u to find the furthest node v from that
- dist(u, v) is our diameter
- [['Patrol']]


Next lecture: [[Misc A (22)]]