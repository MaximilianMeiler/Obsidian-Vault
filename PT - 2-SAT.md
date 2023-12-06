Previous lecture: [[PT - Strongly Connected Components]]


Normally, SAT problems are NP-complete
- Fastest method is 2^n - pure guess and check

CNF forms - ands of ors
- 2-SAT: only 2 variables are being OR'd at a time
	- Solvable in O(N + M) (N - number of vars, M - number of clauses)

Conversion into graph
- P or Q <-> ~P -> Q and ~Q -> P
- These implications can be shaped into a directed graph!

Algorithm
- If x is reachable from ~x and ~x is reachable from x, the equation is a contradiction
- Check for SCCs
	- If any contains a variable and itself, the formula is unsatisfiable


Next lecture: [[PT - Max Flow]]