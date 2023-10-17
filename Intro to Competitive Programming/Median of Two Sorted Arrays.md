https://leetcode.com/problems/median-of-two-sorted-arrays/


Must be done in log time... how can we implement halving?

Finding the median of a sorted array
- If the array size is odd, just take the middle index
- If the array size is even, take the average of the two middle indices
- Avoiding the if statement:
	- L = (n - 1) / 2
	- R = n / 2
	- Median = (L + R) / 2

Merging is too slow, how else can we think about it?
- The final array will always be n + m sized
- Making good cuts
	- Any number on the left >= any num on the right 
		- Verify if left-side of array A is less than right-side of array B and vice versa
	- i + j + 2 = floor((m + n + 1) / 2)
	- Cuts should always move w respect to one another (since the number of elements on each side of the median is constant)
	- Do not iterate linearly to find the best cut - do it like a binary search!
		- This gives us logarithmic time!

- Implementation tip - use imaginary positions
	- Place fake indexes before/after each actual value
	- This ensures each array is odd, and the total size is 2m+2n+2 (even!)
	- If array A is cut at location c, B is cut at m + n - c
		- Corresponding index: 
			- Left: (c - 1) / 2
			- Right = c / 2
		- Good cuts: A\[L] < B\[R] and B\[L] < A\[R]
		- 