# Table of contents
* [Big O](#bigo)
	* [Amotized Time](#amotize_time)
* [Steps for Solution](#solution_steps)
	* [How to design&develope an algorithm](#dev_algo)
* [Traversal techinics](#traversal_tech)
	* [Recursive Algorithms](#recursive_algo)
	* [Iterative Algorithms](#iter_algo)
	* [Recursion Vs. Iteration](#recuVsiter)
* [The steps to choice right traversal tech](#choice_traversal)
	* [Data Process](#data_process)
* [Popular Traversal tech](#traversalTech)
	* [Binary Search](#bin_search)
	* [Linked List traversal](#traversal_linkedlist)
	* [Sentinel Usage](#sentinel)
	* [Breadth First Search](#bfs)
	* [Depth First Search](#dfs)



# Big O (for Time and Space complexity) <a name="bigo"></a>
---
Big O is an upper bound on time
Big omega is the lower bound
big theta means both O & omega

Normally we think about three case for Big O analysis: best/worse/Excepted

Recursive function that makes multiple calls, the runtime will often look like O(branch^depth)

## Amotized Time <a name="amotize_time"></a>
---
[wiki link](https://en.wikipedia.org/wiki/Amortized_analysis)


# Keywords
---
- permutation factorial 

# Steps for a Solution <a name="solution_steps"></a>
	 1) Analysis Problem, find solution way. Get the special properties in the solution.
	 2) Find & Simplify to a reasonable Math Model (Data Structure & Algorithm)
	 3) Write the data structure and algorithm by code.
	 4) Test
## How to design&develope an algorithm <a name="dev_algo"></a>
---
In Crack Coding, it have following way to design an algorithm
1) Look for BUD (Bottleneck, Unneccecary Operation, Duplicated Operations)
2) DIY
3) Simplify and Generalize
4) Basecase and build
5) Brainstorm of Data structure
6) Check if we used all information we know.


# Traversal techinics <a name="traversal_tech"></a>
## Recursive Algorithms  <a name="recursive_algo"></a>
	An algorithm that calls itself in its definition.
	
	Recursive case a conditional statement that is used to trigger the recursion.
	Base case a conditional statement that is used to break the recursion.

	Becareful following issue 
	(Issue) Stack level too deep and stack overflow.
	If you've seen either of these from a recursive algorithm, you messed up.
	It means that your base case was never triggered because it was faulty or 
	the problem was so massive you ran out of RAM before reaching it.

	Knowing whether or not you will reach a base case is integral to correctly using recursion.
	Often used in Depth First Search

## Iterative Algorithms (iteration as loops, for, while) <a name="iter_algo"></a>
	An algorithm that is called repeatedly but for a finite number of times,
	each time being a single iteration. Often used to move incrementally through a data set.


## Recursion Vs. Iteration <a name="recuVsiter"></a>
	Recursion is, usually, more expressive and easier to implement.
	Iteration uses less memory.
	Functional languages tend to use recursion. (i.e. Haskell)
	Imperative languages tend to use iteration. (i.e. Ruby)
	Check out this Stack Overflow post for more info.

## Pseudo Code of Moving Through an Array (this is why iteration is used for this)
```
	Recursion                         :|: Iteration
	----------------------------------:|:----------------------------------
	recursive method (array, n)       | iterative method (array)
		if array[n] is not nil    |   for n from 0 to size of array
			print array[n]    |     print(array[n])
	    	recursive method(array, n+1)|
		else                      |
			exit loop         |
```    

# The steps to choice right traversal tech. <a name="choice_traversal"></a>
1) Investigate some samples to figure out the steps to find the solution
2) refine the steps to traversal tech. and convert it to computation logic.
## Data Process <a name="data_process"></a>
In Traversal, we are tring to find/modify/etc. other operations on DATA. Just like normal function call we have following three way to access data
- Passed Parameters (on Stack)
- Global Variables (on HEAP)
- Return Data.

# Some popular Traversal tech <a name="traversalTech"></a>
## Two Pointers <a name="two_pointers"></a>
- Two pointers in array
- Two pointers in Linked List
'''
  	front = 0;
  	tail = A.length()-1
  	while(front < tail)
  	{
  	}
'''

## Binary Search <a name="bin_search"></a>
- Different point have different purpose.
- The iterator have clear definition. for loop / do-while /while-do / recursive will iterate in
--	the range of condition!
--	begin and end/termination
--	base case
- Sometimes binary search can have more than one traversal varables

'''  
	while(st < ed)
	{
    	int mid= st  + (ed-st)/2;
    	if( r[mid] < target)
        	st = mid+1;
    	else
        	ed = mid;
	}
	return st;
'''

## In Place swap
---
## Linked List traversal <a name="traversal_linkedlist"></a>
---
 	Two Point in Linked List Need have header & tail two variables
	Note: In the iteration, we need make sure 
		1) the iteration have precondition is [front:tail] cover target. front<=target<=tail
		2) after loop, front>=tail


## Sentinel Usage <a name="sentinel"></a>
In traversal, sometimes to make sure we have a uniform code to avoid boundary check we can use Sentinel
### Array sentinel
	two array compairation
	
### Linked List Sentinel
	==============
	1) Link List sentinel
	2) Link List header
	
### Loop	
	for OR while loop (https://www.geeksforgeeks.org/loops-in-java/)
	====================
	for(int i=0;i<n;i++){} :  the log run n times
	for(int i=1;i<=n;i++){} : the log run n times
	for(int i=0;i<=n;i++){} : the log run n+1 times
	
	while(){} and do{}while(), the diffrence need care.
## Edge Condition
Traversal, we need care about the edge.
1) List Edge condition and test it
2) What is the Traversal variable, how to use it?

## Breadth First Search <a name="bfs"></a>
---
	An algorithm that searches a tree (or graph) by searching levels of the tree first, starting at the root.
	It finds every node on the same level, most often moving left to right.
	While doing this it tracks the children nodes of the nodes on the current level.
	When finished examining a level it moves to the left most node on the next level.
	The bottom-right most node is evaluated last (the node that is deepest and is farthest right of it's level).

	Optimal for searching a tree that is wider than it is deep.
	Uses a queue to store information about the tree while it traverses a tree.
	Because it uses a queue it is more memory intensive than depth first search.
	The queue uses more memory because it needs to stores pointers
	
	The Queue can be FIFO/PriorityQueue/etc. for purposes

	Search: Breadth First Search: O(|E| + |V|)
	E is number of edges
	V is number of vertices

### Depth First Search <a name="dfs"></a>
	An algorithm that searches a tree (or graph) by searching depth of the tree first, starting at the root.
	It traverses left down a tree until it cannot go further.
	Once it reaches the end of a branch it traverses back up trying the right child of nodes on that branch,
	and if possible left from the right children.
	When finished examining a branch it moves to the node right of the root then tries to go left on all
	it's children until it reaches the bottom.
	The right most node is evaluated last (the node that is right of all it's ancestors).
		
	Optimal for searching a tree that is deeper than it is wide.
	Uses a STACK to push nodes onto.
	Because a stack is LIFO it does not need to keep track of the nodes pointers and is
	therefore less memory intensive than breadth first search.
	Once it cannot go further left it begins evaluating the stack.

	Search: Depth First Search: O(|E| + |V|)
	E is number of edges
	V is number of vertices

### Breadth First Search Vs. Depth First Search <a name="bfsVsdfs"></a>
	The simple answer to this question is that it depends on the size and shape of the tree.
	For wide, shallow trees use Breadth First Search
	For deep, narrow trees use Depth First Search
	Breadth First Search tends to be a looping algorithm.
	Depth First Search tends to be a recursive algorithm.
