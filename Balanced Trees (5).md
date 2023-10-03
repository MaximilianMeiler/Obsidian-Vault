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
	- .

