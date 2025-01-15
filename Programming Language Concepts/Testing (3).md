Previous lecture: [[Regular Expressions (2)]]


Test-driven development: implementing cases as you develop

Unit Testing
- Tests things
- Input conditions -> expected direct/indirect results

Techniques
- Black box ("functional")
	- Based on requirements
	- Techniques
		- Equivalence Partitioning: testing separate sets of equivalence classes
		- Boundary Analysis: 
		- Cause/Effect Analysis: 
			- Identify causes and effects
			- Deduce logical relationships and constraints
			- Identify an appropriate test case selection strategy
				- All Feasible Combinations of Cases
					- All Effects covered with the Minimum number of test Cases
			- Construct a test coverage matrix
- White box ("structural")
	- Based on internal logic
	- Techniques
		- Boundary Analysis
		- Logic Coverage
			- Execute all statements
			- Traverse every branch
			- Make every condition true or false
			- All feasible paths traversed at least once
		- Path Conditions ^ 
			- Should be expressed in terms reflecting relevant state changes along the path
			- Symbolic Evaluation allows for systematic tracking of state changes for this purpose
			- A path is infeasible if its condition reduces to false


Next lecture: [[Lexical Analysis (4)]]