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


**Splay tree** - BST elements that are accessed more have faster search() time
* On search() splay() operation is performed:
    move node to the root using splay steps (rotations, preferable double) depending 
    on which child is searched node (left/right?) and it's parent location (is root?)

**Trie (prefix tree)** - k-ary search tree used for locating keys (strings)
* root - empty node
* internal nodes - characters in a string
* leafs - string end markers

**Interval tree** - tree holding intervals
for a sequence x_0,...x_N
    Construction: take entire range of x-values and divide in half at some x_center.
Resulting 3 groups (left of x_center, right of x_center and overlapping) processed
recursively, except for overlapping, which stored separately as 2 lists (sorted by begin
and by end) linked to node




**A10**: AVL Tree
---
Kind of self-balancing BST, helps with ordered dictionary implementation

*Properties*:
    ⁃ for any node heights of its right and left subtrees differ by at most 1

*Operations*:
    ⁃ Search, Insert, Delete - O(log N)

Balancing is done after modifying operations via single and double rotations



**A11**: (a,b)-tree
---
kind of balanced search tree, good for databases

Properties:
 ⁃ all leaves are at the same depth
 ⁃ all internal nodes has children count in [a,b], where 2 <= a, 2a - 1 <= b
 ⁃ root has children count in [2,b]

B-tree - (a, 2a-1)-/(a, 2a)-tree
* data may be located on the lowest layer above leafs - rest are helper keys



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

Balancing is done after modifying operations, possible O(1) balancing after delete

- Analogy to (2,4)-trees/B-tree of order 4:
Red-Black tree can be fit into (2,4)-tree/B-tree of order 4 and each node in the resulting tree
will contain exactly one black "value" with optional red "values" before and/or after



**B1**: Hashing
---
subset X (of size N) of universe U is stored to hash table (array of size M = O(N))
using hash function h_i; order is not preserved

- Collision detection: 2 different elements of X end up in the same cell
    - Chaining: cell contains linked list of length N/M on average
        Search()/Add()/Delete() has time O(1 + N/M)
    - Open Addressing: rehashing 
if N/M increases badly - increase size of M twice
Birthday Paradox (23 people in a room, 2 of them have >50% chance of having birthday
on the same day) implies that M = O(N^2) is required to have constant probability of
no collision

- Analysis of average cell visits for unsuccessful search



**B2**: Universal hashing
---
H:U-->[m] - **c-universal** system of functions for c >= 1, if for every x != y
from U: Pr[h(x)=h(y)] <= c/M for h in H.

H:U-->[m] - **(2,c)-independent** for c >= 1, if for every x1 != x2 from U, for
every y1, y2 from [m]: Pr[h(x1)=y1 AND h(x2)=y2] <= c/(M^2)
**k-independent** system has for k elements from U and [m]: Pr[...] <= 1/(M^k)



**B3**: Divide and Conquer
---
- algorithm example:
    Merge sort, Karasuba multiplication, Strassen matrix multiplication,
    QuickSort, QuickSelect

- Master Theorem
    * T(n) = aT(n/b) + O(n^c)
    * T(k) = O(1) for k = O(1),
where for a >= 1, b > 1, c >= 0
* T(n) = O(n^c log n), if a/(b^c) = 1
* T(n) = O(n^(log_b a)), if a/(b^c) > 1
* T(n) = O(n^c), if if a/(b^c) < 1



**B4**:
---
- Karatsuba number multiplication

*Idea*:
x = [x1][x0] - first number,
y = [y1][y0] - second number,
B - base,
m = N/2 - roughly half of number length
1. Represent 2 numbers as sum of upper and lower halves of length m
    * x = x1 x B^m + x0
    * y = y1 x B^m + y0
2. Observe their product
(xy) = (x1 B^m + x0)(y1 B^m + y0) = x1y1 B^2m + (x1y0 + x0y1)B^m + x0y0
    * Let
        * z2 = x1y1
        * z1 = x1y0 + x0y1
        * z0 = x0y0
3. Replace 4 multiplications with 3 and some additions
z1 = (x1 + x0)(y1 + y0) - z2 - z0

*Complexity*: O(N^2) --> O(N^(log_2 3))
T(N) = 3T(N/2) + O(N)

- Strassen Matrix Multiplication (w/o equations, just idea and complexity)

*Idea*: replace 8 multiplications and 4 additions with 7 and some additions 10 additions
by defining new matrices

*Complexity*: O(N^3) --> O(N^(log_2 7))
T(N) = 7T(N/2) + O(N^2)



**B5-6**: Dynamic Programming
---
- Longest Increasing Subsequence
    and
    - Edit Distance
        or
    - Optimal BST construction



**B7**: QuickSelect
---
Find k-th element in a list.

*Idea*: choose pivot --> partition list according to it to find its position
--> recursively proceed with one of the sublists or return

```
select(list, left, right, k):
    # trivial case
    if left == right:
        return list[left]

    # choose pivot
    pivotIndex = pivot()

    # partition list
    pivotIndex = partition(list, left, right, pivotIndex)

    # pivot is in sorted position
    if k == pivotIndex:
        # found desired element
        return list[pivotIndex]
    elif k < pivotIndex:
        # search in the left sublist
        return select(list, left, pivotIndex - 1, k)
    else
        # search in the left sublist
        return select(list, pivotIndex + 1, right, k)
```

1. Pivot choice

median-of-three
```
median3(list, start, end):
    mid := ⌊(start + end) / 2⌋
    # swap values of 3 positions
    if list[mid] < list[start]
        swap list[start] with list[mid]
    if list[end] < list[start]
        swap list[start] with list[end]
    if list[mid] < list[end]
        swap list[mid] with list[end]
    
    return end;
```
or random

2. Partition
Hoare
```
hoare(list, left, right, pivotIndex):
    pivotValue = list[pivotIndex]
    # initialize indexes
    start = left
    end = right

    while true:
        # tighten left side
        while list[start] < pivot:
            ++start

        # tighten right side
        while list[end] > pivot:
            --end

        # all elements are in proper order
        if start >= end:
            return end

        swap(list[start], list[end])
```

Lomuto: place all elements smaller than pivot's value to the left to determine
pivot's position
```
lomuto(list, left, right, pivotIndex):
    pivotValue = list[pivotIndex]
    # move pivot to the end
    swap(list[pivotIndex], list[right])
    storeIndex = left
    for i in [left, right - 1]:
        if list[i] < pivotValue:
            swap(list[storeIndex], list[i])
            ++storeIndex
    # move pivot to its proper place
    swap(list[right], list[storeIndex])

    return storeIndex
```

- Best and Worst cases
- Probability analysis wrt pivot selection



**B8**: QuickSort
---


- Best and Worst cases: depend on search decrease size when chosing pivot
Best:
    *
Worst:
    * left-most pivot in a sorted list
    * repeated elements

*Complexity*: O(N) - O(N) - O(N^2)


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
