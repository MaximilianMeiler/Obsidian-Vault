Previous lecture: [[Misc B (25)]]


Basics of graph modeling
- Identification
	- Identify the vertices (states)
	- Identify the edges (how to move between states)
	- Identify (and translate) the problem objective 
- Implementation
	- Construct the graph from input
	- Run the suitable algos on the graph
	- Convert the output to the desired format

Common graph problems
- Flood fill (visited DFS)
- Maze (may be BFS)
- Topological sort
- Cycle detection
- Shortest path
	- Single-pair
	- Single-source
	- Single-destination
	- All-pairs
- Max flow
- Strongly connected components

Queries on an array
- Use prefix sums for simple sum queries
	- Be able to do this for 2+ dimensions
- Range minimum queries
	- Sparse table - nlogn construction, constant query
		- Find the largest k such that 2^k <= j - i + 1
		- The range is the overlap of \[i, i + 2^k - 1] and \[j - 2^k + 1, j]
	- Block based - linear construction, linear/sqrt lookup
- Lowest common ancestor
	- Cartesian tree
		- Indices in order on tree
		- Smaller vals on top of tree
		- RMQ(i, j) = LCA(i, j)

String matching
- Failure function - how long a substring's prefix equals its suffix
	- KMP algorithm - j <- failure(j - 1)
- Bayer-moore
	- When a mismatch occurs at x = T(s+j-1)
		- If P contains x, shift P to align with the last x in P with T(s+j-1)
		- Else, shift P to align P0 with T(i+1)
- Suffix Trie - all chars
- Suffix Tree - split chars
- Suffix Array - no tree needed [STUDY THIS]
	- Each index stores a corresponding suffix index
	- Longest repeat substring - calculate longest common prefix between 2 successive indexes
	- Longest common substring - concat both strings, find the longest common prefix where indices originate from separate strings

Sweeping line
- Klee's algorithm

Using binary
- Calculating a^n
- Representing subsets using bitmasks