Previous lecture: N/A


A **set** $\{\}$ is a collection of things where order does not matter

Notation
- **Inclusion**: $a \in A$, where $A = \{a, b, c\}$
- **Subset**: $A \subseteq B$ if any element of $A$ is also in $B$ ($a \in A \Rightarrow a \in B$)
- The **empty set** $\emptyset$ contains nothing, $\{\}$
	- $\emptyset$  is a subset of any set!
- **Union**: $A \cup B = \{a$ in $A$ or $B\}$
- **Intersection** $A \cap B = \{a$ in $A$ and $B\}$
- Let $S$ be the set known as the **universal set**, or **sample space**
	- This set contains everything possible for a circumstance
	- **Events** are subsets of this set $S$
- The **complement** of a set $A' = \{s \in S, s \notin A\}$
- $A$ and $B$ are **disjoint** or **mutually exclusive** if $A \cap B = \emptyset$
- $B \setminus A$: $B$ with the points in $A$ removed
- **Cardinality** $|S|$: The number of elements in a set $S$
- $\mathcal{A}$: The set containing all possible subsets of $S$ ($A \subseteq S \Leftrightarrow A \in \mathcal{A}$)

Logical equivalencies
- De Morgan's Law: $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$
	- $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
- $(A \cup B)' = A'\cap B'$

Probabilities
- Conditions
	- The probability $P(A)$ of an event $A \in [0,1]$
	- $P(S) = 1$
	- If $A_{1}, A_{2},...$ are mutually exclusive, $P(\cup_{1}^{\infty}A_{i}) = \sum_{1}^{\infty}P(A_{i})$ 
- Rules
	- If all outcomes have the same probability, $P(A) = \frac{|A|}{|S|}$
	- Independent probabilities can be multiplied together