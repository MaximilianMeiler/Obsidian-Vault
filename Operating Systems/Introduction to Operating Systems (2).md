Previous lecture: [[Computer Hardware Fundamentals (1)]]


Terminology
- **Algorithm**: Set of instructions with an initial state, a starting point, and an ordering
- **Program**: The sequence of instructions that embody the algorithm. Can be source / machine code
- **Process**: A program in execution plus its processing state (current instruction, state of memory)
- **Job**: A task, such as a program, to be completed

Why OS
- The OS helps with repetitive/complex tasks. Loading a program requires loading memory into registers
- The OS also grants a uniform interface for the usage of I/O devices
- The OS restricts access to certain read/write routines for user safety
- The OS manages resources and information between multiple programs

Note: an OS is not a user interface! Instead, it connects the hardware and the user interface!

OS's Jobs
- Resource Manager
	- Process manager: Multiple programs are actually run in an alternating sequence, giving the illusion of parallel execution. The OS must define what programs should next be executed and their timing
	- Memory manager: Decides what programs to load into main memory, which to keep on storage
	- I/O device: Communicates between I/O and programs
- Extended Machine
	- Abstracts file management for the user!
- NOT a user interface, system tools (dev tools), or libraries

OS types
- Interactive: Used by us, prioritize user response time
- Batch: Prioritizes large sets of tasks/jobs, deprioritizes user input
- Real Time: Has well-defined task priorities (airplanes, cars)

OS generations
- Gen 1: Vacuum tubes, Plugboards (1945-55)
	- Unreliable wiring programming and vacuum tubes
		- Punchcards later replace plugboards
	- Combined programmer and operator
	- No OS - ran one application at once
- Gen 2: Transistors, Batch Systems (55-65)
	- Transistors were much faster and more reliable than vacuum tubes
	- Sequence of programs, or **batches**, were managed by an OS
	- Programmers and operators became defined
	- Tapes were used for storage
	- Subgenerations
		- 2A (Uniprogrammed) - One program is ran at any time. Sequential programs led to a lot of idle cpu time
		- 2B (Multiprogrammed) - Multiple programs run at once, meaning while one is writing, another can be executed and another read
			- No user interaction within a batch
- Gen 3: Ics, Multiprogramming (65-80)
	- Integrated Circuits make things faster and smaller
	- The operator disappeared
	- Terminals are used for development
	- Timesharing: connecting multiple terminals to one powerful mainframe, processing each sequentially


Next lecture: [[Named Calls (3)]]