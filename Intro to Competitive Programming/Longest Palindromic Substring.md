Naive is O(n^3) - comparing all possible substrings

Observe that a palindrome occurs if a palindrome is surrounded by 2 equivalent characters
- Let dp(i, j) denote whether the string from i to j is a palindrome
	- dp(i, i) is always true
	- dp(i, i + 1) is also simple - check if the i and i+1 are equivalent
	- `dp(i, j) = (a[i] == a[j]) && dp(i + 1, j - 1)`

Can be solved in linear time by Manacher's algorithm
