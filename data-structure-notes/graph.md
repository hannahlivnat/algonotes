# Graph

### Type
Non-Linear Data Structure

### Definition
Graphs are defined as node/vertices connected by edges (G = (V,E)). They are used to show connections and relationships. Graphs can be directed / undirected, cyclic / acyclic, and weighted/unweighted. Graphs with few connections are defined as sparse while those with many connections are dense.

Graphs are represented with...
* Edge Lists: A nested array of edges

  ```
    [[0,1], [1,2], [1,3], [3,3]]
  ```
* Adjacency List: Can be stored as 2D array or Linked List / Object where each index or key represents a node and the value at that index/key represents all it's neighbors

  ```
  // List
  [[1], [0,2,3], [1,3], [1,2]]

  // Object
  { 0: [1], 1: [0,2,3], 2: [1,3], 3: [1,2]}
  ```
* Adjacency Matrix: Matrix of 0's and 1's indicating connection of the node at key/index to each node represented by the nested index/key

  ```
    [
      [0,1,0,0],
      [1,0,1,1],
      [0,1,0,1],
      [0,1,1,0]
    ]
  ```

### Associated Time / Space Complexity
Most time complexities for graph operations come out to O(n*log(n)) or more, which is a scaling weakness. Space complexity depends on the type of graph. i.e. adjacency lists can vary between O(v + e) - O(n<sup>2</sup>) depending on underlying structure. Adjacency matrix would be O(n<sup>2</sup>)

### When to Use
Solving any problems having to do with connections, relationships, paths/mazes

### Common Operations / Implementation

#### Construct an Adjacency List From Edge List
```
const convertEdgeListToAdjacencyList = (edgeList) => {
  const adjacencyList = new Graph();
  edgeList.map((edgePair) => {
    adjacencyList.add(edgePair[0], edgePair[1]);
    adjacencyList.add(edgePari[1], edgePair[0]);
  })

  return adjacencyList;
}

class Graph {
  constructor() {
    this.adjacencyList = {};
  }

  add(node, adjacentVertex) {
    if (node in this.adjacencyList) {
      this.adjacencyList[node].push(adjacentVertex);
    } else {
      this.adjacencyList[node] = [adjacentVertex];
    }
  }

  printAdjacentNodes(node) {
    if (!node in this.adjacencyList) return [];

    return this.adjacencyList[node];
  }
}
```

### Find Path In Graph Using Adjacency List and DFS

```
const dfs = (adjacencyList, start, end) => {
  const stack = new Stack();
  const seen = new Set();

  stack.push(start);

  while(!stack.isEmpty()) {
    const currNode = stack.pop(); //LIFO

    if (currNode === end) return true;

    if (!seen.has(currNode)) seen.add(currNode);

    graph.printAdjacentNodes(currNode).map((node) => {
      if(!seen.has(node)) stack.add(node);
    })
  }

  // If you made if through the stack and did not find the end
  // you've failed to find path
  return false;
}
```

### Resource Links
* [Interview Cake](https://www.interviewcake.com/concept/javascript/graph?)
* [Graph Fundamental](https://backtobackswe.com/platform/content/graphs-fundamentals)

