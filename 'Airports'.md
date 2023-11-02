https://open.kattis.com/problems/airports


Standard representation
- Airports are nodes
- Edges represent flights from one airport to another
	- You can merge node values (inspection time) of the destination with the time of flight for the edge weight
- Each destination should store a set of connecting flights
	- How do we schedule all these connecting flights optimally...?
	- Use another graph that stores 2 sets of nodes representatives of edges
		- Group edges by connecting flights possible
			- ex. if A -> B is edge 1 and B -> C is edge 2 and you can connect from A to B to C, place an edge in between 1 and 2 with weight 1
		- Connect a source node to all first nodes and sink node to all second nodes
			- These edges will also have weight one - you can optimally only send one airplane down each path!
			- Run max flow - it will give you how many flights you can save