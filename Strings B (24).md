Previous lecture: [[Strings A (23)]]


Tries!
- Edges between nodes are letters
- Insert words, where the root is the original empty string
	- If child node of the current char is null, make a new node and turn that to the curr node
	- Otherwise, set curr node to child node and move to next char
- Nodes should store if they are word endings for lookups
	- o***r***ang***e***
- O(m) worst-case lookup time, but generally worse than hashes
- Suffix Trie
	- Create a trie with all of a string's suffixes (cat, at, t, )
- Suffix Tree
	- Similar execution to suffix trie
	- No insertion character by character, instead edges represent string chunks
	- Edges need to be adjusted (split) on runtime
	- Uses - string matching
		- Can look for many patterns on the same host text
		- For one pattern, all leaf nodes after following the pattern's chars contain that pattern
		- O(m + \#occ)
	- Uses - longest repeated substring
		- Any edge from the root is a substring
			- The number of eventual child nodes from the subroots are the number of repeats!
	- Uses - longest common substring
		- Insert both words into the suffix tree, with different markers for ending nodes
		- If any internal node shares an eventual \# and $ (both markers) child, these are a shared substring
- Suffix array
	- Sorted array of all suffixes of a string 
		- \[acat$ (0), cat$ (1), at$ (2), t$ (3), $(4)] -> \[\$ (4), at\$ (2), acat\$ (0), cat\$ (1), t\$ (3)]
	- Sorted indices array (corresponding strings can be taken from original array):
		 `bool cmp(a, b) {
			`return strcmp(T + a, T + b) < 0;
		 `}
		 - O(n^2logn) :(
	 - Uses - string matching
		 - Since array is sorted, use binary search to find target string location in array
			 - Use twice - once for lower bound of matches, once for upper bound
	 - Uses - longest repeated substring
		 - The array is sorted!
		 - Just compare neighbors - the longest similarity between adj indices is the LRS
	 - Uses - longest common substring
		 - Concat both strings: (ex. first$second#)
		 - Run LRS algorithm, but both neighbors have to be "owned" by different strings
			 - This can be checked by seeing if one index is past n, one index is before n
		 - O(n + m)


Next lecture: [[Misc B (25)]]