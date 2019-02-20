# JavaScript Data Structures

An **Abstract Data Structure** is a class for objects whose behavior is defined by a set of values and a set of operations. It does not described the how to be implemented, just the operations that can be performed, making it "abstract"

___
### Arrays
An **array** data structure is of the js type **object**. 

js arrays can have multiple types within a single array dimension. 

All arrays have a `length` property which can be accessed with `Array.length`

Array maintain order

* Arrays can have different types in the same array 
* Arrays can contain other arrays - **multidimensional arrays** 
* Array entries are mutable 
* Append data to the end of an array with `push()` method, which takes one or more parameters, mutating the array. **It returns the length of the array**, not the new array
* The `pop()` method pops the value of the end of an array and returns it, mutating the array 
* The `shift()` method removes the first element of an array and returns it 
* The `unshift()` method adds values to the front of an array`
* Use `splice()` to remove and return consecutive elements. The first argument is the index where to start. The second argument is how many elements to remove. This modifies the original array by removing those elements. The third (and more), optional, arguments, are element(s) to add to the original array starting where the other elements were removed
* `slice()` copies a given number of elements to a new array, leaving the original array untouched. The first argument is the index to start (inclusive) and the second argument is the index to end (exclusive)
* Check for the presence of an element in an array with `indexOf()`, which returns `-1` if the element does not exist


**You can `slice` and `splice` arrays but you CAN ONLY `slice` strings**

### Objects
Use the `delete` keyword to remove properties. IF we had an object like `foods` with the property `apple`, we can delete the property `apple` by writing `delete foods.apple`

Order of properties is not maintained in an object. It is irrelevant. 

`Objects.key()` returns an array with strings representing each property of the passed in object to the `keys()` method.

### Queue
* Items are kept in order
* New items can be added to the back and old items are taken off from the front (**First In, First Out**)
