# Important JavaScript Terms & Methods

### `reduce` 
`reduce` - Executes a **reducer** function that is provided as an argument on each value in the array, **which results in a single output value**
```js
const array = [1, 2, 3, 4];

// User-defined function to be passed into the `reduce` function
const reducer = (accumulator, currentValue) => accumulator + currentValue;

const resultOne = array.reduce(reducer);
console.log(resultOne);
// 10

const resultTwo = array.reducer(reducer, 5) 
// 15
```

The user-defined **reducer function** takes four arguments.
1. Accumulator
2. Current Value
3. Current Index (optional)
4. Source Array (optional)

Each iteration of the reducer function on a value on the array is returned and assigned to the **accumulator** which will eventually result in a single return value once the entire array has been iterated through.


`arr.reduce(callback [, initialValue])`

`callback` is the user defined function.
If an `initialValue` is provided, then the `currentIndex` starts at 0, which is the `currentValue`, and the `accumulator` is assigned to the `initialValue`. If there is no `initialValue`, then the `currentIndex` starts at index 1 and `accumulator` is assigned to index 0. 

Can manipulate this function to return an array instead of a value. To do this, assign the initial value for the accumulator to be an empty array, and push to the array in the reducer function.

You can also only reduce certain elements by including conditionals.

This is similar to the `map` and `filter` functions. The benefit of doing it in the `reduce` function is that **you don't need to go through the array twice**

#### When is it best to use `reduce`?
* For increased speed if you are doing both a `map` and a `filter`
* Tallying: when you want to know how many of each item is in an array
* Flattening an array of arrays into a single array 
* Piping: that is, reducing over functions to perform a set of functions on each value. Use `reduce` to create a pipeline. To do this, create an array of functions and set the initial value to be the amount that you want to transform. Example:
```js
// variables assigned to mathematical functions
let pipeline = [increment, double, decrement]

// transforming the value `1`
const result = pipeline.reduce((total, func) => func(total), 1)
```

***Make sure to included an inital value when necessary. Like when returning an array or object, need to provide an empty array or object as the initial value.***

```js
// square the value if it is a positive integer

const arr = [-5, 1.1, 2, -3, -3.3, 4.2, 3]

const result = arr.reduce((acc, val) => {
  if (val % 1 === 0 && val > 0) {
    acc.push(val * val);
  }
  return acc;
}, []);

console.log(result);
// [ 4, 9];

```


### `map`
`map` - creates a new array with the results of calling a user-defined function on ever element of the array.

```js
const array = [1, 2, 3];

const result = array.map(val => val * 2);

console.log(result);
// [2, 4, 6]
```

`const newArray = arr.map(function callback(currentValue[, index[, array]]) { // Return element for newArray}[, thisArg])`

1. `callback` function that produces the new array
2. `currentValue` is the current element being processed
3. `index` (optional) current index
4. `array` (otional) is the the array `map` was called on
5. `thisArg` (optional) - the value to use at `this` when executing the callback. It is `undefined` if no value passed to it


### `filter`
`filter` - creates a new array with all elements that pass the test implemented by the provided function

```js
const array = ['potato', 'car', 'house'];

const result = array.filter(word => word.length > 3);

console.log(result);
// ["potato", "house"];
```

`const newArray = arr.filter=(callback(element[, index[, array]]), [, thisArg])`

1. `callback` is a user-defined function that keeps each provided element if it passes the function's user-defined conditional
2. `element` is the current element being processed
3. `index` (optional) is the index of the current element
4. `array` (optional) is the array that `filter` was called on
5. `thisArg` (optional) is the value to use as `this` when executing the `callback`. If not provided, the `this` value is `undefined`.

Returns an empty array if no value passes the provided test

### `concat`
Merge two or more arrays. It does not change exisiting arrays, but returns a new array
```js
const arrOne = [1, 2, 3];
const arrTwo = [4, 5, 6];
console.log(arrOne.concat(array2));
// [1, 2, 3, 4, 5, 6]
```

### forEach
`forEach()` executes a provided function once for each array element

You cannot stop or break a `forEach()` loop other than an error or throwing an exception. 

**It does not return anything. This callback is allowed to mutate the calling array**

**Can only be used on Arrays, Maps, and Sets**

### `for ... in`
`for ... in` is used to iterate over the enumerable properties of objects. 

**Every property in an object has an `Enumberable` value, if its `true`, then the property is `Enumerable`**

```js
const arr = "potato";

for (let c in arr) {
  console.log(c);
}
// p
// o
// t
// a
// t
// o
```

### `for ... of` 
`for ... of` creates a loop over iterable objects


### `for ... of` vs `for ... in`
`for ... in` iterates of **enumerable properties** of an object **in an arbitrary order**.

`for ... of` iterates over data that the **iterable object** defines to be iterated over

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of

### `call` & `apply`

`call()` calls a function with a given `this` value and **arguments provided individually**. Allows for a function/method belonging to one object to be assigned and called for a different object, so you don't need to rewrite the method for the new object.


`apply` calls a function with a given `this` value and `arguments` provided as an array or array-like object. Allows you to inherit a method from another object without rewriting the method. 

`call()` accepts an **argument list**
`apply()` accepts a **single array of arguments**

`function.call(thisArg, arg1, arg2, ...)`

`function.apply(thisArg, [argsArray])`
for `apply`, when using it with built-in functions and want to loop through the argument list, should set `thisArg` to `null`.

`this` refers to the **calling object**

When to use `call()`
1. chain constructors for an object
2. to invoke an anonymous function
3. to invoke a function an specify the context for `this`

When to use `apply()`
1. to append an array to another array
2. Use built-in functions with apply
3. Chain constructors 

### `slice()`
Returns a new array object selected from `begin` (inclusive) to `end` (exclusive). If `begin` is not provided, slicing begins at the 0th index. `begin` can be negative, in which case, extracting begins counting from the end of the array. `arr.slice(-2)` takes the last two elements. 


### `every()`
Checks if every element of an array passes a provided function.















