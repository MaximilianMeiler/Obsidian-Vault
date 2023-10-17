https://leetcode.com/problems/minimum-score-triangulation-of-polygon/


- Triangulation - for every 2 vertices, iterate over all possible edges to connect
	- First and last edges MUST share a triangle - solve them first!
- ``dp(i,j) = min(d(i,k) + d(k,j) + vi*vk*vj)
	- if j = i+1, return 0
	