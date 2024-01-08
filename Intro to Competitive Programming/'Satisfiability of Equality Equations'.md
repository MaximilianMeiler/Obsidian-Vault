https://leetcode.com/problems/satisfiability-of-equality-equations/


- a == b
	- a -> b
		- b -> a
	- ~a -> ~b
		- ~b -> ~a
- a != b
	- a -> ~b
		- b -> ~a
	- ~a -> b
		- ~b -> a

Anyways...

We can just use union-find to solve this problem
- \==: place both letters into the same group
- !=: check if the letters are in the same group