Previous lecture: [[Sorting (6)]]


Sets
- Collection w no duplicate elements
- Not indexed
- Do not reveal order of insertion
- Operations
	- Find
	- Insert
	- Remove
	- Set union/intersection/differences
		- Union: "or"
		- Intersection: "and"
		- Difference: A, but not B
	- Return subset
- C++
	- set: ordered (rb tree)
	- unordered_set: true set (no order, hash tables)

Maps
- Collection of key-value pairs
- No duplicate keys, but multiple keys can have the same value
- C++
	- map: ordered (rb tree)
	- unordered map (hash map)
	- Operations
		- Insert
		- \[]
		- erase
		- find
		- count
		- size
		- empty
		- (unordered) bucket_size
		- (unordered) load_factor

Hash tables
- Tree-based structures make sense only if datatypes are comparable - what if they aren't?
	- We also want to improve the complexity of nlogn insert/search functions
- Say we want to make an unordered_set - create a 2billion long array initialized to false
	- When an element is inserted, set the value at that index to "True"
- What if we want to store other data types, not just numbers?
	- Somehow convert that data type into an index
	- Multiply all digit vals by a power of 27
		- ex. "cat" -> (3 \* 27^2) + (1 \* 27^1) + (20 \* 27^0) = 2234
		- Make sure to 1-index 
		- As long as all conversions are under 27, we will get NO COLLISIONS
	- Wrangling collisions
		- After hashing, reduce the function output into something that fits in the memory table
		- This may mean different values access the same element in the table
		- Good hash functions should:
			- Evenly distribute data
			- Be easy to compute
	- Collision Resolution
		- Buckets
			- Number of slots in the hash table structure
			- Load factor (alpha): number of entries in the table / number of buckets
			- Maximum load factor: arbitrary threshold. When reached, rehash into a table with more buckets to reduce collision chance
				- Hash function doesn't change upon rehash, only insertion mod
		- Separate chaining (open hashing)
			- Object is stored outside the table
			- Fixed, Resizable
			- Each bucket store a linked list, collisions (any insertion) append to the list
			- When finding an element, iterate thru the linked list at a corresponding hash
		- Open addressing (closed chaining)
			- Object is stored within the table
			- Linear probing
				- When a collision occurs, move the probe linearly until a free slot is found
				- When searching for an element:
					- Check slot status (never used / deleted / occupied)
						- Never used - that element was never inserted, don't check further
			- Quadratic probing
				- Move the probe quadratically (1->4->9->16)
					- This avoids clusters in the hash table
- Performance
	- O(1) on average
	- O(alpha) ~ O(n) in worst case (rehashes!)
		- n ~= m because of max load factor, and alpha = n/m