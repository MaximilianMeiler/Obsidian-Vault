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