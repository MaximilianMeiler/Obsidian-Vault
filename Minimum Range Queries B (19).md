Previous lecture: [[Minimum Range Queries A (18)]]


Cartesian Tree
- Binary tree derived from a sequence of numbers
- Root: minimal element of A\[1,n], located at an index i
	- Left child: cartesian tree for A\[1,i-1]
	- Right child: cartesian tree for A\[i+1,n]
	- Val: the index that the min-val occurs at
- Linear construction
	- Properties to maintain
		- The indexes must maintain a BST ordering (later vals on the right)
		- Smallest val on top, children are greater than parent
	- Start at i=0, create a node
		- This node always has to become the rightmost in the tree
		- However, you will have to adjust surrounding pointers since its value has to scale
			- Val less than root: create a new root
			- Val greater than root: bubble down to the right
	- Algorithm
		- Use a stack to store the indices of the rightmost nodes
		- Pop the stack until the stack top is greater than or equal to the new value (or empty)
			- Then, rewire tree
- Application
	- LCA - Lowest Common Ancestor
		- Used for RMQs on an indexes \[i,j]
			- BST search for an index between \[i,j] (inclusive), when one is found, it contains the min
		- LCA of U and V is the node of greatest depth that is the ancestor of both U and V
			- Recursively mark up tree after finding U and V
		- Properties
			- U is an ancestor of V iff LCA(U, V) = U
			- LCA(U, V) is on the simple path from U tot V
		- Tarjan's LCA
			- Maintain "ancestors" array
			- DFS thru the tree
				- For a node, set its ancestor to itself
				- When all children of a node are explored, set its ancestor to its parent
				- WHEN both nodes in a pair are found, the ancestor of the earlier-found one is the LCA
			- Union-Find?
		- Euler tour
			- Traverses each edge of a tree once
			- A, B, C are pointers in each node
				- A points to left node's A, or current node's B if no left child
				- B points to right node's A, or current node's C if no right child
				- C points to previous node's B (if curr is left child), or previous node's C if (curr is right child)
			- ![[slide8-l-3504734009.jpg]]
			- Taking the tour gives us the "dfs sequence"
				- You can also take the level/height at every point in this sequence
					- tour/level relation: Increasing, +1 / Decreasing, -1
				- You can also take the first appearance (i) of each number in the tour
					- LCS of U and V -> the RMQ between firstApp\[U], firstApp\[V]
					- Thus, LCS uses this time ->> >O(1) query, O(nlogn) preprocess (sparse table)
						- Hybridization

Hybrid strategies for RMQs
- Remember the block based approach?
	- If we have high input size, we can recursively block our blocks!
	- 