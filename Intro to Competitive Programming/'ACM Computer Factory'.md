http://poj.org/problem?id=3436


Each machine has production values, required input, and output
- You aim to get all parts produced
- Source - 0 … 0 
- Sink - 1 … 1 

Construction of the flow graph
- State representation
	- Each production state is a node
	- The machines connect these nodes!
		- These edges are weighted with their production capacity
		- Connect "2" things with inf-capacity edges
- Machine representation
	- Each machine is a node
	- Use production states to connect machines
	- The weight of each edge is the min production of the two machines it connects