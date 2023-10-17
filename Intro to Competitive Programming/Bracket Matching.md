
Say you're given an expression of brackets, consisting of:
	() 
	\[]
	{}
	<>
	(**)

Iterate through the expression as follows:
- If you find a beginning bracket, push it onto the stack
- If you find an ending bracket, see if the top of the stack matches
	- If so, pop off the stack
	- If not, the expression is invalid
- If you find anything else, ignore it