	`
function Dijkstra(Graph, source):
   // Initialize distances to all nodes as infinity, except for the source node.
   distances = map infinity to all nodes
   distances = 0

   // Initialize an empty set of visited nodes and a priority queue to keep track of the nodes to visit.
   visited = empty set
   queue = new PriorityQueue()
   queue.enqueue(source, 0)

   // Loop until all nodes have been visited.
   while queue is not empty:
       // Dequeue the node with the smallest distance from the priority queue.
       current = queue.dequeue()

       // If the node has already been visited, skip it.
       if current in visited:
           continue

       // Mark the node as visited.
       visited.add(current)

       // Check all neighboring nodes to see if their distances need to be updated.
       for neighbor in Graph.neighbors(current):
           // Calculate the tentative distance to the neighbor through the current node.
           tentative_distance = distances[current] + Graph.distance(current, neighbor)

           // If the tentative distance is smaller than the current distance to the neighbor, update the distance.
           if tentative_distance < distances[neighbor]:
               distances[neighbor] = tentative_distance

               // Enqueue the neighbor with its new distance to be considered for visitation in the future.
               queue.enqueue(neighbor, distances[neighbor])

   // Return the calculated distances from the source to all other nodes in the graph.
   return distances










|   |
|---|
|`// Program to find Dijkstra's shortest path using`<br><br>`// priority_queue in STL`<br><br>`#include <bits/stdc++.h>`<br><br>`using` `namespace` `std;`<br><br>`#define INF 0x3f3f3f3f`<br><br>`// iPair ==> Integer Pair`<br><br>`typedef` `pair<``int``,` `int``> iPair;`<br><br>`// This class represents a directed graph using`<br><br>`// adjacency list representation`<br><br>`class` `Graph {`<br><br>    `int` `V;` `// No. of vertices`<br><br>    `// In a weighted graph, we need to store vertex`<br><br>    `// and weight pair for every edge`<br><br>    `list<pair<``int``,` `int``> >* adj;`<br><br>`public``:`<br><br>    `Graph(``int` `V);` `// Constructor`<br><br>    `// function to add an edge to graph`<br><br>    `void` `addEdge(``int` `u,` `int` `v,` `int` `w);`<br><br>    `// prints shortest path from s`<br><br>    `void` `shortestPath(``int` `s);`<br><br>`};`<br><br>`// Allocates memory for adjacency list`<br><br>`Graph::Graph(``int` `V)`<br><br>`{`<br><br>    `this``->V = V;`<br><br>    `adj =` `new` `list<iPair>[V];`<br><br>`}`<br><br>`void` `Graph::addEdge(``int` `u,` `int` `v,` `int` `w)`<br><br>`{`<br><br>    `adj[u].push_back(make_pair(v, w));`<br><br>    `adj[v].push_back(make_pair(u, w));`<br><br>`}`<br><br>`// Prints shortest paths from src to all other vertices`<br><br>`void` `Graph::shortestPath(``int` `src)`<br><br>`{`<br><br>    `// Create a priority queue to store vertices that`<br><br>    `// are being preprocessed. This is weird syntax in C++.`<br><br>    `// Refer below link for details of this syntax`<br><br>    `// [https://www.geeksforgeeks.org/implement-min-heap-using-stl/](https://www.geeksforgeeks.org/implement-min-heap-using-stl/)`<br><br>    `priority_queue<iPair, vector<iPair>, greater<iPair> >`<br><br>        `pq;`<br><br>    `// Create a vector for distances and initialize all`<br><br>    `// distances as infinite (INF)`<br><br>    `vector<``int``> dist(V, INF);`<br><br>    `// Insert source itself in priority queue and initialize`<br><br>    `// its distance as 0.`<br><br>    `pq.push(make_pair(0, src));`<br><br>    `dist[src] = 0;`<br><br>    `/* Looping till priority queue becomes empty (or all`<br><br>    `distances are not finalized) */`<br><br>    `while` `(!pq.empty()) {`<br><br>        `// The first vertex in pair is the minimum distance`<br><br>        `// vertex, extract it from priority queue.`<br><br>        `// vertex label is stored in second of pair (it`<br><br>        `// has to be done this way to keep the vertices`<br><br>        `// sorted distance (distance must be first item`<br><br>        `// in pair)`<br><br>        `int` `u = pq.top().second;`<br><br>        `pq.pop();`<br><br>        `// 'i' is used to get all adjacent vertices of a`<br><br>        `// vertex`<br><br>        `list<pair<``int``,` `int``> >::iterator i;`<br><br>        `for` `(i = adj[u].begin(); i != adj[u].end(); ++i) {`<br><br>            `// Get vertex label and weight of current`<br><br>            `// adjacent of u.`<br><br>            `int` `v = (*i).first;`<br><br>            `int` `weight = (*i).second;`<br><br>            `// If there is shorted path to v through u.`<br><br>            `if` `(dist[v] > dist[u] + weight) {`<br><br>                `// Updating distance of v`<br><br>                `dist[v] = dist[u] + weight;`<br><br>                `pq.push(make_pair(dist[v], v));`<br><br>            `}`<br><br>        `}`<br><br>    `}`<br><br>    `// Print shortest distances stored in dist[]`<br><br>    `printf``(``"Vertex Distance from Source\n"``);`<br><br>    `for` `(``int` `i = 0; i < V; ++i)`<br><br>        `printf``(``"%d \t\t %d\n"``, i, dist[i]);`<br><br>`}`<br><br>`// Driver program to test methods of graph class`<br><br>`int` `main()`<br><br>`{`<br><br>    `// create the graph given in above figure`<br><br>    `int` `V = 7;`<br><br>    `Graph g(V);`<br><br>    `// making above shown graph`<br><br>    `g.addEdge(0, 1, 2);`<br><br>    `g.addEdge(0, 2, 6);`<br><br>    `g.addEdge(1, 3, 5);`<br><br>    `g.addEdge(2, 3, 8);`<br><br>    `g.addEdge(3, 4, 10);`<br><br>    `g.addEdge(3, 5, 15);`<br><br>    `g.addEdge(4, 6, 2);`<br><br>    `g.addEdge(5, 6, 6);`<br><br>    `g.shortestPath(0);`<br><br>    `return` `0;`<br><br>`}`|


    ios_base::sync_with_stdio(false);
    cin.tie(NULL);