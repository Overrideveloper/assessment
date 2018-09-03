# Graph
A graph is a set of interconnected objects where some pairs of the objects are connected by links. The interconnected objects are called vertices(V), and the links that connect the vertices are called edges(E). Formally, a graph is a pair of sets (V, E).
Graph is basically divided into two broad categories:

- Directed Graph (Di- graph) – Where edges have direction.
- Undirected Graph – Where edges do not represent any directed

**Adjacency**
----------------------------------------
Two vertices are adjacent if they are connected to each other through an edge.

**Path**
----------------------------------------
Path − Path represents a sequence of edges between the two vertices.

Example
***
```
class Graph {
  constructor(noOfVertices) {
    this.noOfVertices = noOfVertices;
    this.adjArr = {};
  }

  addVertex(v){
    this.adjArr[v] = [];
  }

  addEdge(v, w) {
    this.adjArr[v].push(w);
    // Since graph is undirected,
    // add an edge from w to w also
    this.adjArr[w].push(v);
  }
  printGraph() {
    // get all the vertices
    let getKeys = Object.keys(this.adjArr);
 
    // iterate over the vertices
    getKeys.forEach(key=>{
      let getValues = this.adjArr[key];
      
    })
    for (let key of getKeys) {
      let getValues = this.adjArr[key];
      console.log(`${key} -> ${getValues.join(' ')}`);
    }
  }

}
```

# Heaps
A heap is a specialized tree-based data structure that satisfies the heap property: if P is a parent node of C, then the key (the value) of P is either greater than or equal to (in a max heap) or less than or equal to (in a min heap) the key of C.The node at the "top" of the heap (with no parents) is called the root node.

Example
***
```
class Heap {
  constructor(){
    this.data = []
  }

  insert(val){
    this.data.push(val);
    this.bubbleUp(this.data.length - 1)
  }
  
  private bubbleUp(index){
    while (index > 0) {
      // get the parent
      let parent = Math.floor((index + 1) / 2) - 1;
      
      // if parent is greater than child
      if (this.data[parent] > this.data[index]) {
        // swap
        let temp = this.data[parent];
        this.data[parent] = this.data[index];
        this.data[index] = temp;
      }
      
      index = parent;
    }
  }
  
  popMin(){
    let min = this.data[0];
  
    // set first element to last element
    this.data[0] = this.data.pop();
    
    // call bubble down
    this.bubbleDown(0);
    
    return min;
  }
  
  bubbleDown(){
    while (true) {
      let child = (index+1) * 2;
      let sibling = child - 1;
      let toSwap = null;
      
      // if current is greater than child
      if (this.data[index] > this.data[child]) {
        toSwap = child;
      }
      
      // if sibling is smaller than child, but also smaller than current
      if (this.data[index] > this.data[sibling] && (this.data[child] == null || (this.data[child] !== null && this.data[sibling] < this.data[child]))) {
          toSwap = sibling;
      }
      
      // if we don't need to swap, then break.
      if (toSwap == null) {
        break;
      }
      
      let temp = this.data[toSwap];
      this.data[toSwap] = this.data[index];
      this.data[index] = temp;
      
      index = toSwap;
    }
  }
}

let heap = new Heap();

heap.insert(5);
heap.insert(4);
heap.insert(9);
heap.insert(6);
heap.insert(1);
heap.insert(10);
heap.insert(2);
heap.insert(7);

console.log(heap.popMin());
console.log(heap.popMin());
console.log(heap.popMin());
console.log(heap.popMin());
```

# Binary Trees
A Binary tree is a set of nodes or a collection of nodes along with two possible references to other nodes(children) that satisfy three conditions.
- references cannot be duplicated
- No node points to the root not
- A node can only have to references to other nodes, commonly called left and right reference
