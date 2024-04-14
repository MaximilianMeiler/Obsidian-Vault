Previous lecture: [[Virtual Memory (ORG-21)]]


Each core has its own L1 cache
- Multiple L1 caches may have copies of the same block 
- **Coherence**: All caches must stay up to date with each other
	- Writes to the same location are serialized, meaning two writes to the same location are seen in the same order by all processors

MSI protocol
- 3 flags are added to each line of an L1 cache: ![[Pasted image 20240408174749.png]]
	- M - this core has written to its copy
	- I - the cache contains an old copy of the value 
	- S - the block is unmodified
- A bus shared across L1 caches **snoops** to see if any memory address is read/write by any cache


Next lecture: [[Parallel Processing (ORG-23)]]