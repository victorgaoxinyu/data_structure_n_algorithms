## Graph
- G = (V, E)
- G: Graph
- V: Set of Verticies
- E: Set of Edges
- |V|: Number of Vertices
- |E|: Number of Edges

Directed Edge
e1 = (v1, v2)  # (ori, dest)

Undirected Edge
e1 = {v1, v2}  # set

Graph:
- Weighted Graph
  - edge also contain value
- Unweighted Graph

## Graph Representation
- Edge Lists
- Adjacency Matrices
- Adjacency Lists

### Edge List
```
            [0]-----[1]
            / \      | \
           /   \     |  \
         [5]    \    |  [2]
           \     \   |   /
            \     \  |  /
             \     \ | /
             [4]----[3]

```
Unweighted Graph
[(0,1), (0,3), (0,5), (1,2), (1,3), (2,3), (3,4), (4,5)]

Weighted Graph
[(0,1,*3*), (0,3,*2*), (0,5,*2*), (1,2,*3*), (1,3,*2*), (2,3,*4*), (3,4,*1*), (4,5,*4*)]

### Adjacency Matrix
```
undirected, so the matrix is symmetric
    0 1 2 3 4 5
    ------------
0 | 0 1 0 1 0 1
1 | 1 0 1 1 0 0
2 | 0 1 0 1 0 0
3 | 1 1 1 0 1 0
4 | 0 0 0 1 0 1
5 | 1 0 0 0 1 0
```
### Adjacency List
- to handle sparse graph/Matrix
- most common implementation for graph, especially for coding interview
- efficient whtn lots of vertices but not many edges
```
0 -> 1,3,5
1 -> 0,2,3
2 -> 1,3
3 -> 0,1,2,4
4 -> 3,5
5 -> 0,4
```

Time Complexity
1. O(1): Get all adjacent vertices for a specific vertex
2. O(d): Searching for an edge between two vertices,
   - d: degree of the vertex
   - worst case d = |V| - 1

Space Complexity
- worst case, all V connected
- 2 * E

#### Implementation
```
        [Anna]
        /    \
       /      \
    [Bob]---[Dave]  
```
Hashmap
```c
// string: GraphVertex*
{
    Anna: 0x0022,
    Bob:  0x0073,
    Dave: 0x00E3
}
```
C Implementation
```c
Graph {
    HashMap < string, GraphVertex* > vertices;
}

GraphVertex {
    string name;
    AdjacencyList* edges;
}

AdjacencyList {
    Node* head
}

Node {
    GraphVertex* value;
    Node* next
}
```

Python Implementation
```py
class GraphVertex:
    def __init__(self, name):
        self.name = name
        self.edges = []
```

## Graph Search
Graph Exploring
- Visit all nodes
- Find all nodes reachable from a vertex
- Find the shortest path from one vertex to another

### Breadth-first Search (BFS)
- Use a Queue to store the vertices that have been discovered.
- pop 1 vertex off the front of the Queue, start exploring and push vertices to Queue if not discovered before.
- Keep doing step 2 until the Queue is empty

Pseudocode
```
function BST (v0) {
    q = new Queue
    mark all vertices undiscovered
    q.enqueue(v0)
    mark(v0) = discovered

    while q not empty {
        v = q.dequeue()
        // explore v
        for each neighbour u of v {
            if mark(u) != discovered {
                mark(u) = discovered
                q.enqueue(u)
            }
        }
    }
}
```

### Depth-first Search (DFS)
