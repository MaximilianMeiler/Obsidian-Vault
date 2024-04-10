Previous lecture: [[Cache Memory (ORG-20)]]

Virtual Memory
- Makes main memory appear larger
- Programs use a logical address space
	- Logical address space is partitioned into pages
	- Physical memory is partitioned into frames, of same size as pages
	- Addresses used by a program map to pages
		- Some pages map to the disk, some to the main memory
	- Each active process has its own page table
		- A valid bit stores if a virtual address is in memory, and the page entry table indicates which frame contains the page

Address translation
- A virtual address is composed of a page number and offset
- ![[Pasted image 20240405173828.png]]
- ![[Pasted image 20240405173908.png]]

Cache use
- Recent translation can be saved in the cache
	- Translation look-aside buffer used (TLB)
- Fully associative cache
- Hit provides frame number immediately
	- Combine with offset to get the main memory address
- Updated on event of a miss

OS
- OS ensures that frames are assigned exclusively


![[Pasted image 20240408173234.png]]
![[Pasted image 20240408173236.png]]


Next lecture: [[Cache Coherence (ORG-22)]]