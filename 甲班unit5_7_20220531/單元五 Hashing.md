資料結構筆記 單元：5~7 10927101 林柏諺 


# 單元五 Hashing 

## h1Hashing
- Enables access to table items in time that is relatively constant regardless of their locations
自動存物箱
Hash function
- Maps the search key of a is table item into a location that will contain the item
#May two locations have the same search key?

## h2 Hashing: Basics

**Hash table = (automatic) Manger of lockers
- An array that contains the table items, as assigned
  by a hash function (key > location mapping)
  e.g., ID, birthday,
**Perfect hash function
Maps each search key into a unique location
Possible only if all the search keys are known
![](https://i.imgur.com/lzGKiMu.jpg)

## h3 Hashing: Requirements
 - Hash functions
   Assign each search key to a single location
   1 Easy and fast to compute
   2.Places items evenly throughout the hash table
   3.Involves the entire search kev
   4 Uses a prime base, if it uses modulo arithmetic
 - Collision resolution schemes
   Assigns distinct locations in the hash table to
   items involved in a collision
   
## h4 Hashing: Collision Resolution
 
  1. *Open addressing*
  - Probe for an empty location in the hash table
    As the hash table fills, collisions increase
  d.Increase of table size
  *  Need to hash the items again*
  
  2. *Restructuring the hash table*
     Allows the hash table to accommodate more than
     one item in the same location
     
     
### Hashing: Collision Resolution
  ~ Open addressing
    
    a.  *Linear probing*
    b.  *Ouadratic probing*
      - Both create key independent probing sequences
      
   - C   Double hashing
     It creates key dependent probing sequences
     Uses two hash functions h,, h, to reduce clustering problems
     h1, for the first location and h, for the step size
![](https://i.imgur.com/pqlIDeX.jpg)



# 單元六 Graph Basics
    Terminologies
    Representations
    Traversals


## h1 Seven Bridges of Königsberg

 - Königsberg in Prussia
   Kaliningrad, Russia
   Pregel River
   Two large islands
   Seven bridges
 - Leonhard Euler [1735]
   Find a walk through the city that would cross each
   bridge once and exactly once
   The first paper in the history of graph theory
   

## h2 Seven Bridges of Königsberg
 - G= (V, E;
    V(G): vertex set
    E(G): edge set
    degree
      -Number of edges
- Vertex types
  Odd or even degrees
![](https://i.imgur.com/O21DL6N.jpg)


## h3 Graphs As ADTs

 - Variations of an ADT graph are possible
  -Vertices may or may not contain values
    - Many problems have no need for vertex values
    - [Relationships] among vertices is what is important
    - Either directed or undirected edges
    - Either weighted or unweighted edges
- Insertion and deletion operations for graphs apply to vertices and edges
- Graphs can have traversal operations


## h4 ADT graph Operations

- int num Vertices;   /** Number of vertices in the graph.*/
- int numEdges;       /** Number of edges in the graph.*/
- int getNum VerticesO:
- int getNumEdgesO;
- int get Weight (Edge e);
- void add (Edge e);
- void remove(Edge e);
- bool isEdge(Vertex u, Vertex v);
- int getDegree (Vertex v);
- **bool isConnected(Graph g);**
- **edgeList traverse(Graph g);**


## h5 Adjacency List

- Adjacency list for a directed graph that has n
  vertices numbered 0, 1, ...,.. n - 1
- An array of n linked lists
- The ith linked list has a node for vertex ; if and
  only if an edge exists from vertex i to vertex j
- The list's node can contain either
 
       Vertex j's value, if any
       An indication of vertex j's identity




# 單元七 Graph App.
    Topological Sort
    Spanning Tree
    Shortest Paths
    
## h1 Topological Sort: Definition
- Topological order
  - A list of vertices in a directed graph without cycles
    (Acyclic Digraph or Directed Acyclic Graph, DAG)
    such that vertex a precedes vertex y if there is a
    directed edge from x to y in the graph
   - Several topological orders are possible for a given graph
- Topological sorting
  - Arranging the vertices into a topological order

## h2 Topological Sort: Examples

![](https://i.imgur.com/txY4pCw.jpg)


## h3 A Trace of topSort1 (concept)
- List
  - SP 
    ALGO, SP
    DM, ALGO, Sp !
    PL, DM, ALGO, SP
    DS, DM, ALGO, SP
    AL, DS, DM, ALGO, SP
    CAL, AL, DS, DM, ALGO, SP 
    ![](https://i.imgur.com/3UIyJFR.jpg)
    
## h4 Practice 3: in-degree = 0 (no predecessor)
   ![](https://i.imgur.com/4XQH6Hy.jpg)
 
    
## h5 Topological Sort: Algorithms
 - topSort2
    - A modification of the iterative DFS algorithm
    - Push all vertices that have no predecessor onto a stack
    - Each time you pop la vertex from the stack, add
      it to the beginning of a list of vertices
    - When the traversal ends, the list of vertices will
      be in topological order
      

## h6 DFS in iterative form (stack)
  
 - iterativeDFS(Vertex v)
   s.createStack0;
   s.push(v);
   Mark vas visited;
   
   ![](https://i.imgur.com/FSmAGMv.jpg)
