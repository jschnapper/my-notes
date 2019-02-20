# Final Review

**repl.it**

## Midterm 1 and 2
* can't extend more than one class, but can implement more than one class
  * even if extending a class, do not get the private methods inside
* Dynamic type = must be the same or less than type of the static, and is to the right of the equal sign
* During compile time (check if static class has method that can take these arguments)
  * At run time --> dynamic method lookup
  * compile time **only sees that static class** on either side of equal sign
* classes that implement classes need the same methods as its parent with the **exact same signature**
* extended classes do not need to have the same classes as the class it extends
* Will not compile if method absent from static class
* Interfaces can never be a static stype because not a class


**Iterators**
* iterator needs *hasNext* and *next*

## Sorting

**Inversion**: Pair of elements that are out of order
**time complexity**: runtime efficiency
**space complexity**: the extra memory usage

**Selection Sort**
*Time:* $\theta(N^2)$;
*Space: $\theta(1)$*
*Place: in-placce*
*Stability: ?*

* find the smallest, exchange with first entry; find second smallest, exchange with second entry, and so on until array is fully sorted
* scans entire array until find min

**Heapsort**
*Time:* $O (N log N)$ for both in-place and not in-place;
*Space:* $\theta(N)$ ig naive approach  because made another array, without extra array it is $\theta(1)$
*Place: Can be in-place*
*Stability: ?*

* Naive: maintain heap so getting min is fast (use max-oriented heap for best efficiency)
* Naive: use the input array to create n+1 map heap with top spot empty for nicer math
* Naive :want to move heap to output array (take max and move to back of output array -- deleting from heap takes run time of log n)
* Not Naive: treat input array as heap using bottom-up heapification by sinking nodes in reverse level order (avoid extra array)
* Not Naive (which is why to use max instead of min heap): Back of array becomes the sorted array while the front is the heap as you swap

**Insertion Sort**
*Time:* best -- $\theta(N)$; worst -- $\theta(N^2)$
*Space: ?*
*Place: In-Place*
*Stability: ?*
* Start at beginning of array and insert item in proper order relative to what has been sorted already. If inserting, move larger items one to the right before inserting the current item into that position
* In-place insertion will keep track of current item and the travell back to the left until its in its right place among all examined items. Continue through unexamined

**Mergesort**
*Time:* $\theta(N log N)$  
*Space:* $\theta(N)$ because of aux array
*Place: not in-place; can be in-place but sucks and slow*
*Stability: ?*
* we focus on top-down
* divide array in two halves
* sort the two halves (recursively)
* merge the results

**Quicksort**
*Time: ?*
*Space: ?*
*Place: in-place*
*Stability: ?*
* variety of options: partition, shuffle, ...
* partition
  * randomly assign pivot
  * pivot is in it's final place, sort that which is less than pivot, and sort that which is greater than pivot; revursively
  * 

