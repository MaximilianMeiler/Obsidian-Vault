Previous lecture: N/A


Components of a computer
- Input
- Output
- CPU/GPU
- Memory (RAM)
- Storage (Hard Drive, I/O)

Typical PC architecture
- A **bus** connects together all parts of the PC for data transfer
- **Controller**: Hardware/software that manages dataflow between two entities (video, usb, fixed storage)

CPU architecture
- Parts of the CPU
	- Processor/CPU **registers**: small but fast memory units for instructions, addresses, variables
	- **ALU**: Carries out arithmetic + logic operations in the instructions
	- **Control unit**: Takes instructions from main memory, interprets them by activating other system elements
- Instructions are executed through the fetch/decode/execute cycle
	- Fetch: Instructions are loaded from the Memory Address/Buffer Register and placed into Instruction Register, Program Counter is incremented
	- Decode: Opcode and instruction data is interpreted
- **Protected instructions** can only be accessed in a protected kernel mode, not a user mode
- **Pipelining** speeds up instructions by allowing each stage of execution to always be busy with separate instructions
	- **Superscalar** CPUs have multiple units for each stage of the cycle, with buffers to account for execution inefficiencies
- Access times:![[Pasted image 20250116174005.png]]
	- Registers are in the CPU, Caches are near it, the rest are only connected with a bus

Memory Units
- $10^{3}$ -> $10^6$ -> $10^9$, etc
- $2^{10}$ -> $2^{20}$ -> $2^{30}$, etc
- Kilo, mega, giga, tera, peta
 
The Boot Process
- **BIOS**: Binary Input/Output system. Performs an initialization process.
	- Runs a POST (power-on self test) check to ensure basic components exist
	- Looks for the boot device (hard drive containing OS), which is stored in an NV(non-volatile)RAM 
	- The boot disk is then read into the main memory in a section called the "boot sector"
	- From there, the "boot block" program is run, which calls the OS boot loader
- With multiple OSs, the boot sector, now known as the "master boot record", allows users to select an OS when run
	- Then, the corresponding first section of that OS's memory partition is run, executing the boot block program
- New systems instead have a **UEFI** (Universal Extensible Firmware Interface)
	- Standardized, allowing the OS to control stuff like disk partitioning / boot disks
	- Process
		- Verifies hardware
		- Runs an EFI manager, which looks for the boot device (disk containing the OS) stored in NVRAM
		- The EFI partition of that disk is accessed, calling the OS bootloader
	- Storage
		- First sector is protected to ensure recognition of BIOS disks
		- Second sector, or the **Primary Header**, contains basic disk info. The following partitions are:
			- Partition Entities: Partition containing metadata about each partition on the disk
			- EFI partition: Partition containing bootloaders for each different OS on the disk
			- Copies of the partition entries / primary header!
- ARM (Advanced RISC machine) doesn't have a UEFI-like system


Next lecture: [[Introduction to Operating Systems (2)]]