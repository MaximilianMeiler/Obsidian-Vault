
Hash functions map data into buckets based on keys

Key mod table size
- Hash value is equal to a key % bucket count / table size

Load factor
- n / k (num of elements / table size)

Collision resolution
- Open addressing
	- Linear probing
		- When you encounter a collision, move hashes forward linearly until a free slot is town
	- Quadratic probing
		- When you encounter a collision, move hashes forward quadratically until a free slot is town
- Separate chaining

Time complexity
- Average - O(1)
- Worst - O(n) if rehashing is needed

C++ maps
- Maps are red black trees, but unordered_maps are true maps

C++ sets
- Sets are red black trees, unordered_sets are hash tables
- No duplicate elements
- Properties
	- Non-indexed
	- No inherent ordering