https://onlinejudge.org/index.php?option=onlinejudge&Itemid=8&page=show_problem&problem=2445


Achieve max possible spending while still remaining under budget
- However, one of each garment is required

Say you implement by index and money left
How do you return the shopping list?
- Work backwards, looking if any of the items of a certain garment match the path used

Bottom-up technique
- Set the c = 1 level full of 0s, with 1s where the m's values are
	- Alternatively, set only the money=0 col of c = 1 to 1
	- For any subsequent levels, add all ms to all 1s in the previous level
- The max spending is the rightmost 1 in the last level <= max budget
	- To return, work back across all ms from this box
	