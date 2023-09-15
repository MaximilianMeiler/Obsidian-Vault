Previous lecture: [[Efficiency (1)]]
1 2 2
21 4 4
A data structure is a particular way of organizing data so it can be used effectively
- Fixed-size arrays
- Dynamic arrays (vectors)
	- Add/removal to end is almost as fast as normal array (O(1))
	- See [['Table Tennis']]
- Heap
- Stack
	- Last in, First out
	- O(1) insertion & deletion
	- Used in recursion, bracket matching
	- [[Bracket Matching]]
	- [[Postfix Matching]]
- Queue
	- Used for BFS, Topological sort
	- [['Table Tennis']]
- Deque
	- Dynamic array which can be manipulated from both ends
	- O(1) average time, but with a larger constant factor
	- Often used for sliding window problems
- Linked Lists
- Pairs / Tuples
- etc...

Operator overloading:
- `bool operator<(const student& a, const student& b) {return ...}`
- "student" class can now be automatically be used with .sort / priority queues


Next lecture: [[Data Structures B (3)]]