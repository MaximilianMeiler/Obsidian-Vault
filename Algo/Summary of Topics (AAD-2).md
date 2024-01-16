Previous lecture: [[Introduction (AAD-1)]]


Stable pair matching
- Hospital h and student s form an unstable pair if both:
	- h prefers s to one of its admitted students
	- s prefers h to its assigned hospital
- Stable assignment: no final unstable pairs
- Input - a set of n hospitals H, and n students S
	- Each hospital ranks all students in order
	- Each students ranks all hospitals in order
- Matching M: a set of ordered pairs of one student, and one hospital
	- Every hospital and student appears in at most one pair in M
	- A matching M is perfect if |M| = |H| = |M| = n

Interval scheduling
- Input - set of jobs with start times and finish times
- Goal - find the max cardinality subset of mutually compatible jobs (most non-overlapping jobs)
- Extension: weighted interval scheduling 
	- Each job has a weight
	- Goal - Find the max weight subset of mutually compatible jobs

Bipartite matching
- Given a bipartite graph, find a max cardinality matching
	- A subset of edges is a matching if each node appears in at most one pair in M

Independent set
- Given a graph, find a max cardinality independent set
	- A subset is independent if every single edge only connects at most one node in the subset (no edges can connect two nodes in the subset)

Competitive facility location


Next lecture: [[Proofs Review (AAD-3)]]