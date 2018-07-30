#Reference:	
---
	https://hk029.gitbooks.io/leetbook/
	https://javarevisited.blogspot.com/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html
	https://www.ntu.edu.sg/home/ehchua/programming/java/J5c_Collection.html
	https://softeng.polito.it/slides/07-JavaCollections.pdf
	https://pdfs.semanticscholar.org/2d4a/a0f63c26dee36310c6c1ce3fe1fe4b4551e9.pdf
	
#Java Collection
------
Java Classes (Collections & Map), Collections have List/Set/Queue  & Map
##Collection 
```
		|----------Set
		|-----------|-----SortedSet-------TreeSet
		|			|------HashSet ----Linked HashSet
		|
		|----------Queue---LinkedList
		|			|------PriorityQueue
		|
		|-----------List
		|------ArrayList
```
##Map
```
	  |-----------Sorted Map
	  |-----------HashMap-----Linked HashMap
```

##Collection/Map just interface. The interal data structure to implement them is Array/Tree/Linked List
```
	Collection:
		int size()
		boolean isEmpty()
		boolean contains(Object element)
		boolean containsAll(Collection c)
		boolean add(Object element)
		boolean addAll(Collection c)
		boolean remove(Object element)
		boolean removeAll(Collection c)
		void clear()
		Object[] toArray()
		Iterator iterator()
	Map:
		Object put(Object key, Object value)
		Object get(Object key)
		Object remove(Object key)
		boolean containsKey(Object key)
		boolean containsValue(Object value)
		public Set keySet()
		public Collection values()
		int size()
		boolean isEmpty()
		void clear()
	List:
		Object get(int index)
		Object set(int index, Object element)
		void add(int index, Object element)
		Object remove(int index)
		boolean addAll(int index, Collection c)
		int indexOf(Object o)
		int lastIndexOf(Object o)
		List subList(int fromIndex, int toIndex)
	Queue:
		E remove()         // throws NoSuchElementException if this queue is empty
		E poll()           // returns the head of this queue, or null if this queue is empty
		E peek()           // returns the head of this queue, or null if this queue is empty, but does not remove
		boolean add(E e)   // throws IllegalStateException if no space is currently available
		boolean offer(E e) // returns true if the element was added to this queue, else false

	LinkedList used for Stack/Queue/Deque
		addFirst()
		addLast()
		getFirst()
		getLast()
		removeFirst()
		removeLast()
```
	Misc
	====
	Converting a List to an Array - toArray()
	Using an Array as a List - Arrays.asList()
	Java Collections.binarySearch
  #Array
  ---
Array have following frequently used methods
```
- Partial sort: Arrays.sort(arr, 0, arr.length())
- Copy: Arrays.copyOf(arr, arr.length())
- target=Arrays.copyOfRange(original,from,to)

- ArrayList.add(index, elem);

- 2darray data[][] size is data.length * data[0].length
- Arrays.asList([1,2,3]);
- Arrays.toString(int[] arr) => string representation: "[1,2,3,4]"
```
Array in java is fixed length. ArrayList is resizable (An ArrayList can resize itself as needed)

# String & Character
String have following high frequency methods
- Character.isDigit(x)
- Character.getNumericValue();
- String.split("regular Expression"); 
- String.indexOf()
- String.isEmpty()
- String.subString()
- String.contains(CharSequence x)
- String.valueOf(charArrary)
- String.compareTo( "XXX" ), lexicographically order
- char[] rst = String.toCharArray()
- String.trim()

Questions: palindrome/permutation/unified

#StringBuffer
----
StringBuffer is a resizable array. Can be used to avoid high operation drawback of String when you add other strings.

## Linked List
---
Linked List have Singly Linked List
class Node{
	int data;
	Node next;
	public Node(int data){
		this.data=data;
		next=null;
	}
	void append(int d){
		Node newNode = new Node(d);
		Node current = this;
		while(current.next!=null){
			current=current.next;
		}
		current.next=newNode;
	}
}

Iteration Linked List, sometimes will can use recursive/runner pointer

  #Vector vs. ArrayList
  ---
  
  #Tree
  ---
  #Tries
  ---
  #Graphs
  ---
