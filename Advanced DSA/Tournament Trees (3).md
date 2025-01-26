Previous lecture: [[External Sorting (2)]]


Winner trees
- Complete binary tree (n-1 internal nodes, n leaf nodes)
- Leaf nodes represent a player, internal nodes store the winner between that node's two children
- Its just a segtree
	- Time to initialize: O(n)
	- Replace and replay: O(logn)

Loser trees
- Each node stores the match loser rather than the winner
	- The winner is kicked up to the parent for storage
- Replay works how you'd expect, a bit simpler than the winner tree (since you don't have to look at siblings) but still O(logn)

Applications
- k-way merging for external sorts
- Truck loading (bin packing to minimize number of bins)
	- First fit heuristic: Make a segtree on amt open per bin, then go down left in a winner tree as long as the new node's value can fit the new package