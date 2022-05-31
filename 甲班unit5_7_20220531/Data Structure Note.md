#### 資訊二甲 10927120 余政達
# Data Structure Note

## Chapter 5 - Hashing

### `Highlights`
- Hashing is a function that **transforms a key into table index, denote by $h(key)$**
- $r$ is a record whose key hashes into $hr$, $hr$ is called the **hash key of $r$**
- Time Complexity
    - **worst-case** for search, insert, and delete is $O(size)$
    - **expected time is** $O(1)$
- example: 1D array (table)
    - denote by `table[0: b-1]`
    - **each position is a bucket**
    - a bucket can normally hold **only one dictionary pair**
    - **hash**
        - using hash function $f$ converts each key $k$ **into an index in the range [0, b-1]**
        - $f(k)$ **is the home bucket for key $k$**
        - each **dictionary pair is stored in its home bucket**
- problem
    - **synonyms**: keys have the **same home bucket**
    - **collision**: home buckets for the new key is already **being occupied**
    - **overflow**: there is **no space** in the home bucket for the new pair


 
 ### `Hash functions`
- Assign each search key to a single location
  1. Easy and fast to compute
  2. Places items evenly throughout the hash table
  3. Involves the entire search key
  4. Uses a prime base, if it uses modulo arithmetic
    

### `Linear probing`
 
- **Primary clustering problem**
  - Items tend to cluster together and large clusters tend to get even larger
  - Large clusters cause long probing sequences (sequential search)
  Deletion problem
- Empty locations after deletions would incorrectly stop a probing sequence

### `Quadratic probing`
- Probing sequence may not visit every location in the hash table
- Secondary clustering problem
  - Different keys at the same location create the same probing sequence Table size must be prime
- Fewer alternate locations if it is not prime

### `Double probing`
- table size vs. step size
  - If they are relatively prime, the probing sequence will visit every location in the hash table
  
  
## Chapter 6 - Graph

- Solution of Königsberg Bridge Problem
    
    ![](https://i.imgur.com/GSL8vJn.png)

    
    - a walk starting at any vertex, going through each edge exactly once and terminating at the start vertex **iff the degree of each vertex is even**
    - a walk that satisfies the above conditions is called Eulerian walk
- definition of graph
    - consist of two sets, $V$ and $E$, usually be represented as $G=(V, E)$
        - $V$: a **finite, nonempty** set of vertices
        - $E$: a set of edge
    - degree of a vertex is defined as **the number of edges incident to it**
- subgraph $G'$
a graph that $V(G')\subseteq V(G)$ and $E(G')\subseteq E(G)$
- undirected graph
using ($v_1$, $v_2$) to represent edge
- **directed graph(digraph)**
    - **each edge is represented by a directed pair**
    - using <$v_1$, $v_2$> to represent the **edge from $v_1$ to $v_2$**
- graph with **self edges**
a edge from one vertex and **back to itself**
- multigraph
**multiple edges** between a pair of vertices
- $n$-vertex complete graph
    - a **undirected complete graph** has $n(n-1)/2$ edges
    - directed complete graph is a graph that every pair vertex is **connected by a bidirectional edge**
- path
    - length:the **number of edges** on it
    - simple path: a path that **except start and terminal points are distinct**
    - cycle: a **simple path** that **start and terminal points are the same**
- connection
    - an undirected graph is said to be **connected** iff there **exists paths between every pair of distinct vertices**
    - **connected component** $H$ of an undirected graph is a **maximal connected subgraph**
        
    - tree is a connected acyclic graph
    - a directed graph is **strongly connected** iff there exists a **biconnected directed path** between every pair of distinct vertices in it
    - strongly connected component is a maximal subgraph that is strongly connected
- degree
    - in directed graph
        - in-degree: the number of edges that **start from** a vertex
        - out-degree: the number of edges that **end at** a vertex
    - if $d_i$ is the degree of vertex $i$ in in a graph with $n$ vertices and $e$ edges, then the number of edges is $e=(\sum_{i=0}^{n-1} d_i)/2$

    
- representation
    - adjacency matrix
        - a **square matrix with only 0, 1(edge)**
        - **diagonal entries are zero**
        - adjacency matrix of **an undirected graph is symmetric**
        - for an **undirected graph, may store only lower or upper triangle**
        - $O(n^2)$ time to examine if a graph is connected
        - When graphs are sparse one would expect that the time could reduce to $O(e+n)$, where $e$ is the number of edges in $G$, and $e\ll n^2 /2$
    - adjacency list
        
      ![](https://i.imgur.com/0izQfXa.png)

        
        - **one chain for each vertex**
        - An array is used so that we can access the adjacency list for any vertex in $O(1)$ time
        - number of list elements
            
            undirected graph: $2e$
            digraph: $e$
            
- **weighted edges**
    - may represent the distance from one vertex to another or the cost
    - a **graph with weighted edges is called network**
- traversal
    - **Depth First Search(DFS)**
        - preorder tree traversal
        - time complexity
            - if a graph with $e$ edges is **represent by its adjacency list**, the time complexity is $O(e)$
            - if a graph with $n$ nodes is **represent by its adjacency matrix**, the time complexity is $O(n^2)$
    - **Breadth First Search(BFS)**
        - level order tree traversal
        - time complexity
            - if a graph with $e$ edges is **represent by its adjacency list**, the time complexity is $O(e)$
            - if a graph with $n$ nodes is **represent by its adjacency matrix**, the time complexity is $O(n^2)$
            - 

## Chapter 7 - Graph Application

### `Topological Sort: Definition`
- A list of vertices in a directed graph without cycles (Acyclic Digraph or Directed Acyclic Graph, DAG) such that vertex x precedes vertex y if there is a directed edge from x to y in the graph
- Several topological orders are possible for a given graph

### `Topological sorting`
- Arranging the vertices into a topological order

- top sort1
  1. Find a vertex that has no successor (out-degree=0)
  2. Add the vertex to the beginning of a list
  3. Remove that vertex from the graph, as well as all edges that lead to it
  4. Repeat the previous steps until the graph is empty
    - When the loop ends, the list of vertices will be in topological order
- topSort2
  - A modification of the iterative DFS algorithm
  - Push all vertices that have no predecessor onto a stack
  - Each time you pop a vertex from the stack, add it to the beginning of a list of vertices
  - When the traversal ends, the list of vertices will be in topological order

### `Minimum Spanning Tree: Definition`

- Cost of spanning tree
  - Sum of the edge weights on a spanning tree
- A minimum spanning tree of a connected undirected graph has a minimal edge-weight sum
  - A particular graph could have several minimum spanning trees

### `Minimum Spanning Tree: Algorithms`
- Find a minimum spanning tree that begins at any given vertex 
  1. Find the least-cost edge (v, u) from a visited vertex v to some unvisited vertex u
  2. Mark u as visited
  3. Add the vertex u and the edge (v, u) to the minimum spanning tree
  4. Repeat the above steps until all vertices are visited

### `Prim's algorithm`
- build the tree by **choosing the vertex** from original graph that **the weight of edge connect to it is the smallest a time** then connect the vertex if it **doesn't form cycle in the tree**
- choose the **edge connected to the two ends of the spanning tree**
