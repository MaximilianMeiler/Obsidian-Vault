https://leetcode.com/problems/container-with-most-water/


Naive n^2 solution TLEs 

Capacity is always determined by smaller edge
- Start at both ends (we want width to be large)
- Move the smaller edge in, update global max w new val if needed
	- Moving the larger one in will never help!
	