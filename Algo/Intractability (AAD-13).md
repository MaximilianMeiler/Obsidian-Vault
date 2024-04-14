Previous lecture: [[Turing Machines (AAD-12)]]


**P**
	- Say we have a language $X$, and one string $s$ from it
	- Say we have a machine $A$ that recognizes $X$
- $A$ will terminate in at most $p(|s|)$ steps, where $p$ is a polynomial function
- $P$ is the set of decision problems for which a poly-time algo exists

**NP**
- Set of decision problems for which an algorithm can be proven to have output correctly in polynomial time
	- There exists a **certifier** where for every string $s$, there exists a string $t$ (answer) where $C(s, t) = \text{yes}$
	- 