Previous lecture: [[PT - Aho-Corasick]]


FFT allows for fast polynomial multiplication
- Normally, just multiply all polynomial terms together and add like terms
	- O(mn)
- We need to reinterpret polynomials to do this faster!
	- Sets of n+1 points are connected by 1 unique polynomial of order n
	- 3x^2 + 9x + 6 = 3(x+2)(x+2)
		- Coefficient form: (6, 9, 3)
		- Root/Scale form: .
		- Sampling form:
	- Multiplication of samples: pq(x) = p(x)q(x) for each x
		- However, degree(pq) ends up being deg(p) + deg(q)
		- We need extra sample points so the end func isn't underdetermined
		- O(n)
- Transformation between forms
	- Discrete Fourier Transform
		- Use the coefficients to generate many samples
		- ![[Pasted image 20231117103004.png]]
		- Usually O(n^2) :(
			- Choose roots of unity for your x to reduce this
			- e^(i\*2pik/n) (i : 0->n-1)
				- Powers of unity roots are other unity roots
				- zeta^(n+k) = zeta^(k) (full rotations)
				- zeta^(n/2) = -1
			- The matrix is now symmetric (A = A transpose)
			- Now, pad the polynomial until n is a power of 2
				- Divide the polynomial into even and odd terms
				- It's a power of 2? Keep repeating!
			- O(nlogn) achieved!
		- Inverse of the table is equal to the transpose (nothing) and complex conjugate
			- Multiplying by the inverse allows us to recover our coefficients!