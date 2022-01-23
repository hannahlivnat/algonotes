# Tree

### Type
Data Structure

### Definition
A tree is a series of nodes (vertices) connected by branches (edges) which are directionless and do not create any cycles. They work based on a hierarchical structure with parent/child nodes and each tree has one root node. Any nodes without children are called leaves. There are several types of commonly used trees

#### Binary Tree
A tree where every node has <= 2 children, referred to as left and right.

#### Binary Search Tree
A sorted binary tree. In a binary search tree, every left descendant is less than the node and every right descendant is great than the node.

#### B-Tree
A B-Tree can have more than 2 child nodes, and each node contains much more data than a bindary search tree to hold a reference to each of its children. Each node contains n keys and will have n + 1 children so all leaves are at the same depth, making them perfectly balances. Good to handling data that can't fit into main memory.

### Trie
A tree-like data structures where the nodes of the tree store the entire alphabet and strings/words can be retrieve by traversing down a branch path of the tree.

Each trie contains an empty root node which links to other nodes representing each possible alphabetic value. We can think of uses for this such as autocomplete, matching algorithms, spellcheckers, searching for substrings/strings in a sentence

### Associated Time / Space Complexity
* Binary search trees have average time complexity of O(log n) for most operations. Worst case would be O(n) time complexity for unbalanced binary search trees.


### When to Use
Trees are used for storing data hierarchically for searching and storage purposes, decision trees, expression evaluation, data compression

i.e. git uses binary search tree for the command "git bisect"

### Common Operations / Implementation

#### Depth-First Traversals
Pre order Traversal (Root, Left, Right)
Reason to use: need to inspect all roots before all of the leaves, create copy of a tree
```
preorderTraversal(root) {
    const output = [];
    const stack = [];
    
    //preorder - nlr
    if (root === null) return;
    stack.push(root);
    
    while(stack.length > 0) {
      const currentNode = stack.pop();
      
      // logic for root node before right/left
      console.log(currentNode.val)
      
      // operating on first in last out model so
      // pushing right first then left, assures that we'll look at left and then right
      if (currentNode.right != null) stack.push(currentNode.right)
      if (currentNode.left != null) stack.push(currentNode.left)
 
    }
};
```

Post order Traversal (Left, Right, Root)
Reason to use: need to explore all leaves before any nodes, delete tree from leaf to root
```
postorderTraversal(root) {
  // postorder = lrn
  if (root === null) return;

  postOrderTraversal(root.left);
  postOrderTraversal(root.right);

  // execute logic for root node
  // after all leaves are traversed
  console.log(root.val)
};
```

In order Traversal (Left, Root, Right)
Reason to use: need to flatten tree back to original sequence to
flow inherent node sequence, get values of nodes in non-decreasing order in a binary search tree, get in order successor when deleting node with two children
```
inorderTraversal(root) {
  // inorder lnr
  if (root === null) return;

  postOrderTraversal(root.left);

  // execute logic for root node
  // after all leaves are traversed
  console.log(root.val)

  postOrderTraversal(root.right);
};
```

#### Breadth-First / Level Order Traversal
Starts with root and then examples left - right children at each level
Reason to Use: Find the shortest path, find how much distance is between two nodes

```
bfs(root) {
  if (root === null) return;
  const queue = new Queue();
  const seen = new Set();

  queue.enqueue(root);

  while(!queue.isEmpty()) {
    const node = queue.dequeue();

    //logic for current node here
    console.log(node.val);

    // queues operate with fifo
    if (node.left != null) queue.enqueue(node.left);
    if (node.right != null) queue.enqueue(node.right);
  }
}
```

### Binary Tree Basic Operations

### Binary Search Tree Basic Operations

Search
```
searchBinarySearchTree(root, key) {
  // handle base cases
  if (root === null || root.key === key) return root;

  // If the key is larger than the root's key, move search to right
  // if not, move search to the left
  if (root.key < key) return search(root.right, key);
  return search(root.left, key)
}
```

Insert Node
```
insertNodeInBinarySearchTree(root, key) {
  // If root is empty, return new node
  if (root === null) return Node(key);

  if (root.val === key) return root;

  if (root.val < key) {
    root.right = insertKeyInBinarySearchTree(root.right, key);
  } else {
    root.left = insertKeyInBinarySearchTree(root.left, key)
  }

  return root;
}

```

Delete Key
```
deleteNodeFromBinarySearchTree(root, key) {
  // base case
  if (root === null) return root;

  // Haven't found the key to delete yet
  // Choose which direction to search in
  if (key < root.key) {
    root.left = deleteNodeFromBinarySearchTree(root.left, key);
    return root;
  } 

  if (key > root.key) {
    root.right = deleteNodeFromBinarySearchTree(root.right, key);
    return root;
  }

  // we've found node to delete
  let temp;

  // Case 1: Node has 0 children
  if (root.left === null && root.right === null) return null;

  // Case 2: Node has 1 child
  if (root.left === null) {
    temp = root.right;
    root = null;
    return temp;
  }

  if (root.right === null) {
    temp = root.left
    root = null;
    return temp;
  }

  // Case 3: Node has 2 children
  // (1) set in order successor, the right subtree's leftmost child
  successor = curr.right
  while (successor.left != null) {
    successor = successor.left;
  }

  // (2) store successor valure and delete successor
  successorVal = successor.data;
  deleteNode(root, successor.data);

  // (3) copy successor value to current node
  root.data = succesorVal;
} 
```

### Resource Links
* [Applications of Binary Trees](https://www.baeldung.com/cs/applications-of-binary-trees)
* [Trying to Understand Tries](https://medium.com/basecs/trying-to-understand-tries-3ec6bede0014)
* [CS50 Tries](https://youtu.be/TRg9DQFu0kU)
* [Trees BaseCS](https://medium.com/basecs/how-to-not-be-stumped-by-trees-5f36208f68a7)
* [Binary Search Tree Operations](https://www.geeksforgeeks.org/binary-search-tree-set-1-search-and-insertion/)

