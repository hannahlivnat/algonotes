# Search

### Type
Algorithm

### Definition
Patterned search methods, often for exploring nodes in a tree or graph. the Most common are Depth-First Search (DFS) and Breadth-First search (BFS).

* Depth-First Search: Searches tree/graph deeply using Last In First Out method with the help of a stack (either stack data structure or call stack via recursion)
* Breadth-First Search: Searches tree/graph widely using First In First Out method with the help of a queue

### Associated Time / Space Complexity
* Time complexity for both is O(n) because every node is visited once
* Space compexity varies depending on algorithm / data structure
* Depth First Search generally require less memory than Breadth-First search. Space complexity for BFW is O(w), where w is the max width of the tree. Space complexity for BFS is O(h), where h is the max height of the tree.

### When to Use
* DFS - use for complete search, exhausting possible paths, backtracking
* BFS - use for checking if path exists between two nodes, finding how far / how many "levels" away one connection is from another

### Common Operations / Implementation

Depth-First Search For Graph
```
dfs(start) {
  // Helping Data Structures
  const stack = new Stack();
  const seen = new Set();

  stack.push(start);

  while(!stack.isEmpty()) {
    // Last in first out
    let curr = stack.pop();

    if (!seen.has(curr)) {
      seen.add(curr);

      //Search logic goes here
      console.log(curr);
    }

    // If searching a graph with an adjacency list
    // add next adjacent nodes to search
    curr.adjacent.map((node) => {
      if (!seen.has(node)) stack.push(node);
    })
  }
}
```

Depth-First Search For Binary Tree
** Implementation will change depending on which traversal type is being used (In-order, Pre-order, Post-order). The following example uses preorder traversal and recursion

```
dfs(root) {
  // handle null case
  if (root === null) return;

  // Search logic goes here
  console.log(root);

  // Search left tree
  dfs(root.left);

  // Search right tree
  dfs(root.right);
}
```
Breadth-First Search For Graph

```
bfs(node) {
  // set up data structures
  const queue = new Queue();
  const seen = new Set();

  // add starting node to search
  queue.enqueue(node);

  while(!queue.isEmpty()) {
    // Use FIFO
    const curr = queue.dequeue();

    // should only process each node once
    if (!seen.has(curr)) {
      seen.add(curr);

      //search logic goes here
      console.log(curr);
    }

    // If searching a graph with an adjacency list
    // add next adjacent nodes to search
    curr.adjacent.map((node) => {
      if (!seen.has(node)) queue.enqueue(node)
    })
  }
}
```

Breadth-First Search For Binary Tree
** Also uses pre order traversal

```
bfs(root) {
  // handle null case
  if (root === null) return;

  const queue = new Queue();

  queue.enqueue(root);

  while(!queue.isEmpty()) {
    const node = queue.dequeue();

    // search logic goes here
    console.log(node)

    // add left tree to queue
    if (node.left != null)  queue.enqueue(node.left);

    // add right tree to queue
    if (node.right != null) queue.enqueue(node.right);
  }
}

```

### Resource Links
* [Interview Cake - Breadth First Search](https://www.interviewcake.com/concept/javascript/bfs?)
* [Interview Cake - Depth First Search](https://www.interviewcake.com/concept/javascript/dfs)
* [Back to Back SWD - BFS and DFS Video](https://youtu.be/TIbUeeksXcI)
* [DFS Traversal Example From Geeks For Geeks](https://www.geeksforgeeks.org/dfs-traversal-of-a-tree-using-recursion/)
* [BFS Traversal Example From Geeks For Geeks](https://www.geeksforgeeks.org/level-order-tree-traversal/)

