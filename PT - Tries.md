Previous lecture: [[PT - Fenwick Trees]]


Given a list of strings s and a target strings t, how can we check if each target string is in s?
- Naive: O(n \* s\* t) - n = length of strings

Tries
- Nodes represent string prefixes and edges represent adding a letter to that prefix
- Root - the empty string
- Total runtime - O(n \* S + n \* T)

Node struct
- Vector of node pointers
- bool leaf (not an actual leaf - is this the last letter of a word)
- constructer assigns 26 nullpointers to the vector

Maximum XOR
- Given an array A of N integers, find A\[i], A\[j] such that A\[i] XOR A\[j] is maximized
- Insert the binary representations into a trie
	- Loop through every b in A
	- for every bit in a, take the xor if possible
		- Is possible? push back a 1
		- If not, push back a 1
		- The max of all these values is your max XOR


Next lecture: [[PT - Segment Trees]]