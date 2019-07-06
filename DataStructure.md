# Table of contents
* [Reference](#Reference)
* [Java Collection](#Java_Collection)
* [List] (#List)
	* [Vector/ArrayList/LinkedList]
* [Set] (#Set)
	* [HashSet/LinkedHashSet/TreeSet]
* [Array](#Array)
* [String & Character](#String_Character)
	* [StringBuffer](#StringBuffer)
* [Stack](#Stack)
	* [Stack Usage](#stack_usage)
	* [Monotonous stack](#monotonous_stack)
* [Queue](#Queue)
* [Heaps](#heaps)
* [Tree](#Tree)
	* [Binary Tree Traversal](#Binary_Tree_Traversal)
		* [Inorder Traversal](#Inorder_Traversal)
		* [Preorder Traversal](#Preorder_Traversal)
		* [Post order Traversal](#Postorder_Traversal)
	* [Balance Search Tree](#blancest)
		* [AVL Tree](#avltree)
	* [Convert DFS to while loop by Stack](#dfs_to_loop_by_stack)
* [Graphs](#Graphs)
	* [Define Graph](#graphs_definition)
	* [DFS](#dfs)
	* [BFS](#bfs)
	* [Topological Sort](#Topological_sort)
	* [PRIM MST](#prim)
	* [MST-KRUSKAL](#kruskal)
	* [Dijkstra](#dijkstra)
* [Compare Sort](#Compare_Sort)
* [Tries](#tries)
* [Bit Manipulation](#BitManip)

# Reference:	
---
	https://hk029.gitbooks.io/leetbook/
	https://javarevisited.blogspot.com/2013/03/top-15-data-structures-algorithm-interview-questions-answers-java-programming.html
	https://www.ntu.edu.sg/home/ehchua/programming/java/J5c_Collection.html
	https://softeng.polito.it/slides/07-JavaCollections.pdf
	https://pdfs.semanticscholar.org/2d4a/a0f63c26dee36310c6c1ce3fe1fe4b4551e9.pdf
	https://www.geeksforgeeks.org/data-structures/
	https://www.edureka.co/blog/java-collections/
	
# Java Collection <a name="Java_Collection"></a>
------
Java Classes (Collections & Map), Collections have List/Set/Queue  & Map
![Collections Diagram](https://github.com/ericwork2008/Java-Advanced-Study/blob/master/collections%20framework%20overview.png "Java Collection")

## Collection/Map interfaces
The interal data structure to implement them is Array/Tree/Linked List
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



# List  <a name="List"></a>
## Vector/ArrayList/LinkedList
---
|            |      Random    |Synchronize|  Enumeration | Iterator | ListIterator | Order     |
|------------|:--------------:|----------:|-------------:|---------:|-------------:|----------:|
| ArrayList  |  Random        | No        |  No          | Yes      | Yes         | Added |
| Vector     |  Random        | Yes       |  Yes         | Yes      | Yes         | Added |
| Linked List|  Sequential    | No        |  No          | Yes      | Yes         | Added |

## ArrayList
None of the methods of ArrayList are synchronized. So the ArrayList class is also not synchronized

## Vector
Vector is a legacy class. Vector is extends AbstractList and implements List, RandomAccess, Cloneable & Serializable interface.
almost all the members of vector were synchronized. So it affects the concurrency of the application.

## Linked List 
---
Linked List have Singly Linked List, it is a class which is extends AbstractSequentialList class and implements List, Deque, Cloneable & Serializable interface.
LinkedList element can be synchronized. So that LinkedList class is also not synchronized. As the LinkedList is not synchronized so it doesn't affect the concurrency of an application.



Example
```
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
```
Iteration Linked List, sometimes will can use recursive/runner pointer

# Set <a name="set"></a>
|            |      Random    |Synchronize|  Enumeration | Iterator |  Order     |
|------------|:--------------:|----------:|-------------:|---------:|-----------:|
| HashSet    |  Random        | No        |  No          | Yes      |  Added     |
| Linked HashSet|  Sequential | No        |  No          | Yes      |  Added     |
| TreeSet    |  Random        | No        |  No          | Yes      |  Added     |

Java TreeSet is implemented by red-black balanced binary search tree. Add/Remove/Contains have O(log(n)) complexity.

# Map <a name="map"></a>
|            |      Random    |Synchronize|   Order    |
|------------|:--------------:|----------:|-----------:|
| HashMap    |  Random        | No        | unSorted   |
| Linked HashMap|  Sequential | No        | Added      |
| TreeMap    |  Random        | No        | Sorted     |
| HashTable  |  Random        | Yes       | unSorted   

Java TreeMap implemented by red-black balance binary tree. Key is stored in order.

# Stack <a name="Stack"></a>
Stack<T> drives from Vector<T> so radom access is possible, this void the stack interfaces. Stack<T> isn't drived from collection interface. 
	
## Stack ADT Operations
Push(k): Adds a new item to the top of the stack
Pop(): Remove an element from the top of the stack and return its value.
Top(): Returns the value of the element at the top of the stack
Size(): Returns the number of elements in the stack
IsEmpty(): determines whether the stack is empty. It returns 1 if the stack is empty or return 0.

## Stack Java Implementation
- peek(), pop(), push(), isEmpty()
- Stack<Object> stack = new Stack<>(); Push generic Object to stack
- We can use ArrayDequeue<T> for Stack. pop()/push()/peekLast()/size()/isEmpty()
- Stack can be implemented with LinkedList, adding/removing from same side of the list
	
## Stack Usage <a name="stack_usage"></a>
- Reverse Stack
- stack, change recursive to no recursive
- Use Stack implement Queue
- Use Stack for sort

## Monotonous stack <a name="monotonous_stack"></a>
---
Monotonous stack template:
```
item = someItem; // ex: item in for loop
while (!stack.isEmpty() && (item.property compareTo stack.peek().property)) {
	topItem = stack.pop();
	// Do something with the topItem
}
stack.push(item);
```

# Queue <a name="Queue"></a>
## Queue ADT operations
Add(): Add a new element to the back of the queue.
Remove(): remove an element from the front of the queue and return its value.
Front(): return the value of the element at the front of the queue.
Size(): returns the number of elements inside the queue.
IsEmpty(): returns 1 if the queue is empty otherwise return 0

## Queue Java implementation
- add(),remove(), peek(), isEmpty(). For Java Queue Class, please refer to the #Java Collection
- queue = new LinkedList<...>() Queue can use LinkedList. Add from the last/end of the list; Return/remove from the head of the list. 
- ArrayDeque() also can be used as Queue. add()/remore()/peekFirst()
- PriorityQueue: new Comparator
- PriorityQueue

# Array <a name="Array"></a>

## Java Array
```
- ArrayList.add(index, elem);
- Arrays.asList(1,2,3);
- Arrays.toString(int[] arr) => string representation: "[1,2,3,4]"
- Integer[] array = {1, 2, 3};
- new ArrayList(Arrays.asList(array))
- list.add(index, object)
- list.removeRanege[x, y)
- Partial sort: Arrays.sort(arr, 0, arr.length())
- Copy: Arrays.copyOf(arr, arr.length())
- target=Arrays.copyOfRange(original,from,to)
- System.arraycopy(source, 3, destination, 2, 5)
- O(1) insertion on average. 
- 2darray data[][] size is data.length * data[0].length
```
Array in java is fixed length. ArrayList is resizable (An ArrayList can resize itself as needed)

## High rate operation
- Reverse
- Binary Search
- Rotate
- Find Dup
- Palindrome

# String & Character <a name="String_Character"></a>
---
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

## StringBuffer
----
StringBuffer is a resizable array. Can be used to avoid high operation drawback of String when you add other strings.
## High rate operation
- palindrome/permutation/unified

# Math
- Integer.MAX_VALUE, Integer.MIN_VALUE; if overflow, use long
- Integer.valueOf(number), where number is int
- Math.pow(x, 3) = x ^ 3; Math.pow(x, 1/3) = x ^ (1/3)
- Long a = 10; a.intValue() => int
- Integer: Integer.parseInt("123")
- Integer.parseInt("010", 2) = 2;

# Tree <a name="Tree"></a>
---
A simple version of graph which haven't cycle, and each node can have a list of children
- Binary Tree:  each node has up to  two chidren
- Binary Search Tree: All left nodes <= current node.val <= all right nodes
-- binary-search-tree property: Let x be a node in a binary search tree. If y is a node in the left subtree of x, then y:key <= x:key. If y is a node in the right subtree of x, then y:key >= x:key.
- Balanced: every subtree height difference <= 1
- Completed Tree: every level is fully filled, except the last level which is filled from left to right.
- Full binary Tree: each node have zero or 2 children, NO node will have 1 child
- Perfect binary tree: full and complete
## Binary search tree
### BST ADT Operations
Insert(k): Insert an element k into the tree.
Delete(k): Delete an element k from the tree.
Search(k): Search a particular value k into the tree if it is present or not.
FindMax(): Find the maximum value stored in the tree.
FindMin(): Find the minimum value stored in the tree.

- insert(val)/find(val)/findmin()/next_large(node x)
```
next_large(node x) {
    if(x.right!=null) 
        return minValueofTree(x.right)
    else {
        //reach a node which is the left child of his parent
	y=parent(x);
	while(y !=null && x == y.right){
	    x = y;
	    y = parent(y);
	}
	return y;
    }
}
```
## Binary Tree Traversal <a name="Binary_Tree_Traversal"></a>
- preorder, inorder, post-order
- inorder more often
- Can be implemented By dfs, bfs

### Inorder Traversal <a name="Inorder_Traversal"></a>
```
void inOrderTraversal(TreeNode node) {
    if(node!=null) {
        inOrderTraversal(node.left);
	visit(node);
	inOrderTraversal(node.right);
    }
}
```
### Preorder Traversal <a name="Preorder_Traversal"></a>
```
void preOrderTraversal(TreeNode node) {
    if(node!=null) {
        visit(node);
        preOrderTraversal(node.left);
	preOrderTraversal(node.right);
    }
}
```
### Post order Traversal <a name="Postorder_Traversal"></a>
```
void postOrderTraversal(TreeNode node) {
    if(node!=null) {
        postOrderTraversal(node.left);
	postOrderTraversal(node.right);
	visit(node);
    }
}
```
### Convert DFS to while loop by Stack  <a name="dfs_to_loop_by_stack"></a>
- stack: in while loop: deep dive to left leaf => stack.pop() => `node = node.right`
```
	stack.push(root);
	TreeNode node = root;
	while(!stack.isEmpty()) {
	   //Left first
	   while (node != null && node.left != null) { 
		   stack.add(node.left);
		   node = node.left;
	   }
	   //Process left/curr
	   node = stack.pop();
	   
	   // do something with node
	   node = node.right; // VERY IMPORTANT
	   if (node != null) {
		   stack.push(node);
	   }
	}
```
- `node = node.right` is critical, otherwise it'll be in infinite loop
- alternatively: we could set left = null, but that's disruptive to original structure, not recommended.

### Expression Tree
---
```
Example
For the expression (2*6-(23+7)/(1+2)) 
which can be represented by ["2" "*" "6" "-" "(" "23" "+" "7" ")" "/" "(" "1" "+" "2" ")"]. 
The expression tree will be like

                 [ - ]
             /          \
        [ * ]              [ / ]
      /     \           /         \
    [ 2 ]  [ 6 ]      [ + ]        [ + ]
                     /    \       /      \
                   [ 23 ][ 7 ] [ 1 ]   [ 2 ] .

```
### Tree Technics
- Compare two node in a tree. We have two different trace way, one kind for each node have parent link. Another kind for each node haven't parent link.
- To match two tree, we can use recursion to match each node.
- If you want select tree node randomly. We need use radom(size) to get the index. We can choice left or right by the index.
- Graph/tree path sum. We can use recursive to choice root or no.

## Heap
### Heap ADT operations
Insert() - Adding a new element to the heap. O(log(n))
remove() - Extracting max for max heap case (or min for min heap case). O(log(n))
Heapify() – To convert a list of numbers in an array into a heap. Time Complexity O(n)

Heap Property (Min/Max Heap)
- MAX-HEAPIFY O(lg n)
- BUILD_MAX_HEAP build heap; O(n)
- HEAPSORT, O(nlog n)
- MAX-HEAP-INSERT, HEAP-EXTRACT-MAX, HEAP-INCREASE-KEY, and HEAP-MAXIMUM; O(log n)
### Heap Java implementation
Java PriorityQueue is implemented using binary heap data structure.

PriorityQueue<Integer> pq = new PriorityQueue<Integer>(Collections.reverseOrder());
PriorityQueue<Integer> pq = new PriorityQueue<Integer>();

## Hash-Table
### Hash-Table ADT operations
Insert(x): Add object x to the data set.
Delete(x): Delete object x from the data set.
Search(x): Search object x in data set.

###  HashTable Java implementation
HashSet (Storage: Hash table)
LinkedHashSet (Storage: hash table and a linked list)

|            |      Random    |Synchronize|  Enumeration | Iterator |  Order     |
|------------|:--------------:|----------:|-------------:|---------:|-----------:|
| HashSet    |  Random        | No        |  No          | Yes      |  Added     |
| Linked HashSet|  Sequential | No        |  No          | Yes      |  Added     |

HashMap<>


## Tries
---
- Another name: Prefix Tree
- A variant of n-ary tree in which characters are stored at each node. Each path down the tree may represent a word.
- * node is often used to indicate complete words.
- Can tell if string is a valid prefix in O(K) time, k = str.length

https://en.wikipedia.org/wiki/Trie

### TST (Ternary Search Tree)
https://en.wikipedia.org/wiki/Ternary_search_tree

## Segment Tree
- Another name: Interval Tree. 
- https://en.wikipedia.org/wiki/Segment_tree
- https://en.wikipedia.org/wiki/Interval_tree
- https://www.geeksforgeeks.org/interval-tree/

## Balance Search Tree <a name="blancest"></a>
- AVL Tree
- B-Trees/2-3-4 Trees
- Red-Black Trees
- Splay-Trees
- Skip Lists
- Scapegoat Trees
- Treaps

### Red Black Tree
- one kind of self-balancing binary search tree
- Each node of the binary tree has an extra bit, and that bit is often interpreted as the color (red or black) of the node
- search O(logn), n = total # of nodes in the tree
- deletion/insertion/tree rearrangement && coloring: O(logn)

### B-Tree
- https://en.wikipedia.org/wiki/B-tree

### AVL Tree <a name="avltree"></a>
- Balance: The sub-trees of every node differ in height by at most one.
- Every sub-tree is an AVL tree
- height < 2 log Nh, Nh is the # nodes in height-h AVL tree
- Rotation: From Voilation Node to heavy sub tree, we have Right-Right, Right-Left, Left-Left, Left-Right. When Rotation we following the order from the Heavy-sub tree to the voilation Node.
- Right-Right/Left-Left only related with 2 node. Left/Right Rotation
- Right-Left/Left-Right relates with 3 Nodes. Right-Left Rotation/Left-Right Rotation. 

- Operations: Insert 1.Insert as in Simple BST; 2. Work your way up tree, restoring AVL property.
- AVL Sort: 1) insert each item into AVL tree. O(nlogn); 2)in-order traversal; 

| Priority Queue ADT   |      Heap      |  AVL Tree |
|----------------------|:--------------:|----------:|
| Q=new-empty-queue()  |  O(1)          | O(1)      |
| Q.insert(x)          |  O(logn)       |  O(logn)  |
| x=Q.deletemin()      | O(logn)        |  O(logn)  |
| x=Q.findmin()        | O(1)           |  O(logn)-> O(1) |
| S=new-empty()        |  O(1)          |  O(1)     |
| x=Q.insert(x)        | O(logn)        |  O(logn)  |
| x=Q.delete(x)        | O(n)           |  O(logn)  |
| y=S.predecessor(x)   | O(n)           |  O(logn)  |
| y=S.successor(x)     | O(n)           |  O(logn)  |

### Usage
- Storage system than read/write large blocks of data.
- Commonly used in database, filesystem

# Graphs <a name="graphs"></a>
Ref  https://blog.csdn.net/xiazdong/article/details/8132371 
     https://www.tutorialspoint.com/graph_theory/graph_theory_fundamentals.htm
pendent vertex
isolated vertex
parallel edges
Multigraph

强连通图：任意两个顶点u,v，u到v和v到u都有路径。
弱连通图：此图为有向图，他不是强连通图，但是如果把有向边变成无向边后，图为连通的，则此图为弱连通图。
二分图（Bipartite Graph）：如果一个图的点集能被分成两个不相交的子集V1、V2，使得每条边都是V1中的点与V2中的点连接。
完全二分图：点集分为两个子集后，每个子集中任意抽一个点，他们之间都有边。
着色定理：如果图是二分图当且仅当给图中每个点赋予红蓝两色之一，使得没有一条边的两个顶点是同一个颜色。
着色定理可以通过BFS来实现，即距离为奇数的顶点着色为蓝色，偶数的顶点着色为红色，着色完毕需要O(V+E)，然后在遍历每条边，检查是否着色正确，O（V+E）。
定理：图是二分图当且仅当不可能从某个顶点开始走，经过奇数条边又回到起点。

割点：如果去掉某个点，连通分支数增加，则此点为割点。
割边（桥）：如果去掉某个边，连通分支数增加，则此边为割边。

欧拉回路：在图中能找到遍历每条边一次的简单回路（注意是简单回路）；
欧拉路径：在图中能找到遍历每条边一次的简单路径；

在无向图中，图中有欧拉回路当且仅当图中每个顶点的度数为偶数；
在有向图中，图中有欧拉回路当且仅当图中每个顶点出度和入度相同；

在无向图中，图中有欧拉路径当且仅当图中只有两个顶点度数为奇数；
在有向图中，图中有欧拉路径当且仅当图中只有两个点，出度入度相差奇数；

汉密尔顿回路：在图中能找到能遍历每个点一次的简单回路；
汉密尔顿路径：在图中能找到能遍历每个点一次的简单路径；

连通分支：连通的点的集合，比如{A,B,C}为图的一个连通分支；

在无向图中判断是否存在回路：|E|>|V|-1且连通图，则一定有回路。
在有向图中判断是否存在回路：DFS有反向边。

---
Representation method
- Adjacency Matrix
- Adjacency List

In the website there are many implementation
https://algs4.cs.princeton.edu/41graph/Graph.java.html

Here prefer following (Copied from Geekforgeeks)
## Define Graph <a name="graphs_definition"></a>
```
// A class to represent a graph edge
class Edge implements Comparable<Edge>
{
    int src, dest, weight;
    
    // Comparator function used for sorting edges 
    // based on their weight
    public int compareTo(Edge compareEdge) {
                return this.weight-compareEdge.weight;
    }
};

// A class to represent a subset for union-find
class subset
{
    int parent, rank;
};

public class Graph {
    int V, E;    // V-> no. of vertices & E->no.of edges
    Edge edge[]; // collection of all edges

    LinkedList<Integer> adjListArray[]; //Adj List
    
    // constructor 
    Graph(int V)
    {
        this.V = V;

        // define the size of array as 
        // number of vertices
        adjListArray = new LinkedList[V];
         
        // Create a new list for each vertex
        // such that adjacent nodes can be stored
        for(int i = 0; i < V ; i++){
            adjListArray[i] = new LinkedList<>();
        }
    }
    
    // Creates a graph with V vertices and E edges
    Graph(int v, int e)
    {
        V = v;
        E = e;
        edge = new Edge[E];
        for (int i=0; i<e; ++i)
            edge[i] = new Edge();
    }
    /**
     * Initializes a new graph that is a deep copy of {@code G}.
     *
     * @param  G the graph to copy
     */
    public Graph(Graph G) {
        this(G.V());
        this.E = G.E();
        for (int v = 0; v < G.V(); v++) {
            // reverse so that adjacency list is in same order as original
            Stack<Integer> reverse = new Stack<Integer>();
            for (int w : G.adjListArray[v]) {
                reverse.push(w);
            }
            for (int w : reverse) {
            	adjListArray[v].add(w);
            }
        }
    }
    // Adds an edge to an undirected graph
    static void addEdge(Graph graph, int src, int dest)
    {
        validateVertex(src);
        validateVertex(dest);
        E++;
        
        // Add an edge from src to dest. 
        graph.adjListArray[src].addFirst(dest);
         
        // Since graph is undirected, add an edge from dest
        // to src also
        graph.adjListArray[dest].addFirst(src);
    }

    static void printPath(Graph graph, int s, int v) {
        if(v==s) {
            System.out.println("vertex:"+ v);
        }else if (parent[v] == -1) {
            System.out.print("no path from " + s + " to " + v + "exists");
        }else {
            printPath(graph,s,parent[v]);
        }
    }



    /**
     * Returns the number of vertices in this graph.
     *
     * @return the number of vertices in this graph
     */
    public int V() {
        return V;
    }

    /**
     * Returns the number of edges in this graph.
     *
     * @return the number of edges in this graph
     */
    public int E() {
        return E;
    }

    // throw an IllegalArgumentException unless {@code 0 <= v < V}
    private void validateVertex(int v) {
        if (v < 0 || v >= V)
            throw new IllegalArgumentException("vertex " + v + " is not between 0 and " + (V-1));
    }

    /**
     * Returns the vertices adjacent to vertex {@code v}.
     *
     * @param  v the vertex
     * @return the vertices adjacent to vertex {@code v}, as an iterable
     * @throws IllegalArgumentException unless {@code 0 <= v < V}
     */
    public Iterable<Integer> adj(int v) {
        validateVertex(v);
        return adjListArray[v];
    }

    /**
     * Returns the degree of vertex {@code v}.
     *
     * @param  v the vertex
     * @return the degree of vertex {@code v}
     * @throws IllegalArgumentException unless {@code 0 <= v < V}
     */
    public int degree(int v) {
        validateVertex(v);
        return adjListArray[v].size();
    }


    /**
     * Returns a string representation of this graph.
     *
     * @return the number of vertices <em>V</em>, followed by the number of edges <em>E</em>,
     *         followed by the <em>V</em> adjacency lists
     */
    public String toString() {
        StringBuilder s = new StringBuilder();
        s.append(V + " vertices, " + E + " edges " + NEWLINE);
        for (int v = 0; v < V; v++) {
            s.append(v + ": ");
            for (int w : adj[v]) {
                s.append(w + " ");
            }
            s.append(NEWLINE);
        }
        return s.toString();
    }
}
```
## DFS <a name="dfs"></a>
DFS, double-E (Enter/Exit), U 包 Edge.
```
    /*
      void DFS(G) {
        for each vertex u in G.V
        	u.visited = false
        	u.p =  NIL
        time = 0 
        for each vertex u in G.V
        if u.visited == false
        	DFS-VISIT(G, u)
       }
       
       void DFS-VISIT(G, u) {
        	time = time + 1 // white vertex u has just been discovered
		//Pre-Process u
        	u.d = time
        	u.visited = true
        	for each v in G.Adj[u] // explore edge (u,v)
		        //Process Edge
        		if v.visited == false
        			v.p = u
        			DFS-VISIT(G, v);
        	time = time + 1
		//Post-Process u
       }
     */
   // A function used by DFS
   void DFSVisit(int v,boolean visited[]) {  				//Passed extra data to record visit state/path/depth
       // Mark the current node as visited and print it
       visited[v] = true;						//Visit present node, if we want have special function
       									//to precess
       System.out.print(v+" ");

       // Recur for all the vertices adjacent to this vertex
       Iterator<Integer> i = adj[v].listIterator();
       while (i.hasNext()) { //Termination
           int n = i.next();
           if (!visited[n])
               DFSVisit(n, visited);
       }
   }
   // The function to do DFS traversal. It uses recursive DFSUtil()
   void DFS(int v) {
       // Mark all the vertices as not visited(set as
       // false by default in java)
       boolean visited[] = new boolean[V];

       // Call the recursive helper function to print DFS traversal
       DFSVisit(v, visited);
   }
```

## BFS <a name="bfs"></a>
BFS, I-E-W, PDP(Parent/Discoveried/Processed), u 包 edge
```
   /*
   public void BFS(Graph G, Vertex s) {
        for each vertex u in G.V - {s}
        	u.visited = false
        	u.d = 1
        	u.p = NIL
        	
        s.visited=true
        s.d = 0
        s.p = NIL
        create empty Q 
        ENQUEUE(Q, s)
        while Q != empty  //Termination
        	u = DEQUEUE(Q)
        	for each v in G.Adj[u]
        		if v.visited == false
        			v.visited = true
        			v.d = u.d + 1
        			v.p = u
        			ENQUEUE(Q, v)
   }
   
   */
   void BFS(int s) {
       // Mark all the vertices as not visited(By default
       // set as false)
       boolean visited[] = new boolean[V]; //visited for Discovered & Processed

       // Create a queue for BFS. FIFO queue
       LinkedList<Integer> queue = new LinkedList<Integer>();		//Queue, multiple queue for special case

       // Mark the current node as visited and enqueue it
       visited[s]=true;							//Visted node process, BFS can add extra info in node. 
       									//No call stack
       queue.add(s);

       while (queue.size() != 0)					//If we have multiple queue, we need check the current queue
       {
           // Dequeue a vertex from queue and print it
           s = queue.poll();
           System.out.print(s+" ");

           //Pre-Process u
	   
           // Get all adjacent vertices of the dequeued vertex s
           // If a adjacent has not been visited, then mark it
           // visited and enqueue it
           Iterator<Integer> i = adj[s].listIterator();
           while (i.hasNext())
           {
               int n = i.next();
	       //Process Edge
               if (!visited[n])
               {
                   visited[n] = true;
                   queue.add(n);
               }
           }
	   //Post-Process u
       }
   }
```
## Topological Sort <a name="Topological_sort"></a>
```
   /**
    * ========================= 	
       TOPOLOGICAL-SORT(G)
           1 call DFS(G) to compute finishing times v.f for each vertex v
           2 as each vertex is finished, insert it onto the front of a linked list(or STACK)
           3 return the linked list of vertices
    */
   void topologicalSortUtil(int v, boolean visited[], Stack stack){
       // Mark the current node as visited.
       visited[v] = true;
       Integer i;
       
       // Recur for all the vertices adjacent to this
       // vertex
       Iterator<Integer> it = adj[v].iterator();
       while (it.hasNext())
       {
          i = it.next();
          if (!visited[i])
              topologicalSortUtil(i, visited, stack);
       }
       
       // Post-Process u
       // Push current vertex to stack which stores result
       // In Stack node haven't next. Looks like put no successor in first.
       stack.push(new Integer(v));
   }
   
   void topologicalSort()
   {
       Stack stack = new Stack();

       // Mark all the vertices as not visited
       boolean visited[] = new boolean[V];
       for (int i = 0; i < V; i++)
           visited[i] = false;

       // Call the recursive helper function to store
       // Topological Sort starting from all vertices
       // one by one
       for (int i = 0; i < V; i++)
           if (visited[i] == false)
               topologicalSortUtil(i, visited, stack);

       // Print contents of stack
       while (stack.empty()==false)
           System.out.print(stack.pop() + " ");
   }
```
## PRIM MST  <a name="prim"></a>
PRIM, DPI, move from NonTree into Tree
```

   /**
    * BFS, get adjusted vertex which have the minium edge value. Result is the vertex & parent
    * 	==============
       MST-PRIM(G,w,r)   O(E + V lgV)
           for each u in G.V
               u.key = MAX                      //Set every key=MAX
               u.p = NIL	
           r.key = 0
           Q = G.V				//Q have all vertex
           while Q != empty
               u = EXTRACT-MIN(Q)		//Get the min key value vertex
               for each v in G.Adj[u]
                   if v in Q and w(u,v)< v.key  //Reduce v.key
                       v.p = u
                       v.key = w(u,v)           <== relax function, Pay attention here, different from Dijkstra
    */
   // A utility function to find the vertex with minimum key
   // value, from the set of vertices not yet included in MST
   int minKey(int key[], Boolean mstSet[])
   {
       // Initialize min value
       int min = Integer.MAX_VALUE, min_index=-1;

       for (int v = 0; v < V; v++)
           if (mstSet[v] == false && key[v] < min)
           {
               min = key[v];
               min_index = v;
           }

       return min_index;
   }
   // Function to construct and print MST for a graph represented
   //  using adjacency matrix representation
   void primMST(int graph[][])
   {
       // Array to store constructed MST
       int parent[] = new int[V];

       // Key values used to pick minimum weight edge in cut
       int key[] = new int [V];

       // To represent set of vertices not yet included in MST
       Boolean mstSet[] = new Boolean[V];

       // Initialize all keys as INFINITE
       for (int i = 0; i < V; i++)
       {
           key[i] = Integer.MAX_VALUE;
           mstSet[i] = false;
       }

       // Always include first 1st vertex in MST.
       key[0] = 0;     // Make key 0 so that this vertex is
                       // picked as first vertex
       parent[0] = -1; // First node is always root of MST

       // The MST will have V vertices
       for (int count = 0; count < V-1; count++)
       {
           // Pick thd minimum key vertex from the set of vertices
           // not yet included in MST
           int u = minKey(key, mstSet);

           // Add the picked vertex to the MST Set
           mstSet[u] = true;

           // Update key value and parent index of the adjacent
           // vertices of the picked vertex. Consider only those
           // vertices which are not yet included in MST
           for (int v = 0; v < V; v++)

               // graph[u][v] is non zero only for adjacent vertices of m
               // mstSet[v] is false for vertices not yet included in MST
               // Update the key only if graph[u][v] is smaller than key[v]
               if (graph[u][v]!=0 && mstSet[v] == false &&
                   graph[u][v] <  key[v])
               {
                   parent[v]  = u;
                   key[v] = graph[u][v];
               }
       }

       // print the constructed MST
       printMST(parent, V, graph);
   }
```
## MST-KRUSKAL <a name="kruskal"></a>
Kruskal, go through Edges, union components
```
   // A utility function to find set of an element i
   // (uses path compression technique)
   int find(subset subsets[], int i)
   {
       // find root and make root as parent of i (path compression)
       if (subsets[i].parent != i)
           subsets[i].parent = find(subsets, subsets[i].parent);

       return subsets[i].parent;
   }

   // A function that does union of two sets of x and y
   // (uses union by rank)
   void Union(subset subsets[], int x, int y)
   {
       int xroot = find(subsets, x);
       int yroot = find(subsets, y);

       // Attach smaller rank tree under root of high rank tree
       // (Union by Rank)
       if (subsets[xroot].rank < subsets[yroot].rank)
           subsets[xroot].parent = yroot;
       else if (subsets[xroot].rank > subsets[yroot].rank)
           subsets[yroot].parent = xroot;

       // If ranks are same, then make one as root and increment
       // its rank by one
       else
       {
           subsets[yroot].parent = xroot;
           subsets[xroot].rank++;
       }
   }
   

   /**
    * Find and Union. Choice min edge then find/Union until all vertex processed.
    * If two end of the edge isn't in the UNION side, then UNION it.
    * Result is the edge set	
    * ===================
       MST-KRUSKAL(G,w) :: O(E lgV)
           A = empty
           for each vertex v in G.V
               MAKE-SET(v)
           sort the edges of G.E into nondecreasing order by weight w
           for each edge (u,v) in G.E, taken in nondecreasing order by weight
               if FIND-SET(u) != FIND-SET(v)
               A = A U {(u,v)}
        		UNION(u,v)
           return A
    */
   // The main function to construct MST using Kruskal's algorithm
   void KruskalMST()
   {
       Edge result[] = new Edge[V];  // Tnis will store the resultant MST
       int e = 0;  // An index variable, used for result[]
       int i = 0;  // An index variable, used for sorted edges
       for (i=0; i<V; ++i)
           result[i] = new Edge();

       // Step 1:  Sort all the edges in non-decreasing order of their
       // weight.  If we are not allowed to change the given graph, we
       // can create a copy of array of edges
       Arrays.sort(edge);

       // Allocate memory for creating V ssubsets
       subset subsets[] = new subset[V];
       for(i=0; i<V; ++i)
           subsets[i]=new subset();

       // Create V subsets with single elements
       for (int v = 0; v < V; ++v)
       {
           subsets[v].parent = v;
           subsets[v].rank = 0;
       }

       i = 0;  // Index used to pick next edge

       // Number of edges to be taken is equal to V-1
       while (e < V - 1)
       {
           // Step 2: Pick the smallest edge. And increment 
           // the index for next iteration
           Edge next_edge = new Edge();
           next_edge = edge[i++];

           int x = find(subsets, next_edge.src);
           int y = find(subsets, next_edge.dest);

           // If including this edge does't cause cycle,
           // include it in result and increment the index 
           // of result for next edge
           if (x != y)
           {
               result[e++] = next_edge;
               Union(subsets, x, y);
           }
           // Else discard the next_edge
       }

       // print the contents of result[] to display
       // the built MST
       System.out.println("Following are the edges in " + 
                                    "the constructed MST");
       for (i = 0; i < e; ++i)
           System.out.println(result[i].src+" -- " + 
                  result[i].dest+" == " + result[i].weight);
   }
   
 ```
 ## Dijkstra <a name="dijkstra"></a>
 Dijkstra, DPI, move unknown to known
 ```
   /**
    * DIJKSTRA(G,w,s) find short path
       INITIALIZE-SINGLE-SOURCE(G, s)
           S = empty
           Q = G.V					//All vertex in the Queue
           while Q != empty
               u = EXTRACT-MIN(Q)			//u is visited here
               S = S U {u}
               if (v ∈ Q) and w(u,v) < v.key            // by pass visited node
                    v.parent = u
                    v.key = w(u,v) + u.key               <== relax function, Pay attention here
    */
   // Funtion that implements Dijkstra's single source shortest path
   // algorithm for a graph represented using adjacency matrix
   // representation
   void dijkstra(int graph[][], int src)
   {
       int dist[] = new int[V]; // The output array. dist[i] will hold
                                // the shortest distance from src to i

       // sptSet[i] will true if vertex i is included in shortest
       // path tree or shortest distance from src to i is finalized
       Boolean sptSet[] = new Boolean[V];

       // Initialize all distances as INFINITE and stpSet[] as false
       for (int i = 0; i < V; i++)
       {
           dist[i] = Integer.MAX_VALUE;
           sptSet[i] = false;
       }

       // Distance of source vertex from itself is always 0
       dist[src] = 0;

       // Find shortest path for all vertices
       for (int count = 0; count < V-1; count++)
       {
           // Pick the minimum distance vertex from the set of vertices
           // not yet processed. u is always equal to src in first
           // iteration.
           int u = minDistance(dist, sptSet);

           // Mark the picked vertex as processed
           sptSet[u] = true;

           // Update dist value of the adjacent vertices of the
           // picked vertex.
           for (int v = 0; v < V; v++)

               // Update dist[v] only if is not in sptSet, there is an
               // edge from u to v, and total weight of path from src to
               // v through u is smaller than current value of dist[v]
               if (!sptSet[v] && graph[u][v]!=0 &&
                       dist[u] != Integer.MAX_VALUE &&
                       dist[u]+graph[u][v] < dist[v])
                   dist[v] = dist[u] + graph[u][v];
       }

       // print the constructed distance array
       printSolution(dist, V);
   }
}
```

# Bit Manipulation <a name="BitManip"></a>
- 32 bit number: leading bit = 1, negative numbjer; leading bit = 0, positive number.
-- -k = concat(1, 2^(n-1) - k)
- Arithmetic(>>) & Logical(>>>) Shift
-- '>>' add leading '1' if the 32 bit number originally has leading '1'.
-- Java/python: logical shift >>>, always add leading '0' regardless of the sign of the 32-bit number. That is, it may turn a negative number to positive, if the leading bit is originally '1'
- Bit OR |, AND &, XOR ^
- Bit shift: <<, >>
- A << 1: value x 2
- A >> 1: divide by integer 2
- & 0000 = clean up; 
- A^B=C, then A = B^C
- Math.pow(2, h) = 2 << (h - 1); 
- Also, 1 << h = 2 ^ h;
- bit operation should be in parentheses
Refer [awesome-bits](https://github.com/keon/awesome-bits).

# Compare Sort <a name="Compare_Sort"></a>
Java provides two interfaces to sort objects using data members of the class: Comparable&Comparator. 
Comparable interface compares “this” reference with the object specified and Comparator in Java compares two different class objects provided.
Collections.sort() or Arrays.sort() can be used to sort objects. Default will use Coamparable. Anyway, sort() can pass Comparator too.If sorting of objects needs to be based on natural order then use Comparable whereas if you sorting needs to be done on attributes of different objects, then use Comparator in Java.

- Comparable
```
class MyClass implements Comparable<MyClass>
{
    // Used to sort movies by year
    public int compareTo(Movie m)
    {
    	//return -1,0,1
        return -1;
    }
}
```
- Comparator
```
class MyCompare implements Comparator<MyClass>
{
    public int compare(MyClass m1, MyClass m2)
    {
    	//return -1,0,1
        return 0;
    }
}
```
