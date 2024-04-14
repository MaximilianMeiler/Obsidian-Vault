## Chapter 7

#### Problem 14
$a)$
Let's look at this in terms of a max-flow problem. We're trying to direct units from our populated $X$-nodes to our safe $S$-nodes. Essentially, if we connect a source to all $X$-nodes, and a sink to all $S$-nodes, we can create paths flowing from one group of nodes to the other. However, there are some extra considerations to make, as follows:
- As all edges in the graph can only be used once, give them all an edge weight of 1. We want them guaranteed to be "full" after the bottleneck is applied.
- As each $X$ only needs 1 escape route, give the edges connecting the source to the $X$-nodes a weight of 1 as well
- Because multiple paths can end up at the same safe node, give all edges connecting $S$-nodes to the sink a weight of $\infty$.
After we run max-flow, we can see if the flow is equal to the number of $X$-nodes. If so, an evacuation plan exists!

$b)$
- Set the safe nodes to connect to the sink with edge weights of 1.
- Perhaps visiting a node would bottle all of its outgoing edges instead of just the one that is taken? That way, the only way to repeatedly access that node is to undo the previous path through the node...

**Correct answer:** ![[Pasted image 20240412105324.png]]
Split each node in 2 with effectively one edge "in" that node - this ensures this edge is only taken once!
## Algorithm Problems

#### 1.1
- a: $q_1$
- b: $q_2$, $q_{1}, q_4$
- c: $q_1 \rightarrow q_{2}\rightarrow q_{3} \rightarrow q_{1} \rightarrow q_{1}$, $q_{1} \rightarrow  q_{1} \rightarrow q_{1} \rightarrow q_{2} \rightarrow q_4$
- No, Yes
- No, Yes

#### 1.2
- ~~M1: Recognizes any string that ends in an odd number of "a"s~~
Apparently this is just the boring stuff. Skip.

#### 1.4
![[Pasted image 20240412103208.png]]

#### 1.11
Just draw an $\epsilon$-edge from all current accept states to a sole accept state 
- As the universal accept state has no outgoing edges, this $\epsilon$ edge would only be taken at the end of a string - where accepting would normally occur!

#### 1.15
This is just bonus problem 5: ![[Pasted image 20240412103853.png]]

#### 1.29
- a: $0^{p}1^{p}2^{p}$
	- y would have to be all 0s, pumping it would break the $n$-equivalence
- b: $a^{p}ba^{p}ba^{p}b$
	- y would have to be all 'a's, pumping it would break $w$-equality
- c: $a^{\text{any power of 2 > p}}$
	- Notice that the number of 'a's has to be a power of 2
	- If string length is greater than p, our y can't be the entire string. If we take a power of 2 and increase it by anything less than double, it's no longer a power of 2! Thus, pumping y once will not result in a power of 2 length.