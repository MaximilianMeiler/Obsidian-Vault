Previous lecture: [[Single Cycle Datapath B (ORG-18)]]
Discussion [[ORG-D8]]


Pipelining
- Separate resources for each stage
- Use all applications possible with one resource, repeat

Time for ARM instructions ![[Pasted image 20240306172022.png]]

Speedup:
- Single-cycle: ![[Pasted image 20240306172138.png]]
- Pipelined: ![[Pasted image 20240306172200.png]]

![[Pasted image 20240306174237.png]]

Data Hazards
- Structural - two instructions need the same hardware in the same cycle
	- Von Neuman - Combines data instructions and memory
		- Harvard architecture - separates the two to avoid hazards
	- Split cycle I/O - Writing occurs in the first half, reading in the second half of a cycle
- Data - An instruction needs data from a register before it has been calculated
- Control - Instruction to fetch is unknown because the result of a branch decision is not known yet
	- ![[Pasted image 20240318110753.png]]
	- Often, it is just predicted that a branch is not taken initially, and redone (as above), if not: ![[Pasted image 20240318110935.png]]


- Forwarding - eliminates all R-type hazards
	- ![[Pasted image 20240318105553.png]]
- Load-use Hazard
	- Stalling used to prevent: ![[Pasted image 20240308174615.png]]
	- ![[Pasted image 20240318105722.png]]

![[Pasted image 20240318221629.png]]

Avoiding control hazards
- Normally, SUB -> CBZ leads to 3 stalls! We can change our design to improve this
	- By moving branch calculation and condition checking all into the ID stage (above)
	- SUB -> CBZ now requires one stall
	- LDUR -> CBZ requires 2
		- Let LDUR reach last stage before letting CBZ advance beyond ID
- We predict a branch to either be taken/not taken
	- If our CBZ passes the ID stage and we are incorrect, we need to flush out all of the instructions we incorrectly did in the meantime
- Other predictions
	- Backward branches always taken, forward branches never taken
	- We can also use a 2-bit predictor
		- Flowchart where more takens skew the program into taken more branches and vice versa
		- 00 (never take) <-> 01 <-> 10 <-> 11 (always take)
	- Branch history table - stores if we have previously branched or not at an address


Next lecture: [[Cache Memory (ORG-20)]]