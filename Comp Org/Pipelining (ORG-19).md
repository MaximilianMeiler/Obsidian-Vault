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