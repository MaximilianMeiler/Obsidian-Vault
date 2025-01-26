Previous lecture: [[Introduction to Operating Systems (2)]]



File systems
- Define how data is stored
- Have mounting schemes
- Naming, redundancy, directories
- Passes system calls to the OS to read from the disk

Processes 
- Running a program creates a process for it in main memory
- The OS scheduler then moves the processes to the CPU for execution
- Processes are organized in trees, with multiple children and threads of execution
	- Threads are used to save memory when multiple processes execute the same insructions 

Procedure calls
- Procedures have local variables, parameters (passed by value, reference, or name), and a return pointer
- ![[Pasted image 20250121180115.png]]
	- The heap contains static and dynamic data and grows upward
	- The stack contains activation frames of calls (recursion!)
		- A frame pointer records the top address of a current stack frame, and a stack pointer records the bottom

System Calls
- Named calls containing a context switch into kernel mode for execution
- Called by the routines implemented by system library entry points
	- Stores parameters and a call number in set spaces
	- Then, the procedure issues a kernel trap
	- Kernel dispatcher looks up the system call number in a vector table to find a pointer to the handler code that carries out the call
	- Then, the system returns execution results and swaps back to user mode
- Examples (POSIX standard)
	- Process management
		- fork() - creates a child process identical to parent
		- exit() - terminates a process
		- kill() - instantly end a process (do not allow it to run termination code)
	- File operations
		- open(), close(), read(), write()
		- lseek() - moves the file pointer 


Next lecture: [[Interrupts (4)]]