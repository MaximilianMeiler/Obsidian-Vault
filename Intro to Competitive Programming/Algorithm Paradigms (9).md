Previous lecture: [[Graphs (8)]]

Brute force
- All possible solutions
- Computationally expensive
- Always correct

Divide and conquer
- Split the problem into non-repeating subproblems
- Combine the solutions

Greedy
- Repeatedly take the local optimal solution
- May not always be correct

Dynamic programming!
- The problem is split into overlapping/repeating subproblems
- Store the solutions to these intervals as not to recompute them

Ex: coin change
- Given quarters, dimes, nickels, pennies - find the min number of coins to add up to n cents
	- Greedy works (take largest coin less than n first)
- Given other coin denominations, greedy won't work!

Ex: Bin packing
- Store boxes (14 units, 16 units, 4 units, 6 units) into 20-unit containers
- Greedy algorithms
	- Loot at items on at a time (online implementations)
	- First fit: place the new item in the first bin that is large enough
	- Best fit: place the new item in the bin that creates the least empty space

Ex: Binary conversion
- Get the largest power of 2 that fits in n, subtract it from n and repeat

Huffman Trees
- Encoding characters takes log(n) bits, where n is the number of characters.
	- Characters used more often should be given a smaller value
- Construct a set of trees with root nodes that contain each of the individual symbols and their frequencies
	- Place the set of trees into a priority queue, ordered by their frequency (min first)
	- Take the last two out of the queue, combine them as children into a parent (add frequencies), place that parent back into the queue
	- When only 1 node is in the queue, that is the root of the huffman tree!
- Traversal
	- Move left on the tree: 0, move right on the tree: 1
	- Stop when you hit a leaf
		- Nodes earlier on in the tree take less bytes to store, since they use less bits!

Dynamic Programming
- Top down: memoize
- Bottom up: tabulate
- Fibonnaci
	- Brute force recursion - O(2^n)
	- Tabulation - O(n)
		- 0: 0, 1: 1, iterate upwards and store fib(n)
	- Memoization - O(n)
		- fib(n) calls fib(n-1) and fib(n-2), the answers are stored from bottom-up
- Knapsack
	- Fractional: just compute value / weight for each and take highest-ratio'd items as much as possible
	- 0-1: 
		- Brute force: 2^n combinations of sets for n items
		- Greedy: Repeatedly add item with max ratio - not good
		- DP
			- How to we split up the problem: at any item, choose to pick or not
			- What happens when we have no items?
			- What happens when we have one item - always pick if possible
			- 