# Topological Sort (Graph)

### Common coding patterns

### Definition
Useful for finding a linear ordering of elements that have dependencies on each other. Should be used for graph problems to provide a partial ordering among the vertices of a graph.

Start by storing the graph in adjacency list using a hash table. The order by starting with one of sources and ending at one of the sinks.

  -- source - node with no incoming edge and only outgoing edges
  -- sink - node with only incoming edges and no outgoing edges

Only possible when graph has no directed cycles.For topological sorts, we use Breadth First Search (BFS)

### Associated Time / Space Complexity
Time Complexity - O(V + E)
Space Complexity - O(V + E)

### When to Use
Determine elements of a graph that have dependencies on each other.

### Common Operations / Implementation

(1) store graph in adjacency list using hash table
(2) build separate graph with num of in-degress (incoming edges) of each vertex
  -- vertices with 0 in-degres are sources
(3) store all vertices with 0 in-degrees in a queue
(4) go through queue to add the queue to a list, get all children from the graph, decrement the in-degree of the child by 1, and add those children to the queue if their in-degree becomes 0
(5) if one or more elements in the target vertices are not in the sorted list, then there is a cyclic dependency

```
course schedule problem

function findOrder(numCourses: number, prerequisites: number[][]): number[] {
    const adjacencyList: {[index: number]: number[]} = {};
    const degreesList: {[index: number]: number} = {};
    
    for (let i = 0; i < numCourses; i++) {
       degreesList[i] = 0;
    }
    
    // generate adjacency and degrees map
    prerequisites.forEach((pair) => {
        const course = pair[0];
        const prereq = pair[1];
        
        if (prereq in adjacencyList) {
            adjacencyList[prereq].push(course);
        } else {
            adjacencyList[prereq] = [course];
        }
        
        degreesList[course]++;
    })
        
    const clearedCourseQueue = new CustomQueue();
    let coursesTaken = [];

    Object.keys(degreesList).forEach((course) => {
        if (degreesList[course] === 0) {
            clearedCourseQueue.push(course);
        }
    });
    
    while (!clearedCourseQueue.isEmpty()) {
        const prereq = clearedCourseQueue.pop();
        coursesTaken.push(prereq);
        
        if (prereq in adjacencyList) {
            adjacencyList[prereq].forEach((course) => {
                degreesList[course]--;
                if (degreesList[course] === 0) {
                    clearedCourseQueue.push(course);
                }
            })
        }
    }

    return coursesTaken.length === numCourses ? coursesTaken : [];
};

class CustomQueue {
    private popStack: number[];
    private pushStack: number[];

    constructor() {
        this.popStack = [];
        this.pushStack = [];
    }
    
    push(val) {
        this.pushStack.push(val);
    }
    
    peek() {
        if (this.isEmpty()) return null;
        if (this.popStack.length > 0) return this.popStack[this.popStack.length - 1];
        return this.pushStack[0];
    }
    
    pop() {
        if (this.isEmpty()) return null;
        
        if (this.popStack.length > 0) return this.popStack.pop();
        
        while (this.pushStack.length > 0) {
            this.popStack.push(this.pushStack.pop());
        }
        
        return this.popStack.pop();
    }
    
    isEmpty() {
        return this.popStack.length === 0 && this.pushStack.length === 0;
    }

    size() {
        return this.popStack.length + this.pushStack.length;
    }
}
```

### Resource Links
* [Toplogical Sort](https://emre.me/coding-patterns/topological-sort/)

