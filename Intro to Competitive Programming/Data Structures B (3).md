Previous lecture: [[Data Structures A (2)]]

Examples
- [['Escape from Stones']]

Sets and Treesets
- Sets cannot have repeat elements
- Sets are based on a balanced search tree
	- O(logn) operations
- Unordered sets are just hash-table based
	- O(1) avg operations
- Works similar to a map, but just stores a key instead of a key/value pair
- [['Andy's First Dictionary']]
Maps
- Each element has a key and a corresponding values
	- No two values can share a key
- Balanced bin search tree
	- O(logn) operations
Priority Queue
- Multiset such that the first element of the queue is the greatest one
- Heap structure (special binary tree)
- [['Argus']]
Hash table
- O(1) insert/search/delete IF the hash is good
- Direct Addressing Table (DAT)
	- Key values are distinct
	- Store items in an array, indexed by keys
- [['Newspaper']]

Comparison
- Counting the number of unique elements
	- Set: Slowest (17.35 for large n)
	- Unordered set: (7.18 for large n)
	- Sort + check: Fastest (1.38 for large n)
- Determining the most frequent value
	- Map: Slowest (9.57 for large n)
	- Unordered map: (2.83 for large n)
	- Array: Fastest (0.11 for large n)
- Adding and removing elements
	- Multiset: Slower (30.93 for large n)
	- Priority queue: Faster (5.95 for large n)

Prefix Sum
- [['Stripe']]


Next lecture: [[Sorting and Searching A (4)]]