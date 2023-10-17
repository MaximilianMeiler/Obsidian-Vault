https://leetcode.com/problems/burst-balloons/


- Assume you burst at element k
	- maximize dp\[i->k-1] * dp\[k+1->j] + k\*i\*j
		- Solve last pop first, assume all other balloons besides edges/k have been popped
	- dp\[i, j] denotes solution on open region i,j
		- `d[i,j] = max(d[i,k] + d[k,j] + v[i]*v[k]*v[j]`