
Given a state, find the moves that give it to a goal state

Track the movement of the empty space
- All possibilities - swapping the empty with each adjacent tile
- Use BFS to find the shortest path
	- Each vertex is the complete state of all 8/9 tiles

**Does not use DP because states are not reduced upon recursion

Similar question: "8 queens"