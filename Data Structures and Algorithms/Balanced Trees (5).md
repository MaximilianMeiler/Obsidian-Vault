Previous lecture: [[Trees (4)]]

\<First lecture missing>

Rotations
- Equivalize tree height while still leaving it a valid BST

Cases
- ![[Pasted image 20230926142806.png]]
- Right Right
	- Left Left, but mirrored:![[Pasted image 20230926141234.png]]
- Right Left
	- ![[Pasted image 20230926141442.png]]
- Left Right
	- ![[Pasted image 20230926141458.png]]

AVL properties
- BST invariant (smaller left children, larger right children)
- For every node, balance factor is -1,0, or 1
	- BF = height of left subtree - height of right subtree
- Node classes store their heights/balance factors
	- ![[Pasted image 20230926142257.png]]
- Insertion/Deletion
	- Same as BST
	- Find the deepest node that breaks balance rule, rotate it and move upwards
	- The height of all nodes in the operation's search path may have changed
	- ![[Pasted image 20230926142629.png]]

[[Balanced Trees (D5)]]

Height of an AVL tree ~= 1.44log(n + 2)
- Thus, all operations are O(logn)
- Proof
	- .What are the max number of nodes in an AVL tree of height h?
		- n = 2^h - 1
	- What is the min number of nodes in an AVL tree of height h?
		- n = N(h)
	- Nh <= n <= 2^h - 1
		- ![[Pasted image 20231003141556.png]]
		- ![[Pasted image 20231003141651.png]]
		- h <= 2log(Nh)

Red Black Trees
- Custom properties
	- Nodes are either red or blck
	- The root is always black
	- A red node always has black children (no two consecutive red nodes)
	- The number of black nodes from the root to any leaf is the same
	- *Null nodes are attached to the leaves and are black*
- Fixed thru rotations and color flips
- Insertions
	- Insert nodes as usual
	- New nodes are always red
	- Cases
		- If the tree is empty, color the node black and make it the root
		- If the new node's parent is black, continue
		- If the parent is black, look at the uncles' color
			- If red, flip colors
				- Change last generation to black
					- Change last last generation to red
			- If black, rotate (remember, nullptrs are black)
				- Recolor - change the rotated nodes to red and parent to black

Splay Trees
- Bring accessed nodes to the root for easier access
- BSTs with another "splay" operation - makes given node the root
	- Achieved through zig (right) and zag (left) rotations
		- If a node has a parent but no grandparent, rotate once
			- With a grandparent, rotate twice
			- If parent and gp are in the same direction, do the same rotation twice. If not, do different rotations.
			- Perform rotation on parent first, then child
		- Zig
		- Zag
		- Zig-Zig (LL): Apply zig to x, then zig to x
			- Ends in right right case
		- Zag-Zag (RR)
			- Ends in left left case
		- Zig-Zag (LR)
		- Zag-Zig (RL)
- Guarantees m operations will take mlogn times

B/B+ trees
- Inserted nodes store multiple elements
	- Threshold amount for key amount stored (l)
- Each node has up to n children, following BST properties
	- Elements between min/max key values in middle children
- Tree is built bottom-up
- Leaves are at the same depth
- Non-leaves store up to n-1 (l) keys
	- Leaves have \[ciel(l/2), l] keys except when tree has under l/2 elems
- Root is a leaf or has \[2,n] children
- Non-leaves have \[ciel(n/2), n] children
- B+ tree extra properties
	- ALL data is stored in the leaves (node data is copied down)
	- Leaves point to other leaves, forming a linked list


Next lecture: [[Heaps and Priority Queues (5)]]