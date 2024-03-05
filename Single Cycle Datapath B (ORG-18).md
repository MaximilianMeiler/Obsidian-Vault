![[Pasted image 20240305132406.png]]

**Control unit** uses the opcode to compute a multitude of control signals
![[Pasted image 20240305132435.png]]

**ALUOp**
- 2-bit code, that, combined with the opcode, creates the 4-bit ALU control output ![[Pasted image 20240305132613.png]]

![[Pasted image 20240305132916.png]]
**Reg2Loc**
- 0: Read register num 2 comes from RM field (20-16)
	- R-type
- 1: Read register num 2 comes from Rt field (4-0)
**ALUSrc**
- 0: The second ALU operand comes from the read register 2 data
- 1: The second ALU operand is the sign-extended lower 32 bits of instruction
	- 1 when it has an immediate (usually)
**MemtoReg**
- 0: Value fed to register write input comes from ALU
- 1: Value fed to register write input comes from data memory
	- LDUR
**RegWrite**
- 0: N/A
- 1: Write data input is written onto the write register 
	- R-type, LDUR
**MemRead**
- 0: N/A
- 1: Data memory designated by an input address is put on the read data output
	- LDUR
**MemWrite**
- 0: N/A
- 1: Data memory designated by an input address is replaced by the value on the Write data input
	- STUR
**Branch**
- 0: N/A
	- 1: Sent into an AND gate with ALU output to determine branch target
	- CBZ