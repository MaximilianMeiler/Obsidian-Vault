Previous lecture: [[PT - Heavy-Light Decomposition]]


Lazy propagation
- Updates are stored in nodes
	- Each node only stores one value?
- Updates aren't applied until a target is queried

Persistent segment trees
- Imagine we wanted to store the state of a segment tree between every single update
	- Multiverse, timelines, etc
- Storing the entire tree for each iteration is super inefficient
	- However, only logn of the nodes change each time!
	- Thus, store only the nodes that change, and point those nodes to the past if those children are unaffected by the change