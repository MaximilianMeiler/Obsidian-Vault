Previous lecture: N/A


Measuring performance
- Performance: how fast a computer is
- Response/Execution time: seconds it take to run a program
- Throughput/Bandwith: tasks per time (instructions / seconds)
Improving performance
- Decreasing execution time
- Increase the throughput (do more things per unit of time)
Comparing performance
- Relative performance: Performance(A) /  Performance(B)
	- == ExecutionTime(B) / ExecutionTime(A)
	- Called "Speedup"
		- Do not use percentage units!

Computer clocks
- Computers are run by cyclical clocks that vary between 1 and 0
- For every clock cycle, a instruction is fed through a process
- Thus, execution time is based on the length of a clock cycle
- Cycle time - period of the clock, measured in seconds
- Clock rate - inverse of cycle time, measured in Hz

Unit break
- MHz - 10^6
- GHz - 10^9

CPU equation
- t(exe) = IC x CPI x Cycle time
	- IC: Instruction count of a program
	- CPI: cycles per instruction
		- To get average CPI, just take a weighted average
- Total units : seconds/program!

Amdahl's law for improving computers
- 1 / (1 - fractionEnhanced) + (fractionEnhanced / factorOfImprovement)
- Used to compute efficacy of parallelization



Next lecture: [[Bits, Binary, Digital Logic (ORG-2)]]