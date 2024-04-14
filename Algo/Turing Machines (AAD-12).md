Previous lecture: [[State Machines and Languages (AAD-11)]]


What is a Turing machine?
- Infinite tape of 1s and 0s
- Head/tape can move left/write as needed
- Head can read/write to the tape

Turing recognition
- Say we have a string of composure $a^{k}b^{k}c^{k}$
	- Scan right while checking if input is in form $a*b*c*$
	- Return to start, and then repeatedly override 1 a, 1 b, and 1 c until we can't any longer.
- They are more powerful than DFAs!

A Turing machine is defined as $\{Q,\Sigma, \Gamma, \delta, q_{0}, q_{\text{acc}}, c\}$
- $\Sigma$: Input alphabet
- $\Gamma$: Tape alphabet
- $\delta$: $Q \times \Gamma \rightarrow Q \times \Gamma \times \{L, R\}$
- 3 possible outputs:
	- Enter $q_{\text{acc}}$
	- Enter $q_{\text{acc}}$
	- Loop forever

A Turing machine is a **decider** if it halts on all inputs
- A language $A$ is **Turing-decidable** if it is recognized by some Turing decider
- A language $A$ is **Turing-recognizable** if it is recognized by some Turing machine (incorrect inputs may loop forever) ![[Pasted image 20240411121307.png]]

$A_{TM}$ = A language of pairs containing a string, and a machine that accepts that string
- $A_{TM}$ is not decidable, since a certain $M$ may loop forever on its $w$


Next lecture: [[Intractability (AAD-13)]]