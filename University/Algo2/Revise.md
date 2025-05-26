Definitions - Graphs

BFS + DFS: https://www.youtube.com/playlist?list=PL9xmBV_5YoZMIAJn8M6At9CjZ0Wu0B31d
- BFS FIFO Queue O(n+m)
- DFS FILO Stack O(n+m)
- Topological Sort (~DFS) Directed Acyclic Graph

Greedy = Find optimal solution to problem by making locally optimal choice at each step 
Krusal 
Prim: https://www.youtube.com/playlist?list=PL9xmBV_5YoZPKwb4XPB1sG7S6kNpN9JJo
Dijkstra: https://www.youtube.com/playlist?list=PL9xmBV_5YoZO-Y-H3xIC9DGSfVYJng9Yw \[SSSP]
\[SPSP] **Single pair shortest path problem**
- Find shortest path from s to t 
\[SSPP] or \[SSSP] **Single source shortest path problem**
- Single source or target vertex v is specified, find shortest paths from v to every other vertex u $\in$ V \ {v}
\[APSP] **All Pairs shortest path problem**
- Find shortest path from s to t for every s,t $\in$ V

Chain Product W/ Recurrence
M\[i,i] = 0 
M\[i,j] = min(i<=k<j){M\[i,k] + d(i-1)d(j)d(k) + M\[k+1,j]}

Matrix Multiplication Algorithm
Floyd-Warshall: https://www.youtube.com/playlist?list=PL9xmBV_5YoZO-Y-H3xIC9DGSfVYJng9Yw
CYK Algorithm 
TSP
Problem Variants \[SPSP] \[SSSP] \[APSP]

Direct, Guessing, Master Method
Maximum Independent Set
Karatsuba's Algorithm
Strassen's Algorithm

Priority Queue
Binary Heap
Binomial Tree, Heap
Dictionary
Fibonacci Heap: https://www.youtube.com/playlist?list=PL9xmBV_5YoZNkwWDXcSiZjMgacw2P0U2j

Hash Table
- Collisions,
- Chaining,
- Insertion,
- Etc...

Binary Tree
Tree Traversal: https://www.youtube.com/playlist?list=PL9xmBV_5YoZO1JC2RgEi04nLy6D-rKk6b
- Inorder
- Preorder
- Postorder
Binary Search Tree
Red-Black Tree: https://www.youtube.com/playlist?list=PL9xmBV_5YoZNqDI8qfOZgzbqahCUmUEin
AVL-Tree: https://www.youtube.com/playlist?list=PL9xmBV_5YoZOUFgdIeOPuH6cfSnNRMau-
B-Tree: https://www.youtube.com/playlist?list=PL9xmBV_5YoZNFPPv98DjTdD9X6UI9KMHz
B*-Tree