資料結構與演算法 10927142 黃鈺婷

# Unit5. Hashing
## Basic
* Hash table = Manager of locker
    An array that contains the table items, as assigned by a hashing function
    (key->location mapping)
* Perfect hashing function
    * Maps each search key into a unique location
    * Possible only if all the search keys are known
## Collision
Occurs when the hash function maps two ormore items -- all having different search keys -- into the same array location

### Resolution
* Open addressing
    * **Linear probing**
        -search the first location and then the next
    ![](https://i.imgur.com/DZKDAly.png)
    * **Quadratic probing**
        -search the first location and then continue at the increment of 1^2^, 2^2^, 3^2^...
    ![](https://i.imgur.com/pDpuWbV.png)
    * **Double hashing**
        -create key dependent probing sequence
        -uses two hashing functions h1, h2, to reduce clustering problems
        -h1 for the first location and h2 for the step size
    ![](https://i.imgur.com/P5p02RU.png)
* Restructuring the hash table
    * **Buckets**
        -Each location in the hash table is itself an array
    * **Seperate chaining**
        -Each hash table location is a linked list
        -successfully resolves collisions
        -the size of the hash table is dynamic

## Efficiency
![](https://i.imgur.com/I4goRqx.png)

## Functions
1. Digit selection
2. Folding
3. Modulo arithmetic
4. Converting character strings


# Unit6. Graph Basics
## Definition
* G = {V, E}
    * V(G): vertex set
    * E(G): edge set
    * degree: number of edges
* Vertex types
    * Odd or even degrees

## Basic Terminologies
* Connected graph
    -there is a path between any two vertices
* Complete graph
    -there id an edge between any two vertices
* Strong connected graph
    -for any twp vertices on a disgraph, there is a path from one vertex to the other
* Weighted graph
    -the edges have numeric labels

## Representation
### Adjacency matrix
![](https://i.imgur.com/9tPn4UY.png)
### Adjacency list
![](https://i.imgur.com/44osfaX.png)

## Traversals
### Depth-First Search (stack)
![](https://i.imgur.com/QXE8zSD.png)
![](https://i.imgur.com/dAOfxXG.png)

### Breadth-First Search (queue)
![](https://i.imgur.com/nBFhqyT.png)
![](https://i.imgur.com/3oxOuV4.png)

### DFS v.s.  BFS
![](https://i.imgur.com/WJWA5rF.png)

# Unit7. Graph App.
## Topological Sort
### Definition 
* order
    * A list of vertices in a directed graph without cycles(Acyclic Digraph or Directed Acyclic Graph, DAG) such that vertex x proceeds vertex t if there is a directed edge from x to y in the graph
    * Several topological orders are possibles for a given graph
* sorting
    * Arranging the vertices into a topological order
* Algorithms
    * topSort1
        1. Find a vertex that has no successor(out-degree=0)
        2. Add the vertex to the begining of a list
        3. Remove that vertex from the graph, as well as all edges that lead to it
        4. Repeat the previous steps until the graph is empty
    * topSort2
        1. A modification of the iterative DFS algorithm
        2. Push all  vertices that hace no predecessoronto a stack
        3. Each time you pop a vertex from the stack, add it to the begining of a list of vertices
        4. When the travelsal ends, the list of vertices will be in topological order


## Spanning Tree
### Definition
* A tree is an undirected connected graph without cycles(acyclic)
* A spanning tree of a connected undirected graph G is
    - Asubgraph of G that contains all of G's vertices and enough of its edges to form a tree
    - Application example: communication network
* To obbtain a spanning tree from a connected undirected graph with cycles
    - Remove edges until there are no cycles
:::info
Propertices: Detecting a cycle in an undirested connected graph
:::

### Prufer Sequence
* Rationale behind the proof
    * For n labels, there are n^n-2^ sequences of length n-2
    * Each Prufer sequence can be converted to a unique labeled tree with n vertices(a spanning tree)
    * For a complete graph with n vertives, there are n^n-2^ spanning trees
* Other applications
    * Compact tree representation -> Prufer code
    * XML structural matching -> twig query

### DFS/BFS for Spanning Trees
* DFS
![](https://i.imgur.com/JlHdtoz.png)
* BFS
![](https://i.imgur.com/xxm5Bfe.png)

### Minimum Spanning Tree
Tree of a connected undirected graph has a minimal edge-weight sum
![](https://i.imgur.com/YOxYv5H.png)

* **Prim's Algorithms**
    1. Find the least-cost edge(v, u) from a visited vertex v to some unvisited vertex u
    2. Make u as visited
    3. Add the vertex u and the edge(v, u) to the minimum spanning tree
    4. Repeat the above steps until all vertices are visited
![](https://i.imgur.com/uHFHgUh.png)

* **Kruskal's Algorithms**
    1. Create a forest, where each vertex is a tree
    2. Find the least-cost edge(v, u) where vertex v and vertex u are from two different trees
    3. Merge the tree of vertex v and vertex u, and add the edge(v, u) to the minimum spanning tree
    4. Repeat the above steps until |V|-1 edges
![](https://i.imgur.com/AfHVA2h.png)

* **Sollin's Algorithms**
    1. Create a forest, where each vertex is a tree
    2. For each tree, do the following steps:
        (1) Find the least-cost edge(v, u) where vertex v in T and vertex u is outside T 
        (2) Merge the trees of vertex v and vertex u, and add the edge(v, u) to the minimum spanning tree
    3. Reprat step 2 until only one tree is left
![](https://i.imgur.com/Z01QQpO.png)


## Shortest Paths
Find the shorted path between a given origin and all other vertices
* **Dijkstra's Algorithms**
    1. Initialaize vertexSet & weight
    2. Update weight for each vertex u not in vertexSet, which is adjacent to v
    3. Find the shortest path from o to u among every path starts from o, passes vertices in vertexSet
    4. Repeat step 2, 3 until no more vertex can be added

    * **Adjacency Matrix**
    ![](https://i.imgur.com/ROJ7Mkv.png)
    * **Adjacency List**
    ![](https://i.imgur.com/WgaK9Zq.png)

## Shortest Path Tree v.s. Minimum Spanning Tree
![](https://i.imgur.com/7TpAsG0.png)

## All-Pairs Shortest Path
* **Floyd's Algorithms**
    1. Initialize distance matrix D^-1^
    2. For K = 0 to |V|-1, D^k^ <- D^k-1^
    * **Directed Graph**
    ![](https://i.imgur.com/9rSUX7g.png)
    * **Undirected Graph**
    ![](https://i.imgur.com/CLvQkBB.png)









