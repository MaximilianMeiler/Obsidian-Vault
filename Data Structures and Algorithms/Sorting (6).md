Previous lecture: [[Heaps and Priority Queues (5)]]


Selection sort
- Finds the smallest element in a collection
- Moves this to its correct position
- Repeat *size - 1* times

Bubble sort
- Pass through all pairs in the array, swapping elements if needed
- Repeat this, keep iterating until an iteration leads to no swaps

Insertion sort
- Start with the second element (the first element is considered sorted)
- For every new element, move it to the correct position in the sorted region of the array

Shell sort
- Sort subarrays using insertion sort, then merge
	- Swapped with every 2nd element (gap = n/2)
	- Then reduce the gap
- ![[Pasted image 20231019152844.png]]
- Time complexity
	- O(n^2) worst case
	- O(n^(5/4)) average case

Merge sort
- Split the array in half, split each half, merge the two halves
- Divide and conquer

Quick sort
- Per each iteration:
	- Choose a pivot
	- Move everything less than that pivot to the left, everything greater on the right
- Recursively call on each half on the sides of the pivot
- Implementation example
	- Make the first element the pivot
	- Select the first element greater with an "up" index
	- Select the last element less or equal with a "down" index
	- If up is less than down, swap arr\[up] and arr\[down]
		- Otherwise, swap arr\[piv] with arr\[down] and return arr\[down] (piv)
		- Call recursively
- Complexity
	- Worst case - n^2
	- Average case - nlogn

Others
- Sleep sort
- Counting sort
- Tim sort
- Radix sort
- Bucket sort


Next lecture: [[Sets, Maps, and Hash Tables (7)]]