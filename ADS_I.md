Algorithms and Data Structures I
----------------------------------------------------------------------------------------------------

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
    - AVL Tree
    - (a,b)-Tree
    - B-Tree
    - Red-Black Tree
    - Prefix Tree
    - Interval Tree

Hashing:
    - Hash Table
    - Collision
        - Chaining
        - Open Addressing
    - Birthday Paradox
    - Universal hashing
    - K-independent hashing
    
Techniques:
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
    - QuickSelect
    - QuickSort
    - Sorting Lowerbounds   
----------------------------------------------------------------------------------------------------

Exam Topics
----------------------------------------------------------------------------------------------------

**AB0**:
    - RAM computational model
    - Asymptotic notation

**A1**:
    - DFS
Input: Graph G, vertex v
Output: parent[v] array

DFS(G, root):
S - stack
S.push(root)
while S is not empty:
    v = S.pop()
    if v is not discovered:
        label v as discovered
        for (v,u) s.t u in neighbour(v):
            S.push(u)

Complexity: O(|V| + |E|)
(Similar can be achieved recursively: remove stack and instead of S.push(u) call DFS(G,u))

    - BFS
Input: Graph G, vertex v
Output: parent[v] array

BFS(G,root):
Q - queue
Q.enqueue(root)
while Q not empty:
    v = Q.dequeue()
    if v is not discovered:
        label v as discovered
        for (v,u) s.t u in neighbour(v):
            Q.enqueue(u)        


Complexity: O(|V| + |E|)

    - Edge classification in (un)directed graphs
stromova - (v,u), v - visited, u - new
zpetna   - (v,u), v - visited, u - visited
dopredna - (v,u), v - visited, u - closed, order(v) < order(u)
pricna   - (v,u), v - visited, u - closed, order(v) > order(u)

    - Cycle Detection

    - Bridge Detection
**A2**: Algorithms for acyclic directed graphs
    - Topological order and its applications (longest path, counting paths)

**A3**: Strongly Connected Component search

**A4**: Dijkstras algorithm (description + proof of correctness)

**A5**: Bellman-Ford algorithm

**A6**:
    - Dijkstras implementation with array and binary heap
    - Floyd-Warshall algorithm

**A7**: Min Spanning Tree Search (Jarnik and Boruvka)

**A8**: Kruskal algorithm and Union-Find problem

**A9**: BST perfect vs depth weight

**A10**: AVL Tree

**A11**: (a,b)-tree

**A12**: Red-Black Tree and their connection to (2,4)-trees



**B1**: Hashing
    - Collision detection
    - Analysis of average cell visits for unsuccessful search

**B2**: Universal hashing

**B3**: Divide and Conquer
    - algorithm example
    - Master Theorem

**B4**:
    - Long number multiplication
    - Strassen Matrix Multiplication (w/o equations, just idea and complexity)

**B5-6**: Dynamic Programming
    - Longest Increasing Subsequence
    and
        - Edit Distance
        or
        - Optimal BST construction

**B7**: QuickSelect
    - Best and Worst cases
    - Probability analysis wrt pivot selection

**B8**: QuickSort
    - Best and Worst cases
    - Probability analysis wrt pivot selection
    
**B9**: K-th smallest element deterministic selection in O(N)

**B10**: Sorting Lowerbounds of binary search and comparison-based sorting

----------------------------------------------------------------------------------------------------


Problems
----------------------------------------------------------------------------------------------------
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



