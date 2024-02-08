Previous lecture: [[ARM Procedures (ORG-9)]]


When a procedure is called:
- A frame pointer is placed at the current stack top
- The current temp variables, arguments, and return address is stored in the stack
- A stack pointer is placed at the new stack top
- ARM representation
	- MOV FP, SP
	- SUB SP, SP, \#40 (ex. 5 things to save, * 8)
	- STUR X0, \[SP, #32]
	- STUR X1, \[SP, #24]
	- STUR X2, \[SP, #16]
	- STUR FP, \[SP, #8]
	- STUR X30, \[SP, #0]
	- MOV X0, X2 \#setup arguments
	- BL CALLEE
	- MOV X9, X1 \#return value
	- LDUR X0, \[SP, #32]
	- LDUR X1, \[SP, #24]
	- LDUR X2, \[SP, #16]
	- LDUR FP, \[SP, #8]
	- LDUR X30, \[SP, #0]
	- ADD SP, SP, #40
- Call BR X.. in a function to "return"

