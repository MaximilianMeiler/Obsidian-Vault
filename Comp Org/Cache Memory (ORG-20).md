Previous lecture: [[Pipelining (ORG-19)]]


Introduction
- Instructions operate on registers
	- Caches are between registers and memory, where most frequently used data can be placed for faster access

Locality
- Spatial locality: Instructions are near each other in memory because they are accessed sequentially
	- Data is fetched in blocks, w related memory in the same block
	- Arrays are also stored together in memory
- Temporal locality: Reuse of data previously used

Types
- L1: Primary, on the chip with the registers/cpu
- L2: Secondary, may be separate, larger and slower
	- Multicores share one L2 chip, with unique L1s for each
- Harvard cache: Splits I-type and D-type instructions (often for L1)

Use:
1. Blocks containing desired items are put in the cache
2. ???

Cache writing
- Write through
	- Memory is updated in parallel for every write
	- Defeats the purpose of having cache
- Write back
	- Updates only the cached copy of the item
	- Update main memory when the item is removed is removed from the cache
	- May cause issues with concurrent access
- Cache hit - look for a byte, find it in the cache
	- Hit rate: % of references found at a memory level
	- Hit ratio: \#hits / \#references
	- Hit time: Time needed to access data at a memory level
	- Miss penalty: Time required to process a miss

Lookaside cache
- Accesses both cache and main memory
- Cancels main memory access if cache hit occurs
- ![[Pasted image 20240327145340.png]]

Lookthrough cache
- Checks cache, then main memory if no hit
- Slower!
- ![[Pasted image 20240327145424.png]]

Misses
- Compulsory: Unavoidable due to initially empty cache
- Capacity: Due to limited cache size
- Conflict: Due to different blocks mapping to the same cache line

Cache organization methods
- Fully associative
	- Any mem block can go into any cache line
	- All lines are checked for hits/misses
	- Each line stores a bit to determine if it is occupied or not
		- A new line is written in the event of a miss
			- Lines are replaced if all are full on a miss
	- Example: ![[Pasted image 20240327173724.png]]
- Set associative
	- 
- Direct mapped
	- Block B of memory maps to line BmodN (N = lines of cache, B = block num)
	- Address setup
		- Offset: location within line - width: log(line size)
		- Line: line of cache - width: log(num lines)
		- tag: leftover
	- ![[Pasted image 20240327175819.png]]
		- Line: block in cache to write over
- .
	- Block number: Address / Block size
	- Number of bits in offset: log(Block size)
	- ![[Pasted image 20240327172646.png]]
		- Bottom 8 bits - "E8": offset in block
		- Top 24 bits - "0400AC": block number
	- Number of blocks = memory size / block size
	- Number of lines = cache size / block size
		- Line size is equal to memory block size
	- Associativity: number of blocks in a set
	- ![[Pasted image 20240329172232.png]]
- Set associative (compromise between the two)
	- Multiple blocks are placed into sets
	- Addresses are divided into tag, set, and offset
		- Offset width: log(block size)
		- Set width: log(num sets)
	- Blocks can be loaded into any vacant line in the set, replacements occur if the set is full (usually LRU)
	- ![[Pasted image 20240329174050.png]]
	- ![[Pasted image 20240329174353.png]]


Next lecture: [[Virtual Memory (ORG-21)]]