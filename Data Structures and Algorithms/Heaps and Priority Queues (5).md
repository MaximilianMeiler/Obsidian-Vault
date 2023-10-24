Previous lecture: [[Balanced Trees (4)]]
Discussion: [[Heaps (D5)]]

Priority queue
- All elements have a priority, elements with highest/lowest priority are removed first
	- Insertion(prio)
	- ExtractMin(), ExtractMax()
	- Unsorted array implementation
		- Insertion - O(1)
		- ExtractMin - O(n)
	- Sorted array implementation
		- Insertion - O(n)
		- ExtractMin - O(1)
	- Sorted list implementation
		- Insertion - O(n)
		- ExtractMin - O(1)
	- Binary heap implementation...
		- O(logn) for both

Binary heap
- Complete binary tree (left-shifted last row, but not ordered!)
- Root has the smallest priority (smallest min-heap, greatest max-heap)
	- Each node is less than its children for a min-heap
	- Each node is greater than its children for a max-heap
- Only the root can be removed!
- For any node at position p in a heap:
	- Left child is at position `2p + 1
	- Right child is at position `2p + 2
- Any node's parent can be found with `floor((c-1)/2)`
- Insertion
	- Insert the node at the next bottom heap position
	- If this new node is greater than its parent, swap it with its parent
		- Repeat until equality is re-satisfied
	- log(n)
	- ![[Pasted image 20231005153734.png]]
- Deletion
	- ExtractMin - deletes root
		- Replace root with last element in the heap and swap down
		- Smaller child is always swapped upwards
	- log(n)
- Heap sort
	- Insert n items into heap
	- Remove n items from heap, place in array
	- O(nlogn)
- Creation in-place: only takes O(n) time!

K-largest elements
- Find the K largest items
- Idea: Insert everything into a max-heap and pop K out
	- .
- Idea: Keep k(+1) elements in a min heap, continuously pop the lowest one out
		- Much more memory efficient

Running median
-  Keep two heaps - one for smaller elements and one for larger them
	- Make one a min, one a max so middle-ish elements come to the top
- If the number of elements in both trees are unbalanced, move the root of the larger one into the smaller tree
- The median at any time is the average of both roots (equal n), or the root of the tree with 1 more element


Next lecture: [[Sorting (6)]]