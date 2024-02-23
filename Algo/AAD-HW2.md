## Chapter 3
#### Problem 2
DFS from all nodes, keeping track if they are visited or not. If a node is already visited and attempts to be visited again (by a node of which it is not a "dfs parent"), we know this forms a cycle. Here, we can just store the dfs parent of each node, and work backwards from the offender to the offendee to find the nodes in the cycle.

#### Problem 4
This is a graph coloring problem - start at a node, color nodes according to the initial node based on its same/diff edges, move to one of these nodes, try coloring each node adjacent, repeat until either all nodes have been visited (valid), or we try to color a node a different color from which it has already been assigned (invalid)

#### Problem 5
- Base case: 1 layer - 0 nodes with 2 children, 1 leaf
- NOTE: 
- Inductive hypothesis: Assume any binary tree (????) has 1 more leaf than number of nodes w 2 children
- Inductive step: What does adding one node do? It either be added to a leaf or a half-full tree.
	- Adding to a leaf keeps number of leaves and number of double-child nodes constant
	- Adding to a half-full node adds a leaf, but also adds another node with 2 children
- Thus, in both cases, this +1 dynamic is maintained :)

#### Problem 6
The BFS tree and DFS tree will differ if there are cycles, as these would allow the DFS to travel "backwards" in terms of distance from the source. 
Additionally, BFS trees and DFS trees do not contain any cycles. Thus, if both trees are the same, G must share the no-cycle property of the BFS/DFS trees, and thus appear the same as them.

#### Problem 7
The only counterexample I can think of is splitting the n nodes into equal groups of 2. Even then, each node in these groups would be connected to n/2 - 1 nodes, which would not satisfy the requirement. Thus (very solid proof, I know), the system will always be connected

## Chapter 4
#### Problem 3
- Assume a greedy algorithm A and a supposedly-otherwise-optimal algorithm B
- At a certain point, B will choose not to load a box into a truck, which A does choose to load
- In the next truck, B will have to load this box as well. This means that every box they further load into that truck, A could also load (since their truck has even more space!). Thus, B will never be able to pack a box A has not packed, and thus cannot save trucks.

#### Problem 5
For the first house, place the first station 4 miles in front (as far ahead as possible).
Then, look for the first house that is not covered by this station and repeat.

#### Problem 6
Let's clump biking and running times together, as they don't effectively have any difference. 
Notice that the amount of time spent in the pool is always constant (the sum of all swimming times), as only one person can be in the pool at once.
Thus, we just sort by biking+running times greatest first, and let these people contend first. This means that those who would normally take the longest time to finish biking and running get to start earlier, thus reducing their potential overall bottleneck.

## Chapter 4 extra problems
### Does Dijkstra's still work if...
#### Edges have negative weight?
A negative cycle could cause an effective infinite negative weight optimally, which would cause the algorithm to run infinitely or not output the correct result.
#### Edges have negative weight, with no negative cycles?
This depends on implementation. A simple "relax-all-edges" approach wouldn't work, since certain edges would have to be re-relaxed. However, I think a smart priority-queue implementation would still work.
#### Edges have weight 0?
The proof in class operated on $\geq$, so it should still work?
Somehow I feel like it should still work - edges of 0 can effectively just be ignored and don't stack with themselves into infinity.
