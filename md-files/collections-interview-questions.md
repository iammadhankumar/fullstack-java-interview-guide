# Collections Interview Questions

#### 1. Explain about collection frame work hierarchy ?
The Java Collections Framework provides a set of interfaces and classes for storing and manipulating groups of objects.</br>
The `Collection` interface is the root interface in the Java Collections Framework. It is a parent interface for the `List`, `Set`, and `Queue`.</br></br>
<b>List:</b> Ordered collection that allows duplicate elements (e.g., ArrayList, LinkedList).</br>
<b>Set:</b> Unordered collection that does not allow duplicate elements (e.g., HashSet, TreeSet).</br>
<b>Queue:</b> Collection that represents FIFO(First-in-First-out) principle (e.g., PriorityQueue, LinkedList).</br></br>
<b>Map:</b> A collection that maps keys to values (e.g., HashMap, TreeMap).

#### 2. What is ArrayList ?
An `ArrayList` in Java is a dynamic array used to store and manage a list of elements. It allows adding, removing, and accessing elements by their position. It is a flexible array that can grow or shrink as elements are added or removed. `ArrayList` is preferred when frequent access to elements is needed.

#### 3. What is LinkedList ?
A `LinkedList` is a collection of items where each item points to the next one. It uses a node structure, where each node contains an element and a reference to the next node. `LinkedList` is preferred when frequent insertion and deletion is needed.

#### 4. What is HashSet ?
A `HashSet` is a collection in Java that stores unique items. It doesn’t allow duplicates and doesn’t maintain any order. It uses the hashtable to store and retreive elements.

#### 5. What is TreeSet ?
A `TreeSet` is a collection in Java that stores unique items in a sorted order. It automatically arranges the items from lowest to highest, and it doesn’t allow duplicates.

#### 6. What is HashMap ?
A `HashMap` is a collection in Java that stores key-value pairs. Each key is unique and maps to a specific value. 
HashMap provides useful methods like:
put(K key, V value) to add or update data,
get(Object key) to fetch a value,
remove(Object key) to delete a pair,
containsKey(Object key) to check for a key, and
containsValue(Object value) to check for a value.

#### 7. What is TreeMap ?
A `TreeMap` is a collection in Java that stores key-value pairs in a sorted order based on the keys. It keeps the keys in a natural ascending order and doesn’t allow duplicate keys.

#### 8. What is Vector ?
A `Vector` is a type of list in Java that stores elements and can grow or shrink in size. It’s similar to an `ArrayList`, but it is synchronized, meaning it is thread-safe and can be used safely in a multi-threaded environment.

#### 9. What is Stack ?
A `Stack` is a collection where items are added and removed in a last-in, first-out (LIFO) order. It removes the most recently added element first and extends the Vector class in Java.</b></br>
<b>Basic Operations:</b> push, pop, peek.

#### 10. What is Queue ?
A `Queue` is a collection where items are added and removed in a first-in, first-out (FIFO) order. It removes the elements in the order they were added.</br>
<b>Basic Operations:</b> Enqueue, Dequeue, peek.

#### 11. What is hashcode ?
A hash code is a number used to efficiently locate and organize objects in collections like `HashMap`, `HashSet` and `Hashtable`. When elements are added to these collections, a hash code is generated for each one.

#### 12. What is LinkedHashSet ?
A `LinkedHashSet` is a collection in Java that stores unique items and maintains their order of insertion. It combines the features of both `LinkedList` and `HashSet`, ensuring that items are ordered as they were added and do not contain duplicates.

#### 13. What is LinkedHashMap ?
A `LinkedHashMap` is a collection in Java that stores key-value pairs and maintains the order in which the keys were added. It combines the features of both `LinkedList` and `HashMap`, ensuring that the order of keys remains consistent and unique.

#### 14. What is a Comparable interface ?
The `Comparable` interface in Java is used to define a natural order of sorting objects within a class. It uses the `compareTo` method to compare objects and determine their order.

#### 15.  What is a Comparator interface ?
The `Comparator` interface in Java is used to define a custom order for sorting objects. It uses the `compare` method to compare objects and determine their order.

#### 16. How to make ArrayList Read Only ?
To make an ArrayList read-only in Java, We can use `Collections.unmodifiableList()` to wrap the list. This creates a view of the list that prevents modifications, ensuring it can be read only.

#### 17. What is Iterator ?
An `Iterator` is an object in Java used to iterate over elements in a collection. It moves through the elements in a forward direction and provides methods like `next()` and `hasNext()`.</br></br>
`next()` is used to get the next element in the collection.</br>
`hasNext()` is used to check if there are more elements in the collection.

#### 18. What is ListIterator ?
A ListIterator is a special type of iterator in Java used to iterate over elements in a collection. It lets you go through the both forword and backward directions and provide additional methods like `previous` and `hashPrevious`.</br></br>
`previous()` is used to get the previous element in the collection.</br>
`hasPrevious()` is used to check if there are more elements in the collection.

#### 19. Explain the ConcurrentHashMap ?
`ConcurrentHashMap` is a thread-safe map in Java that allows multiple threads to access and modify the map concurrently without causing conflicts. It is designed to use handle multithread environments to provide better performance. `ConcurrentHashMap` works by dividing the map into smaller segments. Each segment can be accessed and modified independently by different threads.

#### 20. How to synchronize ArrayList ?
A synchronized ArrayList is a thread-safe ArrayList. It ensures that multiple threads can access and modify the list safely without causing conflicts.
We can synchronize ArrayList in two ways.</br>
i) Using Collections.synchronizedList() method </br>
ii) Using CopyOnWriteArrayList<T>

# Internal Workings of Collections
#### 1. Explain the internal working of hashmap ?
* HashMap stores data as key-value pairs.
* When we put data into a HashMap, it first checks if the internal array of buckets exists. If not, it creates one with a default size of 16. Then, it generates a 
  hash code for the key and uses it to decide the position for inserting, reading, or removing the data.
* If two keys produce the same hash code, which is called a hash collision, HashMap handles it using a linked list or a tree structure within the same bucket.
  
#### 2. Explain the internal working of concurrent hashmap ?
* ConcurrentHashMap also stores data as key-value pairs but is designed for thread-safe operations.
* It internally divides the map into multiple segments, allowing multiple threads to read and write without locking the whole map.
* When a key-value pair is added, it calculates the hash and decides the bucket. Only that specific bucket is locked briefly during updates, ensuring better 
  performance in concurrent environments.
* Unlike HashMap, it never allows null keys or values and ensures safe access during multithreaded operations.

#### 3. Explain the internal working of ArrayList:
* ArrayList stores elements in a dynamic array.
* When we add the first element, it creates an internal array with a default size (usually 10). As we keep adding elements, and if the array gets full, it 
  automatically doubles its size.
* It allows fast access by index, but adding or removing in the middle can be slower due to shifting elements.
  





