Previous lecture: [[Algorithm Analysis (AAD-4)]]


Review
- Students, hospitals rank each other based on preference
- Hospital $h$ and student $s$ form an unstable pair if both:
	- $h$ prefers $s$ to one of its admitted students
	- $s$ prefers $h$ to its assigned hospital
- Input: a set of $n$ hospitals $H$ and $n$ students $S$
	- Each hospital/student is only matched once 
- A matching is **perfect** if $|M| = $
- A **stable matching** is perfect, containing no unstable pairs
	- We want to find this (if it exists)!
- An **unstable pair** $h-s$ occurs in a perfect matching if *h* prefers *s* to their assigned student, and *s* prefers *h* to their assigned hospital
	- Could be improved by joint action

~~Are unstable pairs guaranteed?~~
- ~~No, can be proven by counterexample~~
Roommates prove that stable matchings aren't guaranteed
- NOTE: they are guaranteed in the "two-sets" scenario

Gale-Shapley algorithm
- Algorithm
	- Hospitals "propose" to their first available choice
	- If a student is unmatched, they will accept that hospital
	- If a student is matched with a worse choice, they will swap into their preferred choice
		- This newly "unemployed" hospital rematches
	- If a student is matched with a better choice, the hospital moves to the next student choice
- Proof of correctness
	- **Observation 1**: Hospitals propose to students in decreasing order of preference
	- **Observation 2**: Once a student is match, it never becomes unmatched, it only "trades up"
	- **Claim**: Algorithm terminates after at most $n^2$ iterations of a while loop
		- Each iteration of the while loop, a hospital proposes to a new student. This can only be repeated max $n^2$ times.
	- **Claim**: Gale-Shapely outputs a matching
		- Hospital proposes only if unmatched $\Rightarrow$ always matched to at most 1 student
		- Student keeps only the best hospital $\Rightarrow$ always matched to at most 1 hospital
	- **Claim**: Gale-Shapely matches all hospitals
		- Assume that some hospital is not matched
		- Then, some student would also be matched 
		- The hospital would just propose to that student!
	- **Claim**: Gale-Shapely matches all students
		- See above. Since all $n$ hospitals are matched, all $n$ students are matched
	- **Claim**: In a Gale-Shapely matching $M*$, there are no unstable pairs
		- Consider any pair $h-s$ that is not in $M*$
			- Case 1: $h$ never proposed to $s$
				- Then, $h$ prefers its matched student $s'$ to $s$
			- Case 2: $h$ proposed to $s$
				- If $s$ rejects $h$ (upon proposal or later), $s$ prefers its matched hospital $h'$ to  $h$

Problem environment
- For a given problem instance, there may be several stable matchings
	- Gale-shapely will only find one of these per proposer!
- Student $s$ is a **valid partner** for hospital $h$ if there exists *any* stable matching which matches the two
	- Hospital-optimal assignment: if each hospital receives its best valid partner, we need to ensure that this matching is perfect and stable.
	- Gale-Shapely will always yield the hospital-optimal assignment
- Proof
	- **Claim:** Gale-Shapely matching $M*$ is hospital-optimal (when hospitals propose) *\[proof by contradiction]*
		- **Corollary**: Hospital-optimal assignment is a stable matching (as G-S always outputs a stable matching)
		- Assume that there exists a hospital that is not matched with its best valid partner
		- Note that hospitals propose in decreasing order of preference
		- Thus, that hospital is rejected by a valid partner during Gale-Shapely
			- This means that a student left for a hospital they liked more, or the student was already at a hospital they liked more when the hospital proposed
				- This student didn't like the hospital that much, even though the hospital liked the student
		- Let $h$ be the first such hospital (in order of execution), and let $s$ be the first valid partner that rejects $h$
		- Let $M$ be a different stable matching where $h$ and $s$ are matched (the stable matching that makes $h$ and $s$ valid partners)
		- When $s$ rejects $h$, $s$ forms or re-affirms a commitment to a different hospital $h'$
			- This means $s$ prefers $h'$ to $h$ (students only trade up)
		- Let $h'$ be matched with a student $s'$ in $M$
		- As $h$ is the first hospital that is rejected by a valid partner, $h'$ has not been rejected by any valid partner (including $s'$) when $h$ is rejected by $s$ in G-S
		- Thus, when $h'$ proposes to $s$, it has not yet proposed to/been rejected by $s'$
			- This is because $h'$, proposing to $s$, has not yet been rejected by a valid partner. Thus, everything $h$' prefers more than $s$ are invalid partners (as they rejected $h$'), and then $s'$ has to be preferred less by $h'$ to be instead proposed to after $s$.
				- ($h'$ prefers $s$ to $s'$)
			- Thus, $h'-s$ is unstable in $M$, *a contradiction*. ![[Pasted image 20240125115555.png]]
	- **Student-pessimal assignment**: each student receives its worst valid partner
	- **Claim**: G-S find the student-pessimal stable matching $M*$ *\[Proof by contradiction]*
		- Suppose $h-s$ is matched in $M*$, but $h$ is not the worst valid partner for $s$
		- There exists a stable matching $M$ where $s$  is paired with a hospital $h'$ whom $s$ prefers less than $h$
			- ($s$ prefers $h$ to $h'$)
		- Let $s'$ be the partner of $h$ in $M$
		- By hospital-optimality, $s$ is the best valid partner for $h$
			- ($h$ prefers $s$ to $s'$)
		- Thus, $h-s$ is unstable in $M$, *a contradiction*

Implementing Gale-Shapely
- ...


Next lecture: [[Graphs (AAD-6)]]