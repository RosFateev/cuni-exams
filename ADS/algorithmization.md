# Algorithmization

## Topics

# Topics

1. **Algorithms and their effectiveness**

2. **Number Theory algorithms:**
    1. *Brute Force Primality Test* - check if number is prime
        - Input: integer
        - Output: bool
        - Time Complexity: O(2^N)
        - Space Complexity: O(1)
    
    2. *Eratosthenes Sieve* - output all prime numbers in a range
        - Input: integer
        - Output: [ integer ]
        - Time Complexity: O(N log log N)
        - Space Complexity: O(N)
    
    3. *Euclidian* - determine greatest common divisor
        - Input: integer, integer
        - Output: integer
        - Time Complexity: O(log N)
        - Space Complexity: O(1)
    
    4. *Horner Scheme* - polynomial evaluation or number system conversion
        - Input: [ integer ], integer
        - Output: integer
        - Time Complexity: O(N)
        - Space Complexity: O(1)
    
    5. *Quick Power* - compute power of number
        - Input: integer, integer
        - Output: integer
        - Time Complexity: O(log N)
        - Space Complexity: O(1)

3. **Sorting 1:**
    1. *Bubble sort* - iterate N times and swap each two elements violating order
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N^2)
        - Space Complexity: O(1)
        - Stable: Yes

    2. *Select sort* - find minimal element in unsorted and swap with unsorted[0];
    (N-1) swaps, O(N) writes
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N^2)
        - Space Complexity: O(1)
        - Stable: No

    3. *Insert sort* - pick element in unsorted and find its position in sorted (end->start);
    the best quadratic algorithm for small data
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N^2)
        - Space Complexity: O(1)
        - Stable: Yes

    4. *Heap sort* - construct max-heap, n-times swap current max with last element before sorted
    and rebalance
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N log N)
        - Space Complexity: O(1)
        - Stable: No

4. **Sorting 2:**
    1. *Merge sort* - in-place merge sublists to obtain sorted list
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N log N)
        - Space Complexity: O(N) - array / O(1) - linked list
        - Stable: Yes

    2. *Comparison-based sorting lowerbound* - why not faster than N log N
        - for a list of N distinct numbers exist N! permutations
        - if algorithm always completes in f(N) steps => it can't distinguish more than 2^f(N) cases
        - 2^f(N) >= N! => f(N) >= log(N!) >= log((N/2)^(N/2)) = 1/2 N log N

    3. *Counting sort* - place number of occurences of input elements with values in range [0,...,K]
    to approproate buckets; structured data requires additional handling; stable
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N + K)
        - Space Complexity: O(K)
        - Stable: Yes

    4. *Radix sort* - sort sequence of integer by their radixes (digits) using stable linear sorting;
    a lot of space is required
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(d(N + K))
        - Space Complexity: O(N + 2^r)   , r - number of digits
        - Stable: Yes

5. **Searching:**
    1. *Linear search* - sequentialy search for an element in array
        - Input: [ integer ], integer
        - Output: integer
        - Time Complexity: O(N)
        - Space Complexity: O(1)

    2. *Binary Search* - recursively search for an element in an appropriate subarray of **sorted**
    array 
        - Input: [ integer ], integer
        - Output: integer
        - Time Complexity: O(log N)
        - Space Complexity: O(1)

    3. *Compute square root* - using binary search-ish approach of "determining the location"
        - Input: integer
        - Output: integer
        - Time Complexity: O(log N)
        - Space Complexity: O(1)

6. **Data structures:** depend on underlying implementation (Python list)
    0. Python list - is practically an array
        - Methods
            - pop() - list[last]    - O(1)
            - append()              - O(1) / O(N) if reallocation

    1. *Stack* - Last-In-First-Out structure
        - Operations
            - Push  - list.append() - O(1)
            - Pop   - list.pop()    - O(1)

    2. *Queue* - First-In-First-Out structure
        - Operations
            - Enqueue - list.append()   - O(1)
            - Dequeue -                 - O(1) - store start index, when called - ++index (no actual removal)
        - Cycle queue solves operations' complexity pitfalls

    3. *Linked list* - chained nodes containing value and ptr to next

    4. *Priority queue*
        - Properties
            - Every node has priority, based on which operations are performed
        - Implementations
            - Linked list (unsorted) - Enqueue - O(1); Dequeue - O(N)
            - Linked list (sorted) - Enqueue - O(N); Dequeue - O(1)
            - Binary heap - Enqueue and Dequeue - O(log N)
        - Operations
            - Enqueue
            - Dequeue
            - Max
            - ChangePriority
            - Remove

7. **Recursion:**
    1. *Palindrom* - determine if input string is symmetric
        - Input: string
        - Output: bool
        - Time Complexity: O(N)
        - Space Complexity: O(1)

    2. *Hanoi tower* - solve hanoi puzzle
        - Input: integer, string, string, string
        - Output: bool
        - Time Complexity: O(2^N)
        - Space Complexity: O(1)

8. **(8-1)Recursive Data Structures:**
    1. *Binary tree*
        - Properties
            - Every node has at most 2 children
        - Traversal
            - Preorder - Root -> Left subtree -> Right subtree
            - Inorder - Left subtree -> Root -> Right subtree
            - Postorder - Left subtree -> Right subtree -> Root

    2. *DFS* - Depth-First-Search using stack
        - Input: Tree
        - Output: order
        - Time Complexity: O(N)
        - Space Complexity: O(?)

    3. *BFS* - Breadth-First-Search using queue
        - Input: Tree
        - Output: order
        - Time Complexity: O(N)
        - Space Complexity: O(?)

9. **(8-2)Recursive Data Structures:**
    1. *Arithmetic expressions* - using binary tree
        - Properties
            - Leafs - operands
            - Inner nodes - operators
            - Brackets - represented by subtrees (not implicitly present)
        - *Construction 1* - recursive top-to-bottom - search for root operator, if expression is
        enclosed into brackets - operator is outside; recursively compute subtrees for subexpr.
            - Input: string
            - Output: binary tree
            - Time Complexity: O(N^2)
            - Space Complexity: O(1)
        - *Construction 2* - bottom-to-top with stack - go through expression pushing to stack
        according to construction rules
            - Input: string
            - Output: binary tree
            - Time Complexity: O(N)
            - Space Complexity: O(?)
        - Notations
            - Prefix: * + a b c (no brackets) - construct with preorder tree traversal
            - Infix: (a + b) * c              - construct with inorder tree traversal
            - Postfix: a b + 3 * (no brackets)- construct with postorder tree traversal
        - *Evaluate* - recursively traverse tree; leafs - return value; inner - return result of
        left parent right
            - Input: tree
            - Output: integer
            - Time Complexity: O(N)
            - Space Complexity: O(1)
        - *Evaluate postfix left->right/prefix right<->left* - traverse expression linearly,
        use stack to store tokens (the only difference - order of left/right operand pop()
        from stack)
            - Input: string
            - Output: integer
            - Time Complexity: O(N)
            - Space Complexity: O(?)
        - *Evaluate prefix recursive* - recursively call to get operands
            - Input: string
            - Output: integer
            - Time Complexity: O(N)
            - Space Complexity: O(1)
        - *Evaluate infix recursive* - similar to recursive tree construction
            - Input: string
            - Output: integer
            - Time Complexity: O(N^2)
            - Space Complexity: O(1)
        - *Evaluate infix converting to postfix* - convert to postfix (using stack) and evaluate;
        both operations can be done simultaneously
            - Input: string
            - Output: integer
            - Time Complexity: O(N)
            - Space Complexity: O(?)

    2. *K-ary Trees*
        - Properties
            - Each node has at most k children
        - Representations
            - Children attributes (child1, child2, ...)
            - Python list with children
            - Linked list with children (parent has a single child, which is chain-connected to
            brothers - binary tree representation)

10. **(9)Prohledavani stavoveho prostoru:**
    1. *Recursive generation of variation* - recoursively generate variation of K-th class of
    elements {1,...,N} with repetition
        - Input: integer, integer
        - Output: []
        - Time Complexity: O(N^K)
        - Space Complexity: O(?)

    2. *Recursive generation of combination* - recoursively generate combination of K-th class of
    elements {1,...,N} with no repetition
        - Input: integer, integer
        - Output: []
        - Time Complexity: O(N^k)
        - Space Complexity: O(?)

    3. *Summand decomposition* - for a given number recursively generate all possible sums
        - Input: integer
        - Output: []
        - Time Complexity: O(N^?)
        - Space Complexity: O(?)

    4. *N(8) queen problem* - Place N queens on NxN chessboard, so that they won't attack each other;
    program state tree backtracking
        - Input: integer
        - Output: []
        - Time Complexity: O(N!)
        - Space Complexity: O(?)

    5. *Knight path* - Find knight's path from (i,j) on NxN chessboard, so that each field is
    visited only once; program state tree heuristics
        - Warnsdorff heuristics: prioritize children with smallest number of continuations
    
    6. *Traveling salesman problem* - Visit each place once in a shortest cycle-path; 
    state tree backtracking

11. **(10)Prohledavani stavoveho prostoru:** Game theory
    0. *Min-Max algorithm* - value = min max value_player {action_player, action_others}
    
    0. *Game State Tree* - leafs - indicator of player won; inner nodes - max{# player won} based
    on leafs
    
    0. *Startegy* - subtree of game state tree including root; winning strategy - all winning results
    
    1. *NIM* - 2 players remove matches(1-2) one-by-one from pile, player removing last match loses;
    
    2. *Shannon theorem* - proof using MinMax (inductive on the depth  of tree + using game state tree definition)

    3. *Restricted depth MinMax* - look N steps ahead;
        - *Alpha-Beta cutting* - alpha - best for player_1, beta - best for player_2;
    cutting the subtree make sense when its value is outside of (alpha,beta) interval
        - To assemble winning path memorize all reached states in hash table (with their parent)
        - Time complexity: O(b^h), b - leaf count, h - depth

12. **(11-1)Data structures:**
    1. *Dictionary*
        - Properties
        - Implementations
            - 1)Binary Search Tree (if balanced (AVL/Red-Black) => height == log N)
            - 2)Hash Table - collision is avoided with
                - Chaining - possible hash functions:
                division = number mod prime;
                multiplication = floor(2^prime (k * A - floor(k * A))), 0 < A < 1 (golden ratio)
                - Open Addressing - hash with f:Ux{0,...,m-1}-->{0,...,m-1}
                linear(key, index) = (hash(key) + index) mod m
                double - if collision - rehash with different hash function
            perfect hashing - static table with only search operation
        - Operations
            - Search - 1)O(height) / O(1 + stored_count/table_size)
            - Insert - 1)O(height) / O(1 + stored_count/table_size)
            - Delete - 1)O(height) / O(1 + stored_count/table_size)

13. **(11-2)Linear time heap construction:**
    - Start with level (height-1) (roots of minimal heaps) and balance them, continue upwards
    - Time complexity: O(N) - number of steps - sum(j=1, h) j/2^j = 2 - 1/(2^(h-1)) = 2

14. **(12)Divide and Conquer:**
    1. *Merge sort* - 4.1 but recursive
        - Space complexity: O(N)

    2. *Quick Sort* - not in-place
        if start < end (indexes) left = start, right = end
        1)choose pivot - (average case time requires good pivot selecting - QuickSelect/MedianOfMedians)
        2)iteratively tighten the interval until a[left] > pivot and a[right] < pivot
        3)swap a[left] and a[right]
        4)++left, --right
        5)recursively proceed with (start,right) and (left,end)
        - Input: [ integer ]
        - Output: [ integer ]
        - Time Complexity: O(N^2)
        - Space Complexity: O(N)

15. **(13)Graph algorithms:**
    1. *Graph representation*
        - Incidence matrix
        - Adjacency list

    2. *DFS* - detect cycles; detect components; detect strongly-connected components (G directed);
    decide if graph is drawable
        - Additional structures
            - order[vertex]
            - parent[vertex]
        - Input: Graph
        - Output: order
        - Time Complexity: O(N + M)
        - Space Complexity: O(N)

    3. *Topological order* - for every (v_i, v_j) => i < j
        - G acyclic <=> G has topological order
        - Input: Graph
        - Output: order
        - Time Complexity: O(N + M)
        - Space Complexity: O(?)

    4. *BFS* - shortest path;
        - Additional structures
            - distance[vertex]
            - parent[vertex]
        - Input: Graph
        - Output: distance
        - Time Complexity: O(N + M)
        - Space Complexity: O(N)

16. **(14)Basic methods of algorithm design:**
    1. *Precomputing* - precompute input data to speedup algorithm execution;
    improves time complexity, worsens space complexity
        - Soucet useku v pole
        - Soucet souvisle podmatice
        - Maximalni jednickova podmatice

    2. *Greedy algorithm* - local optimum leads to global
        - Doesn't work on:
            - Change problem (depends on input coins)
        - Lecture time planning - choose ending first (+proof)

    3. *Divide and Conquer* - composition of solutions to subproblems gives the solution to a problem

    4. *Dynamic programming* - store results of subproblems to get rid of overlapping
        - Fibonacci numbers
        - Longest common subsequence


17. **Binary Heap**
    1. Properties:
        - Shape: all levels of the tree (except last) are fully filled
        - Heap: node key (>= or <=) children nodes' keys
    2. Operations:
        - Search:       O(N)
        - Insert:       O(log N)
        - Find-Min:     O(1)
        - Delete-Min:   O(log N)
    3. Storage: in array - node a[i] has children a[2i + 1] and a[2i + 2]
    (and in reverse a[(i-1)//2] and a[i])
    4. Construction of max heap in O(N):
        1. Start with leaves - valid trivial heaps
        2. Starting with element N/2 (inner nodes) each element is made a root of a previously
        constructed heap using `siftdown(array, start_index, end_index)` operation:
            0. Heap root element is at *start_index* all children heaps of which are valid
            *root* = *start_index*
            1. Repeat until root's left child > end:
                1. Find index of *left_child* of root and mark root index as candidate to *swap*
                2. If left child is larger than swap candidate - make it a swap candidate
                (*array[swap]* < *array[left_child]*) => *swap* = *left_child*
                3. If right child is larger than swap candidate - make it a swap candidate
                (*left_child* + 1 <= *end* AND *array[swap]* < *array[left_child + 1]*) => *swap* = *left_child + 1*
                4. If swap index is still root index - max heap is done - return
                (*swap* == *root*)
                5. Else swap root element with candidate and proceed further 
                `swap(array[root], array[swap])`
                *root* = *swap*
