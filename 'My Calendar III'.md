https://leetcode.com/problems/my-calendar-iii/


Segment tree used to store the amount of meetings running at one time
- However, times can go up to 10^9!!
	- When each interval is inserted, split the tree along start and end times
		- ex. (10, 20) turns (0, INF) into (0, 10), (10, 20), (20, INF)
		- Each node stores left, right, cut along children