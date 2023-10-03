Previous lecture: [[Greedy A (6)]]


- [[`Fair elections`]]
- [[`Radar Installation`]]

Fractional Knapsack
- Given a weight capacity, and items with a value and weight
- Pick the item with the max value/weight if you can "cut up" the items into weighted units
- If you can't "cut up", the items, this is more difficult (0-1 knapsack)
	- Dynamic programming solution!
- [[`Maximum Units on a Truck']]

Huffman Code
- Optimal prefix code commonly used for data compression
	- High-frequency symbols become shorter
- Trees represent frequency
	- Lowest nodes represent least frequent elements
	- Construction
		- Place nodes in  a priority queue
		- Dequeue one on a left subtree, teh other on the right
	- Decoding tree
		- For each value, following a left branch is a "0", a right branch is a "1"
- [[`Add all`]]

Greedy Algorithms on Graphs
- Djiskstra's - shortest path
	- Always take shortest edge
- Kruskal's - min cost spanning tree
	- Always tries lowest-cost remaining edge
- Prim's - min cost spanning tree
	- Always take lowest-cost edge between spanned nodes and non-included nodes
- May not work on weighted graphs with negative values

- Shortest Path
	- Source s, destination t given
	- Greedy (Djikstra)
		- Any any point, take the shortest cost option
			- This provides a current shortest option
		- Find the further shortest edge leading out of the set
			- Then add the corresponding node to the set
			- Repeat until destination is found?
		- Basically, each node stores the shortest cost from source
			- Update adjacent nodes with total path cost if able
		- [[`Subway2`]]

Spanning Tree
- A tree that connects all vertices of G once
- Minimum Spanning Tree has the least overall weight on edges included
- Removing any edge creates 2 other MSTs
- Kruskal
	- Sort by edge weight, connect if needed and skip if already in graph (loop)
		- Check if already in graph by giving connected nodes a "grandparent root"
	- [[`Arctic Network`]]


Next lecture: [[Dynamic Programming A (8)]]