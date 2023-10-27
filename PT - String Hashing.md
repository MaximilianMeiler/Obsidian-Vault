Previous lecture: [[PT - KMP]]


We want to compare many strings efficiently by converting strings to ints
- if s == t, hash(s) == hash(t)
	- How do we minimize collisions that contradict the converse?
- Polynomial rolling hash function
	- ![[Pasted image 20231026190156.png]]
	- Choosing m and p 
		- Both should be prime
		- m should be large to reduce collisions - 10^9 + 9, 10^9 + 7
		- p should be small while still including the alphabet - 31, 29
- Allows for fast hashing of substrings
	- String s (length n) and q queries, each containing indices a and b
		- hash(s\[a...b]) = hash(s\[0...b]) - hash(s\[0...a-1])
		-  Store the hashes at each char for quick "prefix sum" solves
- Number of distinct substrings
	- Naive solution - iterate over all pairs, place the corresponding sstring in a set
	- We can do the same thing, but finding sstring hashes is faster than finding substrings!
- Rabin-Karp algorithm - same scenario as KMP
	- Compute the hashes for m and t
	- If the hash at any point in t is equal to m's total hash, you've found a match
		- Note that you should only be checking substrings equal to m's length
- Number of distinct palindromic substrings
	- Let S be our string, T being S reversed
		- S\[i...j] is a palindrome iff hash(S\[i...j]) == hash(T\[n-1-j...n-1-i])
- Longest common substring
	- Compute hashes for S and T
	- Binary search on k, the length of the LCS
		- Place all k-length substrings of S in a set, check if any occur in T
		- runs in nlogk
- Avoiding collisions - double hashes
	- When comparing strings, check 2 hashes with different p/m's
	- 