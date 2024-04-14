Previous lecture: [[Network Flow (AAD-10)]]


Finite automata & languages
- Inputs a finite string, outputs either *accept* or *reject* 
	- This machine accepts any binary string with 2 consecutive 1s ![[Pasted image 20240402105045.png]]
		- $A = \{ w | w \text{ contains substring } 11\}$
			- $A$ is the **language** of $M_1$, $M_1$ recognizes $A$, and $A$ = $L(M_1)$ 
- A finite automaton $M$ is an 5-tuple $(Q, \Sigma, \delta, q_{0}, F)$
	- $Q$: finite set of states
	- $\Sigma$: finite set of alphabet symbols
	- $\delta$: transition function ($\delta = Q \times E \rightarrow Q$)
	- $q_0$: start state
	- $F$: set of accept states
- A **language** is a finite or infinite set of strings
	- The **empty language** $\varnothing$ is the set with no strings
	- A language is **regular** if some finite automaton recognizes it
		- Ex. language where all strings have equal amounts of 0s and 1s

Regular operations
- **Union**: $A \cup B$: $\{w | w \in A \text{ or } w \in B\}$
- **Concatenation**: $A \cdot B$ = $\{xy | x \in A \text{ and } y \in B\} = AB$
- $A*$ = $\{x_1 ... x_{k}| \text{ each } x_{i}\in A \text{ for } k \geq 0\}$
	- $\epsilon$ (the empty string) is always in $A*$
- ex. $\Sigma*11\Sigma*$ - all strings that contain 11
- Finite automata are equal to these!
- A **regular expression** is built from operations on variables
	- Atomics - $\Sigma,  \varnothing, \epsilon$
	- Composites - $\cup, \cdot, *$

"A set of strings is regular iff it can be represented as a regular expression"
- **Theorem**: If $A_{1}, A_2$ are regular languages, so is $A_{1} \cup A_2$
	- Let $M_{1}$ recognize $A_{1}$, and $M_{2}$ recognize $A_{2}$
	- $M$, which recognizes $A_{1} \cup A_{2}$, is built as follows:
		- $Q = Q_{1} \times Q_2$
		- $\Sigma$ is constant across all 3 machines
		- $\delta((r_{1},r_{2),}a) = (\delta_{1}(r_{1}, a), \delta_{2}(r_{2}, a))$
		- $q = (q_{1}, q_{2})$
		- $F = F_{1} \times Q_{2} \cup Q_{1} \times F_{2}$
- **Theorem**: If $A_{1}, A_{2}$ are regular languages, so is $A_{1}A_{2}$
	- Let $M_{1}$ recognize $A_{1}$, and $M_{2}$ recognize $A_{2}$
	- **Nondeterminism**: At any point, a single character can branch off into multiple states. 
		- $\epsilon$: Can travel this path whenever, without reading input
		- Multiple paths possible
			- Accept an input if some path leads to an accept state
		- New $\delta: Q \times \Sigma_{\epsilon} \rightarrow P(Q) = \{R | R \subseteq Q\}$
		- This isn't actually necessary for anything - it just shows the ability to try every single possible path
			- **Theorem**: If NFA recognizes $A$ then $A$ is regular
				- DFA $M'$ keeps track of the subset of possible states in NFA $M$
					- $Q' = P(Q)$
					- $\delta'(R, a) = \{q | q \in \delta(r, a) \text{ for some } r \in R\}$
						- $R \in  Q'$
					- $q'_{0}= \{q_0\}$
					- $F' = \{R \in Q' | R \text{ intersects } F\}$
	- Use an NFA: At every state in $F_1$, add an $\epsilon$-edge to $q_2$
	- If we end at an $F_2$ state, we accept the new string!
- Reproving union:
	- Let NFA $M$ recognize $A_{1}\cup A_{2}$
	- NFA's start state just has $\epsilon$ edges to $q_1$ and $q_2$
- **Theorem**: If $A$ is a regular language, so is $A*$
	- NFA $M'$ recognizes $A*$
		- New starting state, that is an accepted state
		- All accepted states (including the new starting state) have an $\epsilon$-edge to the old start state
- **Theorem**: If $R$ is a regular expression and $A = L(R)$, $A$ is regular
	- Convert $R$ to an equivalent NFA $M$: ![[Pasted image 20240404122728.png]]
	- This can then be converted to a DFA $M'$
- **Theorem**: If $A$ is regular, $A= L(R)$ for some regular expression $R$
	- Generalized NFAs
		- Allows reg expressions as transition labels
		- Can be converted into NFAs easily - just convert reg exp labels into machine parts using the rules above
		- Assume one accept state ($\epsilon$-ed from all other accepts) and full connections
			- One accept state is just made by $\epsilon$-ing together the old end states
			- Use $\varnothing$ if no connection otherwise possible
			- BUT, not everything has to go into the start state, or into the new sink
		- **Lemma**: Every GNFA $G$ has an equivalent regular expression $R$ *\[Proof by induction on the number of states $k$ in $G$]
			- Start with $k = 2$
				- ![[Pasted image 20240409111022.png]]
				- $R = r$
			- Inductive state: Assume lemma true for $k-1$ states, prove for $k$ states
				- How do we reduce a $k$-state machine into a $k-1$-state machine?
					- Pick any state $x$ except the start and accept states
					- Remove $x$
					- Recover all states that went through $x$ by merging together all possible regular expressions on edges ![[Pasted image 20240409111841.png]]
				- It's evident that we can begin at the start state with the entire regular expression, and then slowly break it up into "machine form" until fully expanded

Non-Regular Languages
- **Pumping Lemma**: If a language $A$ is regular, every long string in $A$ ($\geq$ than the "pumping length" $p$) can be simplified to a form $xyz$,  where $y$ is just part of a loop in the machine and can thus be repeated any number of times ![[Pasted image 20240411111419.png]]
- How to disprove the regularity of a language
	- Assume a language is regular, and the pumping lemma applies
	- Find a string with a length $\geq p$, which, when "pumped" (y repeated), is not recognized by the machine
		- Ex. machine that recognizes $0^{k}1^{k}$
			- Choose the string $0^{p}1^{p}$
			- By condition 3 of the lemma, $y$ would consist of all 0s
			- By pumping any y, the new string is not recognized by the original machine
		- Ex. machine that recognizes $ww$
			- Choose the string $0^{p}10^{p}1$
	- We can also combine the pumping lemma with closure properties!
		- Ex. machine that recognizes an equal number of 0s and 1s ($B$)
		- Assume 0\*1\* is regular, we can further assume $B \text{ }\cap$ 0\*1\* is regular
			- In this case, $B \text{ }\cap$ 0\*1\* = $0^{k}1^{k}$ would also be regular


Next lecture: [[Turing Machines (AAD-12)]]