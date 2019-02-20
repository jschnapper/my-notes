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

**Quicksort (L3S; aka left pivot)**
*Time*: Best -- $\theta(N log N)$ for N work at log(N) levels; Worst Case $\theta(N log N)$
*Space:* $\theta log N$
*Place:* nope
*Stability:* yes
* variety of options: partition, shuffle, ...
* partition
  * randomly assign pivot
  * pivot is in it's final place, sort such that everything to left of pivot is <= to the pivot and everything to the right is >= the pivot (but what is on those sides are not necessarily in sorted order)
  * do so recursively 
* Best case is when the pivot ends up in the middle (we usually arbitrarily pick the 0th element to be the pivot)
* Worst case is that the pivot always lands at the beginning of the array
* Often **the fastest** sort (on average, will run in best case time)
* If the pivot lands at least always 10% from the edge, runtime is still O(N log N)

**Quicksort (Tony Hoare)**
*Time*: Best -- $\theta(N log N)$ for N work at log(N) levels; Worst Case $\theta(N log N)$
*Space:* $\theta log N$
*Place:* yes!
*Stability:* yes
* leftmost value is the pivot
* pointers for less and greater than; less starts on the left and greater than starts on right and they walk toward each other
  * when the less than pivot encounters a value greater than or equal to the pivot, it stops and waits for the greater than pointer to find a value it also doesnt like. Then they swap those values
  * greater than does the opposite
  * once the pointers pass each other, the greater than pointer swaps with the pivot -- then you are done!

**Can use QuickSelect to find the median**
* find median by partitioning and pivoting...
* time: $\theta N$


**For the "shuffle" optimization in quicksort**
* assign random values to the current values
* sort based on those values
* then run quick sort
