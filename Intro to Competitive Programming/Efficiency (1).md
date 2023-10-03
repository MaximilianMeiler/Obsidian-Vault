Previous lecture: N/A

An algorithm is a set of steps to accomplish a task

Graded on...
- Correctness
- Efficiency

How to find time complexity?
Determine the number of operations needed in regard  to the problem size
- O(f(n)): Asymptotic upper bound
- Omega(f(n)): Asymptotic lower bound
- Theta(f(n)): Asymptotic tight bound

Even a low-complexity algorithm may run slowly if the constant operations repeated are slow

Make sure to know the worst cases of your sorts - test cases may catch you on them!

Estimations of needed efficiency:
- n <= 10: O(n!)
- n <= 20: O(2^n)
- n <= 500: O(n^3)
- n <= 5000: O(n^2)
- n <= 10^6:  O(n) or O(nlogn)
- n is large: O(1) or O(logn)

Complexity for string operations:
- Append char to end: linear
- Remove chars: linear
- Add strings: linear
- Get substring: linear
- Find character: linear
- Return reference to char at index: constant
- Get last char: constant

Problem-solving practice:
	[[Largest Sum Contiguous Subarray]]

Further code optimization:
- Break loops when needed


Next lecture: [[Data Structures A (2)]]