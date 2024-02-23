## Chapter 1
#### Problem 1
False, can be disproven w the following counterexample:

| A | *X* | Y |  | X | B | *A* |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **B** | ***Y*** | **X** |  | **Y** | **A** | ***B*** |
None of the "first choices" are preferred both ways, meaning that such a combination is never possible. However, a stable matching still occurs, as italicized above. 

#### Problem 2
Assume that this "perfect match" is not chosen for a certain matching. 
This means that $m$ prefers $w$ to their chosen partner, and $w$ prefers $m$ to their chosen partner. This forms an unstable pair, proving the original statement true.

#### Problem 3
Firstly, note that the actual "time" of each slot has no impact. 
Let's say we're choosing the show for our first slot. The only way to guarantee this is by sending in the show with the absolute most ratings.

The opposing company should know they will lose this slot, and thus should match their worst-performing in this slot. 
Move to the next slot and repeat by analyzing the new highest watchtime - this is the full algorithm.
The decision to slot the overall most popular TV show, and to respond to this guaranteed loss by airing the least valuable resource, are both globally optimal, meaning the algorithm should guarantee each team their stablest winnings overall. 

#### Problem 6
Observe that n ships exists, n ports exists, and no two ships can be in the same port. 
This means that each ship will undergo maintenance in a unique port. 
We also note that we no longer have to get each ship to every port. 

Say we're deciding that ship $s$ will be repaired port $p$. If $s$ is the last ship to arrive at port $p$, this causes no conflicts. If, however, another ship $s'$ is slated to arrive at $p$ after $s$, we would have to ensure that $s'$ starts being repaired in another port before $s'$ arrives at $p$.
This shows us that we want to repair the latest possible instance of a ship docking at a port, only not choosing this instance if we instead opt for that ship to start being repaired earlier.

Thus, the proposed algorithm is as follows:
- Assign each ship their destination - currently, they are all unassigned.
- Start at the last day of the schedule. If a ship is unassigned and is in a port this day, assign that port to the ship (note - no two ships will be in the same port in the same day, meaning we will not see any conflicts here)
- Then, move "back" a day and look through all ships (that have not already been assigned a port). Two cases can arise here:
	- If a ship rests in a port that has not been assigned to any other ship, simply assign it to this ship.
	- If a ship rests in a port that has been assigned to another ship, do the following:
		- Assign that port to the new ship, and unassign it from the previous ship.
		- Then, look backwards through the previous ship's schedule, stopping when the "current time" is reached. If a port is found (assigned or not), repeat this current decision recursively. 
		- If a new port cannot be found up to the current time, leave the old port to other ship (un-assign to the new ship, re-assign to the previous ship)
			- This is because the other ship has no port to dock onto to block the use of the port on our current time bound
	- This should give the optimal solution for each subproblem?

## Chapter 2

#### Problem 1
- a: $*4$ when doubled, $+ 2n + 1$ when incremented
- b: $*8$ when doubled, $+ n^{2} + ...$ when incremented
- $*4$ when doubled, $+200n + 100$ when incremented
- 2$(logn) + 2 / logn$ when doubled, $n + 1 / n$ when incremented
- $2^n$ when doubled, $*2$ when incremented

#### Problem 4
- $2^{\sqrt{logn}}$
- $n(logn)^3$
- $n^{4/3}$
- $n^{logn}$
- $2^n$
- $2^{n^2}$
- $2^{2^n}$

#### Problem 8
- a: Move by increments of $\sqrt{n}$ - when the jar breaks, look back over the previous section in increments of 1
- b: In the square root, every subsection is the same length - this is what we would like to optimize. This can be obtained by taking steps of ${\sqrt[k]{n}^{(k-1)}}$.