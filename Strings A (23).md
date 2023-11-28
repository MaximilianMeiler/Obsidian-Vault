Previous lecture: [[Misc A (22)]]


String matching (string length n, target length m)
- Naive - check at every index for the target string (O(nm))
	- Finding a mismatch doesn't always mean we should restart - maybe restart from the middle of m?
		- ex. finding a "B" instead of a "C" for the last index of "ABABAC"
		- Can create a matrix to store what state to move into, matrix\[curr state]\[letter of n]
			- The size of this matrix can blow up very quickly!
		- Can be compacted into an array that tells what index to restart at if a mismatch is found as index i
			- Finding the prefix failure function:
				- The number of characters in the prefix and suffix that are equal
				- If check on index j is failed, check pi\[j - 1]
- KMP algorithm
	- Preprocesses the prefix failure function
		- O(m)
	- If a prefix/suffix match is found (prefix ends at i, suffix ends at j)...
		- At i-1, the string should also match with j-1
	- Jump down matched substrings 
		- [INSERT CODE FROM SLIDES]
	- [['Shortest Palindrome']]
	- [['Periodic Strings']]
- Boyer-Moore Algorithm
	- 
		- If at any point, a mismatched letter in n does not occur in the target string m, you can just completely restart target matching on the next index
		- The mismatched letter "walls off" comparisons between relative string halves
	- Bad character rule
		- Use skip table - if a mismatch is found, just shift to accommodate mismatch from an earlier target string character
		- Store the rightmost occurrence of every character in the target string
	- Good suffix rule
	- Longer skips by working backwards?