Previous lecture: [[Trees B (21)]]


2-SAT
- Terms
	- Set of variables which are true or false
	- Set of literals, which adjust variables
	- Set of clauses, which relate variables all need to be satisfied at once
- 2-CNF
	- Each clause has 2 literals, where every clause is a disjunction
	- ![[Pasted image 20231120092649.png]]
- Graph conversion
	- (A v B) <-> (~A  -> B) ^ (~B -> A)
		- Conditionals can serve as directed edges!
		- If an edge connects A -> B, another connects ~B -> ~A 
	- A problem is not satisfiable is ~x is reachable from x, and vice-versa (same SCC)
- [['Peaceful Commission']]
- [['Satisfiability of Equality Equations']]

Bipartite graphs
- [['Bipartite Test']]
- [['Graph without Long Directed Paths']]
- Maximum matchings
	- For two distinct node groups A and B, find the max amount of connections between A and  B (where each node can only have one edge)
	- Use max flow algorithm - connect all of A to a source, all of B to a sink 
		- Set all edge weights to 1
		- [['Maximum Students Taking Exam']]
	- Other method
		- Start with arbitrary matching
		- Pick a free vertex in one set, run BFS on this
			- Alternate unmatched/matched edges until an augmenting path is found
				- At this point, flip the edges and repeat until no augmenting path


Next lecture: [[Strings A (23)]]