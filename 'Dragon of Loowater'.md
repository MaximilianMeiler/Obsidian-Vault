https://onlinejudge.org/index.php?option=onlinejudge&Itemid=8&page=show_problem&problem=2267


Method 1
- For every head, find the shortest knight whose height is greater than the diameter (binary search)
Method 2
- Sort the diameters and heights
- If a knight can chop the top head, move on w both
	- Otherwise, move to the next knight
	- If no more knights remain, Loowater is doomed