Previous lecture: [[Lexical Analysis (4)]]


Parsing constructs Abstract Syntax Trees by using a CFG to recognize legal phrases
	- We don't use regular expressions, because they aren't recursive and thus can't recognize nested constructions (`(x+y) + (a+b)`)

BNF (Backus-Naur Form) allows us to specify Context-Free Grammars

A grammar is a tuple where:
- $\Sigma$ is the set specifying the alphabet of tokens / terminal symbols
- $N$ is the set of non-terminal symbols
	- These are variables that impose a hierarchy of sentence sets
- $P$ is a set of productions (substitution rules)
- $S$ is the start symbol (in $N$)

Parsing
- Parse trees are a way of representing the structure of a sentence
- We will focus on top-down parsing:
	- Begin with the start symbol in the language
	- At each step, replace a non-terminal symbol with one of its productions, trying to match prefixes in the sentence
	- Remove matching prefixes
	- If the resulting string is empty, then the resulting sentence is in the grammar
- Example
	- `S ::= AB`
	- `A ::= x | y`
	- `B ::= z | w`
	- Parsing `zw`
		- `S -> AB -> xB -> B -> w -> empty`


Next lecture: [[Parsing (6)]]