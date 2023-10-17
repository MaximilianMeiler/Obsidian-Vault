Previous lecture: [[Data Structures B (3)]]


2^10 = 10^3, 2^20 = 10^6, 2^30 = 10^9
- Ints only work up to 2x 10^9 (2^31 - 1)
- Long long only works up to 9x 10^18 (2^63 -1) 
Computers run it 10^9 cycles per second
- If input ever exceeds 1 million, IO will become the bottleneck
Sorts work best in Omega(nlogn) time

Selection sort
- Iterate through, find the smallest value, swap w/ beginning (or add to new array)
- O(n^2)
- Efficient in number of swaps, not comparisons though
- Turns to O(nlogn) if a heap is used for comparisons (heapsort)

Insertion sort
- Not inefficient in number of swaps
- O(n^2)
- Good if already mostly sorted

Merge sort
- Divide and conquer
- Recursively sorts each half, then recombines
- Can be used to calculate the number of total inversions
	- Inversions of first half + inversions of last half + inversions needed to merge
	- During merging, a lesser element in array B is inverted with EVERY remaining element of array A
	- [[Global and Local Inversions]]

[[Majority Element]]

Quick Sort
- Partition around a pivot - all lesser come before and all greater come after
- Fastest in-memory sorting

Included in stl
- Sort
- nth_element
- set_union, set_intersection, set_difference
- unique


Next lecture: [[Sorting and Searching B (5)]]