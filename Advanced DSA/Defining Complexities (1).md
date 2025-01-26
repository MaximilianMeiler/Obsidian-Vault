Previous lecture: N/A


Worst-case complexity alone doesn't tell us about the speed of operations when they are run multiple times over (may be too pessimistic)
- We can't use the average complexity to conclude the worst-case time needed to perform a series of operations, either (may be too optimistic)
- Amortized complexity is the amount you charge a task
	- Doing a task n times is better bounded by n*(amortized complexity)
	- This complexity may be smaller than the cost of an individual task, but is always an upper bound for a sequence of tasks
- Determining amortized complexities
	- We need to ensure that $\sum{\text{actual costs}} \leq \sum{\text{amortized cost}}$
	- Aggregate method: Get a good upper bound for $n$ operations, then divide by $n$
	- Define **potential** as amortized cost - actual cost at any point
		- Accounting method: Guesses the amortized cost, checks if potential is $\geq 0$ at end
		- Potential method: Guess a suitable potential function for which $P(n) - P(0) \geq 0$ for all $n$, then derive amortized cost of $i$th operation ($= \text{actual cost} + \Delta P$)


Next lecture: [[External Sorting (2)]]