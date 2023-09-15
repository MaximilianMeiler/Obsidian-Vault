Previous lecture: [[Lists, Stacks, Queues (3)]]

A graph with...
- One root
- One parent per node
- No cycles

Uses
- Decision Trees
- File systems
- Search trees

Terminology
- Root - node at the top
- Parent/Children
	- Siblings - all children with the same parent
- Nodes
	- Leaves - nodes with no children
- Subtree: take a guess
- Depth - the distance of a node from the root (root = 0)
- Height (0 based) - nodes in the longest path from root to a leaf
	- Height (1 based) - root is now counted as a node

Tree Types
- N-Ary tree
	- Each node consists of at most n children
	- Full binary tree
		- Each node has either 0 children or 2 children
		- Perfect Binary Tree
			- Has exactly 2^(h+1) + 1 nodes
			- Completely full on every level
			- Height: log(n + 1) - 1
	- Complete binary tree
		- Perfect on all levels through h-1
		- All leaves skew left on level h
		- Height: ciel(log(n + 1) - 1)
	- Binary Search Tree (BST) / Ordered binary tree
		- All values of a node's left subtree are less than the node's value
		- All values of a nodes' right subtree are greater than the node's value

Representing Trees
- Array Representation
	- Stores values of everything in one depth, then moves to the next size
	- Space scales exponentially with height, even if node count doesn't!
- Linked Representation (nodes)

Using BSTs
- Dictionary: stores words in lexographical order
	- Finding word: compare a query with each node, following accordingly
	- Inserting word: Recursively insert into a corresponding subtree
	- Deletion: 3 cases
		- If a node has no children, just delete it
		- If a node has one child, point its parent to its child
		- If a node has two children, replace it with...
			- Inorder successor: right subtree's leftmost child
			- Preorder successor: left subtree's rightmost child (inorder predecessor)
			- ![[Pasted image 20230914152929.png]]