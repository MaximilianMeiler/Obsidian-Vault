
There are 2 water jugs with capacities N and M litres
- Both are initially empty
- Operations allowed:
	- Empty a jug
	- Fully fill a jug
	- Pour water from one jug to another to fill it
- Goal: get a specific volume K in one of the jugs

Say you have a jar of capacity 3, and a jar of capacity 5
- All possible states/vertices - a 2d dp of {a's water, b's water}
- All transitions/edges
	- Empty a jug: (0, y) or (x, 0)
	- Fully fill a jug: (x, 5) or (3, y)
	- Pour water from one jug to another:
		- (0, x+y) or (x + y - 5, 5)
		- (x+y, 0) or (3, x + y - 3)
- BFS from 0,0 until you get to a case with y = 4!
	- 0,0 -> 0,5 -> 3,2 -> 0,2 -> 2,0 -> 2,5 -> 3,4