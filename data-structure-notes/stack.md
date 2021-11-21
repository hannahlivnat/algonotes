# Stack

### Type
Linear Data Structure

### Definition
Linear data structure serving as a collection of items following Last In First Out behavior, like a stack of plates

### Associated Time / Space Complexity
Time complexity of insertions/deletions is O(1). Space complexity can range from O(1) to O(n) depending on whether you're storing n items or pushing/popping each item.

### When to Use
Depth First Search, Call Stack, string parsing problems such as bracker pair validator, finding a path

### Common Operations / Implementation

#### Dynamic Array Stack
```
code stack = [];

// OR

class Stack {
  constructor() {
    this.stack = [];
  }

  push(item) {
    this.stack.push(item)
  }

  pop(){
    if (this.stack.length === 0) return;

    return this.stack.pop();
  }

  isEmpty() {
    return this.stack.length === 0;
  }
}
```
#### Linked List Stack

```
class Stack {
  constructor() {
    this.first = null;
    this.last = null;
  }

  // add new node to beginning of list
  push(item) {
    let node = new Node(item);

    if (!this.first) {
      this.first = node;
      this.last = node;
    } else {
      let temp = this.first;
      this.first = node;
      this.first.next = temp;
    }
  }

  // remove first node in the list
  pop() {
    if (!this.first) return null;
    let temp = this.first;

    if (this.first === this.last) {
      this.last = null;
    }

    this.first = this.first.next;

    return temp.data;
  }

  isEmpty() {
    return this.first === null && this.last === null;
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
* [BTB Balanced Parentheses Problem](https://backtobackswe.com/platform/content/the-balanced-parentheses-problem)
* [Interview Cake Stack Definition](https://www.interviewcake.com/concept/javascript/stack?)

