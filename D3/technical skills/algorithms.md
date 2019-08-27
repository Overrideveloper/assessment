# Algorithm

### Expectation
The Developer understands and can implement high-performance data retrieval over complex, structured data sets such as:

- Search: Breadth / depth first search, A* search
- Sorting (heap sort, quick sort, merge sort, insertion sort)
- Hashing: Knowledge of what hash algorithms are and what problems they can address (MD5, collisions, linear probing)

### Justification

#### Search
Searching Algorithms are designed to check for an element or retrieve an element from any data structure where it is stored.

##### Breadth-First Search
This is search algorithms used to traverse a tree data structure. it could start at any arbitrary node or the root node and ensures it visits all nodes on the current depth level(sibling nodes) before moving to nodes on the next depth level.
```
class Queue {
  
  constructor(){
    this.list = [];
  }

  addToQueue(item){
    this.list.push(item)
  }
  
  removeFromQueue(){
    return this.list.shift();
  }
  
  isEmpty(){
    return this.list.length === 0;
  }
}

const breadthFirstTraverse = (graph, root) => {
  let nodeInfo = [];

  graph.forEach(node=>{
    nodeInfo.push({distance: null, previousNode: null})
  })
  
  nodeInfo[root].distance = 0;
  
  let queue = new Queue();
  queue.addToQueue(root);
  
  while(!queue.isEmpty()){
    let node = queue.removeFromQueue();
    
    graph[node].forEach(neighbour=>{
      if(nodeInfo[neighbour].distance === null){
        nodeInfo[neighbour].distance = nodeInfo[node].distance + 1;
        nodeInfo[neighbour].previousNode = node;
        queue.addToQueue(neighbour);
      }
    })
  }
  return nodeInfo;
}

```

##### Depth-First Search
Unlike Breadth-First, DFS visits the child vertices before visiting the sibling vertices. It traverses the depth of any particular path before exploring its breadth. A stack (often the program's call stack via recursion) is generally used when implementing the algorithm.

Following is how a DFS works:
- Visit the adjacent unvisited vertex. Mark it as visited. Display it. Push it in a stack.
- If no adjacent vertex is found, pop up a vertex from the stack. (It will pop up all the vertices from the stack, which do not have adjacent vertices.)
- Repeat Rule 1 and Rule 2 until the stack is empty.

```
class Stack {
  
  constructor(){
    this.list = [];
  }

  addToStack(item){
    this.list.push(item)
  }
  
  removeFromStack(){
    return this.list.pop();
  }
  
  isEmpty(){
    return this.list.length === 0;
  }
}
const depthFirstTraverse = (graph, root)=> {
  let nodeInfo = [];
  
  graph.forEach(node=>{
    nodeInfo.push({distance: null, previousNode: null})
  });

  nodeInfo[root].distance = 0;

  let stack = new Stack();
  stack.addToStack(root);
  
  while(!stack.isEmpty()){
    let node = stack.removeFromStack();
 
    graph[node].forEach(neighbour=>{
      if(nodeInfo[neighbour].distance === null){
        nodeInfo[neighbour].distance = nodeInfo[node].distance + 1;
        nodeInfo[neighbour].previousNode = node;
        stack.addToStack(neighbour);
      }
    })
  }
  return nodeInfo;
}
```
sample adjacency list used: 
```
let adj = [
    [1],
    [0, 4, 5],
    [3, 4, 5],
    [2, 6],
    [1, 2],
    [1, 2, 6],
    [3, 5],
    []
    ];

```