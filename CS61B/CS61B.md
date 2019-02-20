# CS61B
## Spring 2018

### 2/14

#### Immutablility 
Declaring a reference as ```Final``` does not make object immutable
```java
public final ArrayDeque(String) d = new ArrayDeque<String>();
```
The ```d``` variable can never change. ```d``` cannot change what it points at, but the contents of the ```ArrayDeque``` can change

#### Autoboxing
* automatically converts types to another more general type (widening) so that it fits the type a parameters of functions. ex: int to Integer (which is an object)
* this occurs due to ambiguity and happens at runtime. The runtime conversions add to the run cost. Therefore, want to **cast**

#### Generics

***generic class***
```java
public class ArrayMap<K,V> implements Map61B<K,V> {
  ...
  ...
}
```
The generics apply to the entire class, share across the class. Meaning that any method must instantiate what the generic types actually are for the methods. 

**generic method**
```java
public static <K,V> V get(Map61B<K,V> sim, K key) {
  return;
}
```
In this instance, just the method is generic, and now does not need to affect the entire class. Applies only to this scope. In this way, don't need to explicitly state the type -- it is automatically inferred by the type of the objects passed in 

**type upper bound**
Only numerical primitives can use comparators > and <. Therefore, cannot compare generics in this way because unknown type. However, a generic itself does not have something like "compareTo," so this specific generic type requires to extend comparable and now has a type that is a subtype of Comparable... which has a type paramater of its own

But it's not actually extending like a class extends. It's just poor wordchoice. It's actually saying "isasubtypeof". This is **type upperbounding**
```java
public static <K extends Comparable<K>,V> K maxKey(ArrayMap<K,V> map) {
  List<K> keylist = map.keys();
  K largest = keylist.get(0);
  for (K k : keylist) {
    if (k.compareTo(largest) > 0) {
      largest = l;
    }
  }
  return largest;

}
```

### 2/16
#### Exceptions

**Catch** prevents program from crashing on exception
```java
try {
  doSomething();
} catch (Exception e) {
    System.out.println("caught");
}
System.out.println("program continues!")
```
If the  ```Exception e```, where ```e``` is an ```Exception Object```, then the error is caught and displays in console, but the program can still run.

Can also do this to fix any particular exceptions and correct errors.

When an exception is called, it descends the ```call stack```, which is the stack of methods that called it, looking for come sort of ```catch```.

If not caught, prints all methods in stack where error occurred. **Read the stack  of methods in the reverse order, from bottom up.** That is the order in which it was executed. 

Assertion Error --> Error = **Unchecked**
IndexOutOfBounds --> RunTime Exception == **Unchecked**
Everything else, like IOException == **Checked**
* must check or specify these exceptions, otherwise, compiler prevents from compilation 
  * can use a ```try catch``` block where ```throw new exception``` and then ```catch``` it. **You provide a fix**
  * can also **specify** method as **dangerous** with ```throws``` an exception in the method signature. And include the same ```throw``` exception inside the method, no catch necessary. But if a method uses the dangerous method, that method also becomes dangerous. Catch or specify it in that method as well. In this case, **you do not provide a fix**.
  
### Iterator
if implements ```Iterable```, requires an ```iterator()``` method. This iterator method can instantiate a new iterator class that must implement ```Iterator```. And this class must contain at least ```hasNext()``` and ```next```.

### 2/21
**Access Control**

Who has access -- 
Public: class, package, subcless, world
Protected: class, package, subclass
no keywork (package private): class, package
Private: class
 
Protected allows for subclass to access declared variables from superclass.

However, when no keyword provided to a public interface, then that access modifier is actually **public** and not **package private**

Classes can either be explicitly declared **public** or implictly declared **package private** if no keyword. 

#### Arrays
```.equals``` versus ```==```
* ```.equals``` checks for equality of references, to see if actually pointing to same reference.
* ```==``` checks to see if they are mapped to same value. Such ```x = 4``` and ```y = 4```;

To test equality: 
* ```Arrays.equals``` for arrays
* ```Arrays.deepEquals``` for arrays of arrays
* ```.equals``` for classes requires writing a ```.equals``` method for your classes because the deafult implementation is ```==```.
  * must *override*. Notice that the default method takes ```Object``` as a parameter
  * requires a ```null``` check and a ```class``` check (which useses ```.getClass()``` to make sure comparing two objects of the same class type)
  * must be relfexive, symmetric, and transitive


### 2/26
#### Program efficiency
#### Runtimes and Order of Growth 

$$ 1 < n < n * log_{2}n < n^2 < 2^n < n! $$

For order of growth, only the largest term matters. Represents the overall runtime.
**simplifications**
* only consider worst case
* pick a representative operation (a.k.a. the cost model)
* ignore lower order terms
* ignore multiplicative constants

Can use geometric rather than summation reasoning if build table. Such that getting the area of a triangle with certain side length based on the number of times an operation is run.

**Big-Theta**
When determining order of growth, that order of growth ***belong to the family of a particular big-theta***

$$ N^3 + 3N^4 \in \Theta(N^4) $$

$$ R(N) \in \Theta(f(N)) $$
which means there exist positive constant k1 and k2 such that:
$$ k_1 * f(N) \leq R(N) \leq k_2 * f(N) $$ 
for all vlues of N great than some very large N.

So now, when asked for order of growth: 
$$ N^2 $$
When asked for worst case count (worst case runtime):  
$$ \Theta(N^2) $$

Write 
$$ log_{2}(N) $$ 
as 
$$ log(N) $$

#### Two sums to know:
1. Sum of First Natural Numbers up to Q 
$$ Q(Q+1)/2 = \Theta(Q^2) $$
2. Sum of First Powers of 2 up to Q 
$$ 2Q - 1 = \Theta(Q) $$

#### Binary Search
Start at middle, and check if the number searching for is higher or lower. Only pay attention to the side of the array that matters.

If even sized array, break ties by rounding down.


#### Mergsort and SelectionSort
SS = selects and sorts the array
SS runtime
$$ \Theta(N^2) $$

Mering alone takes 2 sorted arrays and merges them into 1 giant sorted array. 

Merge runtime 
$$ \Theta(N) $$

Selection sort is slow, merging is fast. 

**Mergesort solution**
*initial inutuition*
split the given array into 2 and so SS on the 2 arrays, then merge them. Continue until size 1. Runtime is still 
$$ \Theta(N^2) $$
But it's faster 

**MERGESORT!**
**OR add another layer! so it sorts 4 arrays and merges 2 times. Actual mergesort --> merge all the way down by cutting each array in half such that runtime is now:**
$$ \Theta(N * logN)$$

### 3/2
#### BIG O & Big $\Omega$

**Big Theta**: equals 
**Big O**: less than or equals, just bounds above. The order of growth is less than of euqla to f(N). *it does not mean worse case*  
**Big Omega**: greater than of equal. Orders of growth that grow as least as fast as this. *Does not mean best case*

***For Big O***
$$ R(N) \in O(f(N)) $$
means there exits positive constants k2 such that:
$$ R(N) \leq k_2 * f(N) $$
for values of N greater than some very large N

If runtime depends on the input, then rather than providing a best case and worst case scenario for Big Theta, we can just use Big O to bound the top. *But Big Theta is more informative*

***For Big Omega***
$$ R(N) \in O(f(N)) $$
means there exits positive constants k1 such that:
$$ k_1 * f(N) \leq R(N) $$
for all values of N greater than some very large N

**Useful Case**
If $R(N) = O(f(N))$ and $R(N) = \Omega(f(N))$, then $R(N) = \Theta(f(N))$

**Amortized Cost is more or less than Actual Cost**
Can do this to solve the bounds for runtime. Amortized cost (a) is arbitrary. With the **Potential**($\Phi$) being the cumulative difference between arbitrary amoritzed costs and actual costs (c) over time.

$$ \Phi_{i+1} = \Phi_i + a_i - c_i $$

Think of amortized cost as *deposits* and costs at *withdrawals*

Example usage goal for array list:
$a_i \in \Theta(1)$ and $\Phi_i \geq 0$ for all i

### 3/5 

**path compression**: results in union/connected operations that are very very close to amortized constant time

### 3/7
**Binary Search Tree**
* a tree consists of a set of nodes
* a tree consits of edges that connect those nodes (constraint: there is exactly one path between any two nodes)
* BST property for every node X in the tree
  * Every key in the **left** subtree is less than X's key
  * Every key in the **right** subtree is greater than X's key
  * **No duplicate keys allowed**
* Height of the tree is what matters -- runtime to complete search is $\Theta(logN)$

**Rooted Trees**
* one node is the root
* every node N except the root has exactly one parent, defined as the first node on the path from N to the root
* The root is usually depicted at the top of the tree
* a node with no child is called a leaf 

In a **rooted *binary tree***, every node has either 0,1, or 2 children (subtrees)

AVOID ARMS LENGTH RECURSION!!! 
* check if you yourself are null instead

### 3/9
#### Trees
Nice and bushy (lots of children) fast! Performance issues when get too tall....

Possible solution:
* take everything and insert in random order
  * results in $\Theta(logN)$ height with very high probability
  * But why don't we do this? because don't have all of the data up from 
* Tree rotation!
  * preserve BST property
  * can balance a tree with sequence rotations -- get same tree and same searching process, but more efficient 

**SEARCH TREES**
2-3, 2-3-4, B-trees (splitting trees): no rotations requires  
* Only way to change height is to split the root 
  * every node is pushed down by exactly one level
* if we split a leaf node or internal node, the height does not change 
* by ony passing things up, all operations are guaranteed $\Theta(logN)$ 
* **M**: max number of children (one more than the item cap)
* **Height**: between $log_{M}(N)$ and $log_{2}(N)$
* max number of splitting operations per inset: ~H
* time per insert/contains method in worst case: $\Theta(H)$ or equivalently $\Theta(logN)$

examples:
* B-tree of order M=4 is also a 2-3-4 tree or a 2-4 tree
  * name refers to number of children that node can have


Move left-middle (arbitrary choice) when overstuffed node

**RED-BLACK TREES**
for any 2-3 tree, there exists a corresponding red-black tree that has a depth no more than 2 times the depth of the 2-3 tree 


### 3/12
#### Hashcode

for -1 mod
use ```Math.floorMod(-int, int)```
For L = N/M, when L gets to big, increase M (RESIZING)

If multiple items in same map, use external chaining ot open addressing

### 3/16
#### Graphs/Trees 

Level Order Traversal
* traversed top to bottom, and left to right (like reading)
* uses iterative deepening

Pre-order (Depth First Traversal)
* preorder and then traverse down tree to the left (and to the left for each left branch that is possible), then recurse back and go through the right sides 
* trick: walk the graph, from top going counter clockwise. Shout every time pass around the LEFT of a node
* useful for printing directory info

In Order Traversal (only makes sense for BST)
* traverses similar to depth first, but actually prints in order from left to right of the entire tree. So if A is parent and B and C are children in that order, would ptiny "BAC". Getting back in **sorted order**
* trick: should when cross the bottom
* should when cross the right

Post Order Traversal 
* prints left children in order, and then right children in order, then the root
* useful for finding file size  


For Tree traversals
* avoid rewriting traversal for every task by using **the visitor pattern**. Can do this by creating an interface

Tree Height
* Bushy Complete Tree
  * H = $\Theta(log(N))$
  * runtime = $\Theta(N)$
* Sindly Tree
  * H = $\Theta(N)$
  * runtime = $\Theta(N^2)$
  * But, if know it's a spindly tree, can go through it as a linkedlist for better runtime 
* no simple mapping from height to runtime 

Range Finding
* want all the items in a range
* **PRUNING!** restrict search to nodes that may have answer

For multi-dimensional data: quadtrees
* can build spatial data


### 4/2
#### Shortest Paths 

**Dijkstra's Alg**
* the fringe never grows -- it only changes or shrinks
* Once a vertex is white (in demo) the edgeTo and DistanceTo will not change 
* Seaching in Best First Order 
* uses **distance from source (adds the weights)**

Only difference between A* and Dijkstra's in the fringe priorities
* A* works as long as the heuristic measurement is *admissible*, that is, it does not over estimate

* shortest paths tree (spt) depends on the starting vertex 

 


### 4/4
#### spanning tree

* spanning trees are only for undirected graphs
  * acyclic + connected (which makes it a tree)
  * includes all vertices (makes it spanning)
* min spanning tree = spanning tree of min total weight

* Min spanning tree is a global property with no source, but sometimes will be the spt 
* **cut property** given any cut, min weight crossing edge is in the MST

**Prim's Alg**
* removing vertex from fringe is the equivalent to adding an edge 
* **uses distance from teh tree (does not add weights, just cares about weight from one node to the other)**
























 
