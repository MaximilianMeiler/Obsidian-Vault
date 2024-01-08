Previous lecture: [[PT - Segment Trees]]


Given a text T, find all occurrences of strings from list w
- KMP only finds the instances of one string!
- Corasick - O(lenT + lenW + Z) (z = num matches)

Algorithm
- Construct a trie on the dictionary
- Must construct a finite-state machine with additional links between internal nodes
	- These allow for fast transitions between failed string matches
	- Fail links connect each node to the node corresponding to the longest possible proper suffix in the trie
		- "caa" -> "aa", "a", ""
		- Base case - root children point to root
		- Target of a blue edge found by following parent's blue edge, then searching for a child whose character matches the current node
			- If no such child is found, follow the new edge's blue edge again
			- Repeat until a child is found or the root is reached
	- Dictionary suffix (out) links in nodes point to longest suffies included in the dictionary
		- Blue links that end up at blue (word/leaf) nodes
		- Finding: Traverse blue edges until you find a node in the dictionary
- Trie traversal (aplication)
	- If the next char does not match, follow blue edges until you can
		- If this is a valid word, it's a match
		- If this applied node has a green edge, the green-connected suffix is also a match
			- Recursively?


Previous lecture: [[PT - Fast Fourier Transform]]