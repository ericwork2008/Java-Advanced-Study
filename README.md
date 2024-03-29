# Algorithm

| [Think in Algorithm](Thinking\_in\_Algorithm.md) | [Basic Algorithm](./) | [Problem](./) |
| ------------------------------------------------ | --------------------- | ------------- |

## Table of contents

* [Big O](./#bigo)
  * [Amotized Time](./#amotize\_time)
  * [Master Method](./#master\_method)
* [Steps for Solution](./#solution\_steps)
  * [How to design\&develope an algorithm](./#dev\_algo)
* [Traversal techinics](./#traversal\_tech)
  * [Recursive Algorithms](./#recursive\_algo)
  * [Iterative Algorithms](./#iter\_algo)
  * [Recursion Vs. Iteration](./#recuVsiter)
  * [Traversal Technics](./#travesalTech)
    * [Two Pointer](./#two\_pointers)
* [The steps to choice right traversal tech](./#choice\_traversal)
  * [Data Process](./#data\_process)
* [Popular Traversal tech](./#traversalTech)
  * [Binary Search](./#bin\_search)
  * [Linked List traversal](./#traversal\_linkedlist)
  * [Sentinel Usage](./#sentinel)
  * [Breadth First Search](./#bfs)
  * [Depth First Search](./#dfs)
* [Sort](./#sort)
* [Dynamic Programming](./#dp)

## Big O (for Time and Space complexity) <a href="#bigo" id="bigo"></a>

***

Big O is an upper bound on time Big omega is the lower bound big theta means both O & omega

Normally we think about three case for Big O analysis: best/worse/Excepted

Recursive function that makes multiple calls, the runtime will often look like O(branch^depth)

### Master Method <a href="#master_method" id="master_method"></a>

T(n) = aT (n/b)+f(n) divide-and-conquer algorithm. Each problem of size n is decomposed into a problems of size n/b. Each subproblem of size k takes O(f(k)) time to deal with internally, between partitioning and merging. The total time for the algorithm is the sum of these internal costs, plus the overhead of building the recursion tree.

nlogb a is the width(leaves), logb n is hight

1. Too many leaves, If f(n) = O(nlogb a−epslon) for some constant epslon > 0, then T(n) = Θ(nlogb a).
2. Equal work per level, If f(n) = Θ(nlogb a), then T(n) = Θ(nlogb a lg n).
3. Too expensive a root, If f(n) = Ω(nlogb a+epslon) for some constant epslon > 0, and if af(n/b) ≤ cf(n) for some c < 1, then T(n) = Θ(f(n)).

### Amotized Time <a href="#amotize_time" id="amotize_time"></a>

***

[wiki link](https://en.wikipedia.org/wiki/Amortized\_analysis)

## Steps for Solution <a href="#solution_steps" id="solution_steps"></a>

* CICCT Constraints/Ideas Generation/Complexities/Coding/Testing

## Keywords

***

* permutation factorial

## Traversal techinics <a href="#traversal_tech" id="traversal_tech"></a>

### Recursive Algorithms <a href="#recursive_algo" id="recursive_algo"></a>

```
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
```

### Iterative Algorithms (iteration as loops, for, while) <a href="#iter_algo" id="iter_algo"></a>

```
An algorithm that is called repeatedly but for a finite number of times,
each time being a single iteration. Often used to move incrementally through a data set.
```

### Recursion Vs. Iteration <a href="#recuvsiter" id="recuvsiter"></a>

```
Recursion is, usually, more expressive and easier to implement.
Iteration uses less memory.
Functional languages tend to use recursion. (i.e. Haskell)
Imperative languages tend to use iteration. (i.e. Ruby)
Check out this Stack Overflow post for more info.
```

### Traversal Techinics <a href="#travesaltech" id="travesaltech"></a>

Traversal, to process data, we have following condition

* For result or intermedia data, we may have partial information for cache/memoization
* Sometimes, one primitive data cannot have enough information. We can defined our Class to hold more than one data field.

Recursion Tree/Combination/Permutation/etc. It depend on the problem. We have following hints

* Search Space = Know Partial + dfs(remaining)
* Search Space = Know Partial + Pick/Non-Pick (Present level and next level all have the pick/non-pick)
* Search Space = DFS(n-1) + Process(n)
* Search Space = DFS(Left Part) + DFS(Right Part) (Devide and Conque)
* Most time, we have mainFunc + helper dfs function.
* For input have duplicate case, most time we need sort. Avoid duplicate item by "i > index && cand\[i] == cand\[i - 1]) continue"

Iteration Combination

* Search Space = Partial + Choice/Non-Choice for each Item

#### String Permutation

* Direct method: Prefix + remain (recursive)
* Build from Base: P(n) = insert Sn in each of P(n-1)

#### LinkedList

* Fast runner Check Even/Odd node number. Fast runner always point to the odder
* Recursive Stack data is a reverse of traversal
* String/LinkedList length info always can be used in algorithm.

#### Operation Tech:

1. Remaining list
2. Copy result from List, then create new List + append new element

#### Backtracking

1. Do not change source data.
2. backtracking: ex: `list.remove(list.size() - 1)`

#### Complexity

* If algorithm each level create x child, If it have n level. Then the node total number is x^n
* T(n) = x \* T(n-1), BigO time will be `O(x^n)`

### Pseudo Code of Moving Through an Array (this is why iteration is used for this)

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

## The steps to choice right traversal tech. <a href="#choice_traversal" id="choice_traversal"></a>

1. Investigate some samples to figure out the steps to find the solution
2. refine the steps to traversal tech. and convert it to computation logic.

### Data Process <a href="#data_process" id="data_process"></a>

In Traversal, we are tring to find/modify/etc. other operations on DATA. Another we also need record for result. We have following ways to list all required variable.

* Trace Table
* Visualise call/return chain

Just like normal function call we have following three way to access data

* Passed Parameters (on Stack)
* Global Variables (on HEAP)
* Return Data.
* In algrithm implementation code, the headache thing is how to handle the data, the following is the idea -- List all input\&output data; -- Organize the data in with a data structure, in an existing class/array/etc. field or have new class/array/etc. to hold the data.

## Some popular Traversal tech <a href="#traversaltech" id="traversaltech"></a>

### Two Pointers <a href="#two_pointers" id="two_pointers"></a>

* Two pointers in array
* Two pointers in Linked List
* Three Pointer: Fix one pointer, let use another two pointer to iterater. ''' front = 0; tail = A.length()-1 while(front < tail) { } '''

### Binary Search <a href="#bin_search" id="bin_search"></a>

* Different pointer have different purpose.
* The iterator have clear definition. for loop / do-while /while-do / recursive will iterate in -- the range of condition! -- begin and end/termination -- base case
* Sometimes binary search can have more than one traversal varables

小于等于，三判断

iteration

```
	while(st <= ed) { // ? st<=ed, if we need check target when st==ed
    	    int mid= st  + (ed-st)/2; //Avoid overflow
    	    if( r[mid]==target) {
	        return mid;           //terminate
	    }else if(r[mid] < target)
        	st = mid+1;
    	    else
        	ed = mid-1;
	}
	return st;
```

recursion

```
    int binarySearch(int arr[], int l, int r, int x) 
    { 
        if (r >= l) { 
            int mid = l + (r - l) / 2; 
  
            // If the element is present at the 
            // middle itself 
            if (arr[mid] == x) 
                return mid; 
  
            // If element is smaller than mid, then 
            // it can only be present in left subarray 
            if (arr[mid] > x) 
                return binarySearch(arr, l, mid - 1, x); 
	    else
                return binarySearch(arr, mid + 1, r, x); 
        } 
  

        return -1; 
    } 
```

### In Place swap

***

### Linked List traversal <a href="#traversal_linkedlist" id="traversal_linkedlist"></a>

***

```
Two Point in Linked List Need have header & tail two variables
Note: In the iteration, we need make sure 
	1) the iteration have precondition is [front:tail] cover target. front<=target<=tail
	2) after loop, front>=tail
```

### Sentinel Usage <a href="#sentinel" id="sentinel"></a>

In traversal, sometimes to make sure we have a uniform code to avoid boundary check we can use Sentinel

#### Array sentinel

```
two array compairation
```

#### Linked List Sentinel

```
==============
1) Link List sentinel
2) Link List header
```

#### Loop

```
for OR while loop (https://www.geeksforgeeks.org/loops-in-java/)
====================
for(int i=0;i<n;i++){} :  the log run n times
for(int i=1;i<=n;i++){} : the log run n times
for(int i=0;i<=n;i++){} : the log run n+1 times

while(){} and do{}while(), the diffrence need care.
```

### Edge Condition

Traversal, we need care about the edge.

1. List Edge condition and test it
2. What is the Traversal variable, how to use it?

### Breadth First Search <a href="#bfs" id="bfs"></a>

***

```
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
```

#### Depth First Search <a href="#dfs" id="dfs"></a>

```
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
```

#### Breadth First Search Vs. Depth First Search <a href="#bfsvsdfs" id="bfsvsdfs"></a>

```
The simple answer to this question is that it depends on the size and shape of the tree.
For wide, shallow trees use Breadth First Search
For deep, narrow trees use Depth First Search
Breadth First Search tends to be a looping algorithm.
Depth First Search tends to be a recursive algorithm.
```

#### DFS recursion techinic

```
- Sometimes when we traveral in an list which may have several dementions. The List can be sorted by one demention, when we decide go to next level recursion, we can use come valid check to make sure next recursion can meet some other dementions' requirement.
```

## Sort <a href="#sort" id="sort"></a>

|                |  AverageTime |    Best Time | Worse Time |               Space | Stability |
| -------------- | :----------: | -----------: | ---------: | ------------------: | --------: |
| Bubble-Sort    |     O(n2)    |        O(n2) |   unSorted |                O(1) |           |
| Selection-Sort |     O(n2)    |        O(n2) |      Added |                O(1) |           |
| Insertion-Sort |     O(n2)    |         O(n) |     Sorted |                O(1) |           |
| Heap-Sort      | O(n\*log(n)) | O(n\*log(n)) |   unSorted |                O(1) |           |
| Merge-Sort     | O(n\*log(n)) | O(n\*log(n)) |            |                O(n) |           |
| QuickSort      | O(n\*log(n)) | O(n\*log(n)) |      O(n2) | O(n)worse,O(log(n)) |           |
| BucketSort     |     O(nk)    |        O(nk) |            |                O(1) |           |
| CountingSort   |              |              |            |                     |           |
| # Math         |              |              |            |                     |           |
| ## Shuffle     |              |              |            |                     |           |

* subset have 1 or k element.
