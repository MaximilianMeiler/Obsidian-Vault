Subarray - contiguous block of original elements
Subsequence - non-contiguous block of of original elements

Brute force is extremely inefficient - 2^n possible increasing subsequences

Breaking into subproblems
- Either use prefix (`a[1:i]`) or suffix (`a[i:end]`)
		- We will use prefixes
- Let d(i) denote the length of the LIS for a\[1:i] (ending with a\[i])
	- If a new a\[i] > a\[j], form a new increasing subsequence ending with a\[i]
	- d\[i] is 1 + d\[j] where a\[j] < a\[i]
- WHEN A NEW ELEMENT IS ADDED
	- Count backwards from the current element
	- If a number is less than the current element, add 1 to its LIS
		- Find the max of all these values
- Return the max of the LIS array

Example: [['Alphabet']]