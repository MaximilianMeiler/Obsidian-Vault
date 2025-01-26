Previous lecture: [[Named Calls (3)]]


The Scheduler
- Handles process scheduling for the OS
- Decides what processes to alternate running while balancing the needs of each process
- Interrupting a process means the scheduler has to instead choose another process to run
- State diagram: ![[Pasted image 20250123181928.png]]

Hardware Interrupts
- Say a process requests a read, and is blocked while waiting for the I/O device to finish
	- When the read operation is completed, the hardware issues an interrupt
- Interrupt steps
	- Hardware "raises a line" by increasing its power output on a wire
	- The interrupt controller then sends this signal to the CPU
	- When it has the time, the CPU sends a signal back to the interrupt controller acknowledging the interrupt
		- The CPU will interrupt the current instruction and swap to kernel mode
	- The interrupt controller responds by sending an interrupt request number to the bus (which represents which hardware device caused the interrupt)
	- The Interrupt Dispatcher finds and executes the correct Interrupt Handler by looking up the request number in a vector table
- Interrupting Interrupts
	- A mask is used to prioritize certain interrupts over others
	- This masks blocks new interrupts until the old interrupt finishes
		- Not always the case - based on interrupt priority
	- When one interrupt completes, the old state of the mask has to be restored in order to also restore previous interrupts
- Interrupts are checked before all (FETCH/DECODE/EXECUTE) cycles
- Interrupt types
	- Precise
		- Upon an interrupt, allows the previously executed instruction to fully finish
		- The state of the program counter is known
	- Imprecise
		- Interrupts are treated immediately before any further instruction execution
		- But now, some instructions are left only partially completed