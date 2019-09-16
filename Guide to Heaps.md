# Heaps in Java 
Implement PriorityQueues
Usually a min heap but can be max heap using Collections.reverseOrder()

```
PriorityQueue<Integer> min = new PriorityQueue<Integer>();
PriorityQueue<Integer> max = new PriorityQueue<Integer>(Collections.reverseOrder());
```

## Useful functions:
boolean add(E element): This method inserts the specified element into this priority queue.
public remove(): This method removes a single instance of the specified element from this queue, if it is present
public poll(): This method retrieves and removes the head of this queue, or returns null if this queue is empty.
public peek(): This method retrieves, but does not remove, the head of this queue, or returns null if this queue is empty.
Iterator iterator(): Returns an iterator over the elements in this queue.
boolean contains(Object o): This method returns true if this queue contains the specified element
void clear(): This method is used to remove all of the contents of the priority queue.
boolean offer(E e): This method is used to insert a specific element into the priority queue.
int size(): The method is used to return the number of elements present in the set.
--> toArray(): This method is used to return an array containing all of the elements in this queue.
Comparator comparator(): The method is used to return the comparator that can be used to order the elements of the queue.
