Previous lecture: N/A


Fast exponentiation under Mod
- Compute a^b % m quickly and w/o overflowing
	- Naive method: O(b)
	- Divide and conquer: O(logb)
	- `ll fast_pow(ll a, int p) {
		`if (p == 0) return 1;
			``ll half = fast_pow(a, p/2)
			`if (p % 2 == 0) return half * half % MOD
			`return a * half % MOD * half % MOD

Matrix multiplication
- Naive: O(n^3)
- Strassen's Algorithm: O(n^2.8)

Fast matrix exponentiation
- Calculate a^b and take mod of each element
- Combine the past two ideas!
- Fibonacci calculations
	- \[1, 1; 1, 0]^n 

Combinations
- Choosing k elems from n total
- Formula: n! / k! / (n-k)!
- Often, you have to output mod "m"
	- Division under modulo
		- (a * b) -> ((a%m) * (b%m) % m
		- (a / b) -> ???
			- Modular inverse: *a*a = 
			- Fermats little theorem: a^p-1 is congr to 1(mod p)

You can take the power of an adjacency matrix
- At any element i,j this is the number of way to get from i to j in p moves


Previous lecture: [[PT - KMP]]