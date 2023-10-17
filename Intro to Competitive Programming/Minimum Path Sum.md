https://leetcode.com/problems/minimum-path-sum/


Max path: can only move down or right
- `sum(y, x) = max(sum(y, x-1), sum(y-1, x)) + val[y][x]

Varitations
- Min path
- Can move diagonally
	- Insert one more sum() condition in max()
- Path can start at any point on the first row
	- (?) change invisible top row from dp table from INF to 0
- Path can end at any point on the last row
	- Quit iteration when reaching the last row, rather than the last box