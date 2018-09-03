# Algorithms
An algorithm is a step by step sequence of actions that if followed solves instances of a specific problem. Algorithms can perform calculation, data processing and automated reasoning tasks. Some algorithms perform faster than others even if they produce an equal result. Usually, the fewer steps it takes for an algorithm to solve the problem, the better. Sometimes we care about other factors like how much memory it uses or consumes. The relationship of input size to the number of steps it takes to run characterizes the complexity of the algorithm. The complexity of an algorithm gives an approximation of how fast or slow an algorithm is going to be and how much memory usage it will consume.

The performance of an algorithm is measured based on the following properties:
- Time Complexity. A representation of the amount of time required by the algorithm to complete its task.
- Space Complexity.  The amount of memory space required by the algorithm, during the course of its execution.

**Linear Search**
----------------------------------------
Is a method for finding a target value within a list. It sequentially checks each element of the list for the target value until a match is found or until all the elements have been searched. Linear search runs in at worst linear time and makes at most n comparisons, where n is the length of the list.

Example - Basic Linear Search
***
```
function linearSearch(arr, item){
  for(let index=0; index < arr.length; index++){
    if(item === arr[index])
      return index
  }
  return 'Item does not exist'
}
```

**Binary Search**
----------------------------------------
Is a search algorithm that finds the position of a target value within a sorted array. Binary search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target value, and repeating this until the target value is found. If the search ends with the remaining half being empty, the target is not in the array. Even though the idea is simple, implementing binary search correctly requires attention to some subtleties about its exit conditions and midpoint calculation.

Binary search runs in logarithmic time in the worst case, making O(log n) comparisons, where n is the number of elements in the array, the O is Big O notation, and log is the logarithm. Binary search takes constant (O(1)) space, meaning that the space taken by the algorithm is the same for any number of elements in the array.

Example - Binary Search
***
```
function binarySearch(arr, item){
  if(arr.length === 0){
    return 'item not found'
  }else{
    let minIndex = 0, maxIndex = arr.length - 1;
    while(minIndex <= maxIndex){
      let midIndex = Math.floor(minIndex + maxIndex / 2);
      if(arr[midIndex] === item){
        return midIndex;
      }else{
        if(arr[midIndex] > item){
          maxIndex = midIndex - 1;
        }else{
          minIndex = midIndex + 1;
        }
      }
    }
  }
}
```
