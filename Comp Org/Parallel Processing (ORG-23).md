Previous lecture: [[Cache Coherence (ORG-22)]]


Static multiple issue
- We use 2 separate pipelines - one for LDUR/STUR and one for R-type CBZ
	- Blue and black ![[Pasted image 20240412173629.png]]
- We try to put 2 instructions into these two pipelines that do not depend on the output of each other!

With hazards
- We can re-arrange instructions that can't be bunched together
- Stalls unfortunately have to be applied to an entire packet

Dynamic multiple issue
- Processor chooses which instructions to run during execution
- Runs through chunks of different instruction types at a time

Parallel Processing 
- A single program running on multiple processors at once
- Amdahl's Law ![[Pasted image 20240412174629.png]]

Taxonomy
- Instructions streams can be just one or multiple (SI/MI)
- Data streams can also be just one or multiple (SD/MD)
	- SIMD: **Vector processing**: One instruction is performed on a whole vector of values
	- MISD: Many programs running on the same data - no processors do this, maybe fault tolerance?
	- MIMD: Multiple processes on different data (cluster computing, threading)

Shared memory processing
- Uniform Memory Access: each processor takes its own data stream
- Non-Uniform Memory Access: idk

Multi-threading
- Performing multiple execution threads in parallel, swapping between them is fast
- Each process has several threads, each with their own state and registers but sharing memory
- **Fine-grain**: Switch threads after each cycle, interleaving instruction execution
	- Other threads can execute even if one stalls
- **Course-grain**: Only switch on long stall, doesn't stop short stalls
- **Simultaneous**: Schedules instructions from multiple threads
	- Can run across threads in one cycle