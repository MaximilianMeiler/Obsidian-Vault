Making a min heap from a BEST
- Iterate using inorder traversal, storing the values
- Pass through the tree with preorder
	- For each node you pass, replace this with the corresponding stored inorder node
	- For a max heap, use postorder instead
	- 