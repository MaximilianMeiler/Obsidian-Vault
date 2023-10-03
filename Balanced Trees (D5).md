Red-black trees
- Self-balances thru 4 rules:
	- A node is either red or black
	- The root is always black
	- A red node always has black children
	- The number of black nodes in any path from root to leaf is the same

Splay trees
- Moves most recently accessed nodes to the root
- Two operations: zig, zag (left & right rotations)

B trees
- Non-binary self balancing trees
- Designed to store huge amounts of children
- Can have multiple key-value pairs by node, sorted ascendingly by keys
- Properties
	- All nodes have at most n children
	- The root node is either a leaf, or has 2-n children
	- Internal nodes have ciel(n/2)-n children, and a max of n-1 keys
	- L is the max numbers of keys a node can have

B+ trees
- B tree, but each node only contains keys and not values
- All data is stored in leaves
	- Leaves at the bottom create a left-to-right linked list