//


Let N\[i,j] be the min amount of scalar multiplications to compute the matrix A\[i]A\[i+1]...A\[j]
- Leverage the association rule: AxBxC can be done (AxB)xC or Ax(BxC)
	- Interval DP!
	- `N(i,j) = min(N(i,k) + N(k+1,j) + d(i)d(k+1)(d(j+1))`
- Filling the table up bottom-up
	- N(i,i) = 0 (any matrix x itself is 0)
	- Work up, then fully right
	- 