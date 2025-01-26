Previous lecture: [[Defining Complexities (1)]]


Say we have n records, which together take up a lot of space
- We have a limited main memory and a more expansive disk
	- HDD seek time = 100k operations
	- HDD latency time = 25k operations
	- ALU interfaces with the main memory
	- -> In order to maximize caching efficiency, we should perform operations on previously calculated or subsequent data wherever we can
- It's not feasible to input all at once and sort them
- Case 1 - small n, large files
	- Read in the keys (which are sorted upon), and sort those
- Case 2 - large n
	- Adapted quick sort (optimize for average case)
		- Memory is split into 3 buffers (input, small, large), each of size 1 block
			- Remaining memory stores the middle group
		- Middle group and input buffer are fully filled from disk
		- Iterate from input
			- If the next record is smaller than the *min* of the middle group, move it to the small group
			- If the next record is greater than the *max* of the middle group, move it to the large group
			- If neither above case holds, replace either the middle's min or max value with the new value. Move that old value into the small/large group
		- Fill the input buffer from disk when it gets empty
		- Write the small/large buffer into the disk when it gets full
		- When done, sort the middle group and write it to the disk
		- Then, recur on the small and large groups that sit on the disk
	- Adapted merge sort (optimize for worst case)
		- Let $t_{IO}$ be the time to input/output one block, $t_{IS}$ the time to internally sort one memory load, and $t_{IM}$ to internally merge one block of data
		- Phase 1: Run generation
			- Input all the blocks you can into main memory, sort, and output
			- Repeat for all data on the disk
			- Improvements
				- Use 2 disks to overlap input, output, and sorting computations
				- Generation of larger runs, which exceed capacity of main memory
		- Phase 2: Run merging
			- Split the memory into 3 buffers (input 0, input 1, output), each of size 1 block
			- Fill Input 0 from your first array to merge, and Input 1 from your second
			- Merge from I0 and I1 to the output buffer
			- If an input buffer becomes empty, read more array data in. If the output becomes full, write it to the disk
			- Higher-order merging
				- With a fixed memory, decrease block size to increase order
				- Naïve comparing takes order-1 comparisons per merge into the output buffer
				- Using a tournament tree allows for log(order) comparisons instead


Next lecture: [[Tournament Trees (3)]]