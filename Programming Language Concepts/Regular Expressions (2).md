Previous lecture: [[Object-Oriented Programming (1)]]


- Used to specify specific sets of strings

Definitions
- **Atom**:  an element of a finite alphabet $\Sigma$
	- $\epsilon$: the set containing the empty string `""`
- **Concatenation**: Two or more adjacent regular expressions
- **Disjunction**: The union (or) of two REs separated by `|`
	- `(a|b)c` - set containing "ab" and "ac"
- **Kleene Closure**: A `*` indicates 0 or more instances of the RE preceding it
- **Positive Closure**: A `+` indicates 0 or more instances of the RE preceding it
- **Blocking**
	- `()`: blocks off, or groups, an RE
	- `[]`: Match on *one or more* of the REs inside
	- `{n}`: Denotes n occurrences of the previous RE
	- `{n,}`: Denotes n+ occurrences of the previous RE
	- `{m,n}`: Denotes at least m, and at most n, of the previous RE
	- `[a-d]`: Denotes the alphabetic (ASCII) range from `a` through `d`
	- `[1-3]`: Denotes the numeric range from 1 to 3
- **Metasymbols** ![[Pasted image 20240904164814.png]]
	- Use `\` to escape these metasymbols
- **Escaping** ![[Pasted image 20240904165240.png]]


Next lecture: [[Testing (3)]]