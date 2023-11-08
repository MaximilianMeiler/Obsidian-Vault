Previous lecture: [[PT - Computational Geometry]]


Given a list of numbers how can we handle additions and ranged-sum queries efficiently?
- Add a given val at a given index
- Add a range of values from i->j
	- Both operations log(n)!
- NOTE - these are 1-indexed :gasp:

Fenwick tree implementation
- The value at index i stores:
	- j, the location of the first 1 in the binary representation of i
	- The sum of the previous 2^j
		- ex. 0011 stores 1 last val, 0010 stores 2 last vals
- sum(i) - repeatedly subtract j's at each index, add sum iteratively
- add(i, v) - Continually flip bits (?)


Next lecture: [[PT - Tries]]