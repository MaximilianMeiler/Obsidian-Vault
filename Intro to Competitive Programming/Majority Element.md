https://leetcode.com/problems/majority-element/

- Unordered map: O(n)
- Binary search tree (map): O(nlogk)
- Randomization: O(n)
	- Can be either fast or slow - majority element is most likely to be chosen!
- Sorting: O(nlogn)
- Partial sorting: O(n)
- Divide and conquer: O(n) - O(nlogn)

Boyer-Moore Voting Algorithm
- Uses linear time and constant space
- For any given number (start with array\[0])
	- Add to a running sum if a match is found
	- Subtract from the sum if a non-match is found
	- If sum > 0, this is the majority. Keep working
	- If sum = 0, it is equal to half
		- On this case, restart the algorithm
		- All prior numbers found cancel each other out