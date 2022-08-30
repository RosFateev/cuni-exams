# Topics

Graph Algorithms:

Traversal:

- DFS
- BFS

Component search:

- Bridge Detection
- Articulation Point Detection
- Strongly Connected Components Search
- Union-Find Problem

Shortest path:

- Dijkstra
- Bellman-Ford
- Floyd-Warshall        

Min Spanning Tree:

- Jarnik
- Boruvka
- Kruskal

Data Structures:
---

- AVL Tree
- (a,b)-Tree
- B-Tree
- Red-Black Tree
- Prefix Tree
- Interval Tree

Hashing:
---

- Hash Table
- Collision

    - Chaining
    - Open Addressing

- Birthday Paradox
- Universal hashing
- K-independent hashing
    
Techniques:
---
- Divide and Conquer

    - Principle
    - Master Theorem
    - N-digit number multiplication (Karasuba)
    - Strassen Matrix Multiplication
    
- Dynamic programming:

    - Principle
    - Typicla Problems:

        - Fibonacci numbers
        - Edit distance
        - Longest increasing subsequence
        - Longest common subsequence
        - Optimal BST

Probability Algorithms:
---
- QuickSelect
- QuickSort
- Sorting Lowerbounds   


# Exam Questions

**AB0**:
    - RAM computational model
    - Asymptotic notation

**A1**:
---
- DFS
*Usage*: Traverse a graph (pre-/in-/post-order)
*Complexity*: O(|V| + |E|)

Input: Graph G, vertex v
Output: parent[v] array

```
DFS(G, root):
S - stack
S.push(root)
while S is not empty:
    v = S.pop()
    if v is not discovered:
        label v as discovered
        for (v,u) s.t u in neighbour(v):
            S.push(u)
```
(Similar can be achieved recursively: remove stack and instead of S.push(u) call DFS(G,u))

- BFS

*Usage*: Traverse a graph
*Complexity*: O(|V| + |E|)

Input: Graph G, vertex v
Output: parent[v] array

```
BFS(G,root):
Q - queue
Q.enqueue(root)
while Q not empty:
    v = Q.dequeue()
    if v is not discovered:
        label v as discovered
        for (v,u) s.t u in neighbour(v):
            Q.enqueue(u)        
```

- Edge classification in (un)directed graphs

stromova - (v,u), v - visited, u - new
zpetna   - (v,u), v - visited, u - visited
dopredna - (v,u), v - visited, u - closed, order(v) < order(u)
pricna   - (v,u), v - visited, u - closed, order(v) > order(u)

- Cycle Detection

- Bridge Detection

**A2**: Algorithms for acyclic directed graphs
---

- Topological order and its applications (longest path, counting paths):

*Usage*: Determine topological order in directed acyclic graph using DFS
*Complexity*: O(|V| + |E|)

```
Algorithm goes here
```

- Applications:
    - Shortest path in a weighted directed acyclic graph: proceed using vertex ordering and relax distance to vertex

**A3**: Strongly Connected Component search
---

*Usage*: Find Strongly Connected Components in a graph using DFS
*Complexity*: O(|V| + |E|)

```
Algorithm goes here
```

**A4**: Dijkstras algorithm (description + proof of correctness)
---

- Algorithm:

*Usage*: 1-to-1/many shortest path in any graph
*Complexity*: O(|E| + |V| log |V|) with min-queue/Fibonacci heap

* Initialise: for every vertex v (except source vertex)
    * dist[v] - infty
    * pred[v] - undefined
    * queue.add_with_priority(v, dist[v]) 
* While queue is not empty
    * v = get min from queue
    * for each neighbour u of v: 
        * if possible relax dist[u] and decrease u's priority to new distance
* return dist[] and pred[]

- Proof:
Hypothesis - "For each v: dist[v] - shortest when travelling via visited nodes only or infinity"
By induction on N:
⁃ 1 visited node: trivial
⁃ assume n-1 holds: simulate algorithm iteration for current min u and min weight edge (v,u).
Shortest path through unvisited node cannot exist (or u isn't min), and through visited as well (or (v,u) isn't min weight)


**A5**: Bellman-Ford algorithm
---

*Usage*: 1-to-1/many shortest path in any graph
*Complexity*: O(|V|x|E|)

* Initialise: for every vertex v (except source vertex)
    * dist[v] - infinity
    * pred[v] - undefined
* repeat |V| - 1 times:
    * for every edge e:
        * relax e
* check for negative loop: e=(u,v)
    * if weight can still improve some edge - detect negative cycle
* return dist[] and pred[]

**A6**:
---
    
- Dijkstras implementation with array and binary heap

- Floyd-Warshall algorithm

*Usage*: all shortest paths in a directed weighted graph with no negative cycles
*Complexity*: O(|V|^3)

* Initialise:
    * dist[][] to infinity
    * for each e=(u,v):
        * dist[u][v] = weight(u,v)
    * for each v:
        * dist[v][v] = 0
* for k in 1...N
    * for i in 1...N
        * for j in 1...N
            * if dist[i][j] > path through k:
                * update dist[i][j]

To detect negative cycles inspect the diagonal entries: negative value = negative cycle

**A7**: Min Spanning Tree Search (Jarnik and Boruvka)
---

- Jarnik/Prim:

*Usage*: min span tree in weighted undirected graph
*Complexity*: O(|E| + |V| log |V|) - Fibonacci heap + Adj list

* Initialise:
    * cost[v] - cheapest connection cost to v - infinity
    * edge[v] - edge of the cheapest connection - null
    * F - forrest - empty
    * Q - vertices not in the forrest - V
* repeat until Q is not empty:
    * find v with min cost[v]
    * add v to F
    * for each u in neighbour(v):
        * if u is in Q:
            * cost[u] = weight(v,u)
            * edge[u] = (v,u)
* return F

- Boruvka:

*Usage*: min span tree in weighted undirected graph

 1. Initialise
 1. F - forrest - (V, E'={})
...

**A8**: Kruskal algorithm and Union-Find problem
---

**A9**: Binary Search Tree
---

*Properties*:
    * every node has at most 2 children
    ⁃ node order: l_child.value < parent.value < r_child.value

*Operations*:
    ⁃ Search, Insert, Delete - O(log N) - O(N)

Height balance: left and right subtrees' heights are related by a constant factor (AVL)
Weight balance: left and right subtrees' leaf count differ at most by one

**A10**: AVL Tree
---
Kind of self-balancing BST

*Properties*:
    ⁃ for any node heights of its right and left subtrees differ by at most 1

*Operations*:
    ⁃ Search, Insert, Delete - O(log N)

Balancing is done after modifying operations via single and double rotations

**A11**: (a,b)-tree
---
kind of balanced search tree
Properties:
 ⁃ all leaves are at the same depth
 ⁃ all internal nodes has children count in [a,b], where 2 <= a <= (b+1)/2
 ⁃ root has 2 <= children <= b


**A12**: Red-Black Tree and their connection to (2,4)-trees
---
Kind of self-balancing BST

*Properties*:
    ⁃ every node is red or black
    ⁃ all NIL nodes (empty leafs) are black
    ⁃ red node doesn't have a red child
    ⁃ every node-NIL path goes through the same number of black nodes

*Operations*:
    ⁃ Insert/Delete - O(1)-O(log N)
    ⁃ Search - O(log N)

Balancing is done after modifying operations via ...

- Analogy to (2,4)-trees/B-tree of order 4:
Red-Black tree can be fit into (2,4)-tree/B-tree of order 4 and each node in the resulting tree
will contain exactly one black "value" with optional red "values" before and/or after



**B1**: Hashing
---
- Collision detection
- Analysis of average cell visits for unsuccessful search

**B2**: Universal hashing
---

**B3**: Divide and Conquer
---
- algorithm example
- Master Theorem

**B4**:
---
- Long number multiplication
- Strassen Matrix Multiplication (w/o equations, just idea and complexity)

**B5-6**: Dynamic Programming
---
- Longest Increasing Subsequence
    and
    - Edit Distance
        or
    - Optimal BST construction

**B7**: QuickSelect
---
- Best and Worst cases
- Probability analysis wrt pivot selection

**B8**: QuickSort
---
- Best and Worst cases
- Probability analysis wrt pivot selection
    
**B9**: K-th smallest element deterministic selection in O(N)
---

**B10**: Sorting Lowerbounds of binary search and comparison-based sorting
---



# Problems

- Town: edges - streets, vertices - intersections; Place policman, so that every street has at
    least one with minimal cost (vertex)
- Given text of words; Compute frequency of each word and print all ordered by it.

- Painting of planar graph with 6 colours
- Design data structure: ...

- Given a labirinth with protagonist, start point, end point and doors and keys of 3 different
    colours; Find shortest path
- Given unsorted sequence of length N and number K < N; Find max median of intervals of length K

- Compute number of inversions in a sequence
- Merge 2 BST to a single balanced BST

- Find shortest common supersequence of 2 given sequences
- Given a set of vectors of length D; Decide if exist V and U: V + U = 0

- Given sequence of integers; find longest interval with element sum divisible by 17
- Given set of words; Design data structure which finds all anagrams for given input word
