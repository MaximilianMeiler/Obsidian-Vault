Previous lecture: [[PT - Combinatorics under Mod]]


How many times can you find a pattern m in a text t?
- Naive solution compares the same characters many times
- KMP algorithm
	- Start like the naive, but as soon as you have a mismatch after some matches...
		- If the checked suffix and prefix is the same, skip to the suffix
	- Preprocess the string to build a "reset table"
		- First index = -1, most things just point to 0
		- Each element in "m" refers to its own prefix index (what to start over at)
		- When a mismatch occurs, start at that t index for the corresponding prefix index
	- You basically


Next lecture: [[PT - String Hashing]]