# Queue

### Type
Abstract Data Type

### Definition
A queue is an abstract data type which supports First in First Out behavior (FIFO). It's required to support the following functiontality: 
* enqueue (add to the queue)
* dequeue (remove from the queue using FIFO)
* peek (see next item up in queue)
* isEmpty (see if queue is empty)

It can be implemented using linear data types like a stack or linked list.

### Associated Time / Space Complexity
A queue can have an amortized time complexity of O(1) for insertions/deletions. Space complexity can range from O(1) - O(n) depending on storage requirements for accompanying algorithm.

### When to Use
* Breadth First Search
* Resolving requests / orders
* Anything that should be processed in the order that it was received (i.e. printer job queue, web server request queue, CPU process scheduler queue)

### Common Operations / Implementation

#### Implement a Stack Queue

```
class Queue {
  constructor() {
    // use 2 stacks to maintain FIFO behavior in O(1) amortized time
    this.pushStack = [];
    this.popStack = [];
  }

  enqueue(val) {
    this.pushStack.push(val);
  }

  dequeue() {
    // only move items over from push stack if pop stack is empty
    if (this.popStack.length === 0) {
      while(this.pushStack.length > 0) {
        this.popStack.push(this.pushStack.pop());
      }

      if(!this.popStack.length > 0) {
        return;
      }
    }
    
    return this.popStack.pop();
  }

  isEmpty() {
    return this.pushStack.length === 0 && this.popStack.length === 0;
  }
}
```

#### Implement a Linked List Queue
```
class Queue {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  // node is inserted at end of list
  enqueue(item) {
    const node = new Node(item);
    if (this.head === null) {
      this.head = node;
    } else {
      this.rear.next = node;
    }

    this.rear = node;
  }

  // return node from head of list
  dequeue() {
    if (this.head === null) return;

    let temp = this.head;
    this.head = this.head.next;

    if (this.head === null) {
      this.rear = null;
    }

    return temp.data;
  }

  peek() {
    if (this.head === null) return;
    return this.head.data;
  }

  isEmpty(){
    return this.head === null && this.read === null;
  }

}

class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}
```

### Resource Links
* [Interview Cake Definition](https://www.interviewcake.com/concept/javascript/queue?)
* [BTB SWE Queue Problem](https://backtobackswe.com/platform/content/the-balanced-parentheses-problem)
* [BTB SWE Queue With Stacks Video](https://youtu.be/Wg8IiY1LbII)