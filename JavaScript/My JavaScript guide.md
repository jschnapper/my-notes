# My JavaScript guide

* JavaScript has nothing to do with Java -- it was a marketing ploy because of the success and popularity of Java 
* There are two names for the same language: **ECMAScript** (or **ES**) and **JavaScript**

### Data types
7 different data types in js
1. undefined
2. null
3. boolean
4. string
5. symbol
6. number
7. object

Primitives: integer, string, boolean

* `NaN` is of type number 
* Empty values are either `null` or `undefined`
* **falsy** values are `NaN`, `undefined`, `null`, `0`, `''`, and `false`

### Strings

* backtickes (`) are **template literals**
  * can embed values into strings with this
  *   \`half of 100 is ${100 / 2}` =>

  ```JavaScript
  Half of 100 is 50
  ```
  * use "${...}" to insert values into strings

String **values** are **immutable**. You can't change a character in a string by indexing, but you can reassign the value of the string.

```JavaScript
var x = "bob"
x[0] = "j"
// x = "bob"
x = "job"
// x = "job"
```


### Booleans
* booleans for strings are by alphabetical order `a < b // true`
* uppercase letters are less than lowercase letters 
```JavaScript
NaN == NaN
// false
// one nonsensical number does not equal another nonsensical number
```
* true/false are lowercase

### Logical Operators
* js uses "&&" and "||" operators
* *ternary operator* (or the *conditional operator*) logical operator
```JavaScript
true ? 1 : 2 
// 1
false ? 1 : 2
// 2 
```
* ternary operators can be chained together 
* *short-circuiting* in general for logical operations is that the item to the right is only evaluated if needed, -- the program will stop and execute before reaching it if the value on the left is true

### Switch
`case` values are tested with strict equality. Include `break`after each case. 



### Type Coercion
* equality operators given wrong types will automatically convert the value of that type to the type that is needed to complete the operation. This allows js to compare two different data types
* this is done from left to right 
* `===` and  `!==` prevent automatic type coercion, comparing both the value and the type to see if they are **strictly equal**. These are **strict equality operators**
* Use the `typeof` operator to determine type like `typeof 3 // returns 'number'`

### Arrays
* Arrays can have different types in the same array
* Arrays can contain other arrays - **multidimensional arrays**
* Array entries are mutable 
* Append data to the end of an array with `push()` method, which takes one or more parameters, mutating the array. It returns the length of the array
* The `pop()` method pops the value of the end of an array and returns it, mutating the array
* The `shift()` method removes the first element of an array and returns it
* The `unshift() method adds values to the front of an array`

### Variables
variables are also called **bindings**. They are *defined* when provided a value or expression. Can define multiple variables at once.
```JavaScript
let one = 1, two = 2;
```
*let*, *const*, and *var* are used to create variables

When a variable is declared but not initialized, it has an initial value of `undefined`.

Adding a value to an undefined variable returns `null`

Concatenating a string to an undefined variable returns the literal string `"undefined"`.

### Functions
* Functions have **parameters** that act as placeholders for the actual values that get input into the function, **arguments** 
* Functions without a return statement return the value **undefined**

### Scope
* *scope** refers to the visibility of variables
* Variables defined outside of a function block have **global scope** - visible anywhere
* Variables declared in a function, as well as function parameters have **local scope** - visible only within the function
* local variables take precedence over global variables


### Objects
* Store objects in variables
* Access data in objects through properties
* Properties can be stored as strings or numbers, and you can omit the quotes for single-word string properties
```JavaScript
var example = {
  "test": "testing",
  5: "potato",
  seven: "anything"
}
```
* Any non-string properties are **typecasted as strings**
* Access propeties with dot notation `.` or bracket notaion `[]` (need to use brack notation if the name of the property has spaces, or can use a variable, or if it the propety name is collected dynamically)
* Delete properties with `delete`. Exmaple: `delete ourDog.bark` will delete the "bark" property
* Check if property exists with `.hasOwnProperty()` which returns true or false

### Iterator
`do...while` will first `do` the code no matter what and then it runs `while`

```JavaScript
var array = [];
var i = 0;
do {
  array.push[i];
  i++;
} while (i < 5);
// array = [0,1,2,3,4]
```

the `do...while` loop **ensures the code in the `do` will run at least once**

### Built-in onjects & methods
`Math.random()` returns a number between 0 (inclusive) and 1 (exclusive)

`Math.floor()` rounds down the given argument to the nearest whole number

**To get a range of whole numbers**
`Math.floor(Math.random() * (max - min + 1)) + min`

`parseInt()` parses a string a returns an integer. An optional second argument indicates the base of the string and will convert that to an integer. 
```js
parseInt(11, 2)
// 3
```

# ES6

**USE STRICT**
`"use strict"` will catch and throw common coding mistakes and 'unsafe' actions.


### Var vs Let
`var` does not throw an error when redeclared the variable. When declaring a variable with `var`, it is global, or local if **declared in a function**. 

`let` throws an error when redclared. It also behaves similarly when declared globally or locally.*But there is more*. When declaring `let` inside a block, statement, or expression, it is limited to that declaration scope. Therefore, if you declare another `let` for the same variable name in a different scope, it will not error

**So while you can redeclare a variable with `var`, you cannot do so with `let`.**

```js
var name = "potato";
var name = "steve";
console.log(name)
// steve

let name = "potato";
let name = "steve" // throws an arrow
```
```js
function test() {
  var i = "one";
  if (true) {
    i = "two";
    console.log(i);
  }
  console.log(i);
}
test();
// two
// two



function test() {
  let i = "one";
  if (true) {
    i = "two"
    console.log(i);
  }
  console.log(i);
}
test();
// two
// two





function test() {
  let i = "one";
  if (true) {
    let i = "two";
    console.log(i);
  }
  console.log(i);
}

test();
// two
// one
```

```js
var array = [ ];
for (var i = 0; i < 3; i++) {
  array.push(i);
}
console.log(array);
// [0, 1, 2]
console.log(i) 
// 3

var array = [ ];
var i;
for (i = 0; i < 3; i++) {
  array.push(i);
}

console.log(array);
// [0, 1, 2]
console.log(i);
// 3
```

```js
var printNumTwo;
for (var i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return il
    };
  }
}
console.log(printNumTwo());
// 3
// prints 3 because the value assigned to i was updated, and the function returns a global i not the value i had when the function was created
```

```js
';use strict'
let printNumTwo;
for (let i = 0; i < 3; i++) {
  if (i === 2) {
    printNumTwo = function() {
      return i;
    }
  }
}
console.log(printNumTwo());
// 2
// the value of i in which the function was created
console.log(i)
// i is not defined
// i is not defined because it was not declared globally 
```

### Const
`const` has all the same features as `let`, **PLUS** it is **read-only**. Once the variable is assigned with `const`, it cannot be **reassigned**. It can still be **mutable**, like arrays and other js objects. So you cannot point to another array or object once declared with `const`, but can reassign values within the array or object.

```js
const a = [1, 2, 3];
a = [ 4, 5, 6] // error
a[1] = 10; // OK
console.log(a)
// [1, 10 , 3]
```

It is common practice to use all uppercase when declaring a variable with `const`

`Object.freeze(arg)` **will prevent any mutation on the given argument**. You can no longer add, update, or remove any properties.  

### Functions 

**Anonymous functions** or **inline functions** are functions that don't have names, and are passed as arguments to other functions, often assigned to a variable. They can be written like so
```js
// without arrow function
const func = function() {
  const var = "variable";
  return var;
}

// As an arrow function
const func = () => {
  const var = "variable";
  return var;
}

```

When there is no function body and only a return value, **arrow functions** can be reduced to
```js
const func = () => "variable";
```

### Rest operator & Spread Operator
The **rest operator**, `...args`, allows for representing an indefinite number of arguments as an array. **Can only be the last argument**

A function's last param can be supplied with this notation, such that all remaining args will be placed in a js array.

```js
function fun(a, b, ...manyMore) {
  console.log("a: ", a);
  console.log("b: ", b);
  console.log("more:", manyMore) 
}

fun("one", "two", "three", "four", "five", "six");
// a: one
// b: two
// more: [three, four, five, six]
```

The **spread operator**, `...arr`, allows us to expand arrays and other expressions in places where parameters or elements are expected. Rather than lisiting the actual array, this unpacks the array into its individual elements. 

```js
const arr = [1, 2, 3];
Math.max(arr) // NaN, needs to be comma separated values

Math.max(...arr) 
// 3

// Unpacking
// [1, 2, 3] => 1, 2, 3
```

***This only works in an argument to a function or an array literal***
```js
const arr = [1, 2, 3]
const spreaded = ...arr 
// ERROR

const arr2 = [arr]
// [[1, 2, 3]]

const arr2 = [...arr]
// [1, 2, 3]
```

### Destructuring
Assigning values taken directly from an object to variables. 
```js
var obj = {x: 1, y: 2, z: 3};
const {x, y, z} = obj;
// x = 1, y = 2, z = 3
```
Can copy the values of an object into a variable of another name like so:
```js
var obj = {x: 1, y: 2, z: 3};

const {x : a, y: b, z: c} = obj;
// a = 1, b = 2, c = 3
```

Can use this for nested objects as well.

```js
const obj = {
  start: {
    x: 1,
    y: 2
  },
  end: {
    x: 3,
    y: 4
  }
};

const { start : { x : startX, y: startY}} = obj;
console.log(startX, startY);
// 1, 2
```

Can also destructure array. 
```js
const [a, b] = [1,2,3,4,5]
console.log(a, b);
// 1, 2
```
Can also use commas to reach the desired index.

```js
// gets 0th, 1st, and 4th index
const [a, b,,, c] = [1,2,3,4,5,6];
console.log(a, b, c);
// 1, 2, 5
```

Can use this method to swich variables.

```js
let a = 2, b = 3;

[b, a] = [a, b]
console.log(a, b);
// 3, 2
```

Can use array destructuring like the `slice()` method with the **rest operator**.

```js
// return a subarray of the original array excluding the first two elements

const original = [1,2,3,4,5]
const [a, b, ...theRest] = original;
console.log(original);
// [1,2,3,4,5]
console.log(theRest);
// [3, 4, 5]
```

Can destructure within the argument of a function. 

```js
function half({max, min}) {
  return (max + min) / 2;
}

const x = {
  number: 3,
  max: 200,
  min: -200
}

half(x);
// 0
```

### Object Literal Declarations with Simple Fields 
Use this concept of simple fields to reduce redundancy.

```js
const mousePosition = (x, y) => ({
  x: x,
  y, y
})
// Can be simplified to
const mousePosition = (x, y) => ({
  x,
  y
})
```

### ES5 vs ES6 function declarations in objects
Eliminate redundancy
```js
// ES5
const person = {
  name: "taylor",
  hello: function() {
    return "Hello, my name is" + this.name;
  }
}

// ES6
const person = {
  name: "taylor",
  hello() {
    return `Hello, my name is ${this.name}`;
  }
}
```

### Class Syntax to define a Constructor Function
The `class` syntax is just syntax. It is not a full-fledged class based implementation of object oriented paradigm. 

In ES5, define a constructor function and use `new` to instantiate an object.
```js
// ES5
var SpaceShuttle = function(targetPlanet){
  this.targetPlanet = targetPlanet;
}

var zeus = new SpaceShuttle('Jupiter')
```

In ES6, class syntax replaces the constructor function.
```js
// ES6
class SpaceShuttle {
  constructor(targetPlanet) {
    this.targetPlanet = targetPlanet;
  }
}

const zeus = new SpaceShuttle('Jupiter')
```
### `getters` and `setters`
Can get and set values of a property within an object.

```js
class Book {
  constructor(author) {
    this._author = author;
  }
  get writer() {
    return this._author;
  }
  set writer(updatedAuthor) {
    this._author = updatedAuthor;
  }
}

const name = new Book('potato');
console.log(name.writer);
// potato
name.writer = "head";
console.log(name.writer);
// head
```
`getters` and `setters` hide internal implementation, hiding private variables 

### `import` and `export`
These are non-browser features. Requires transpiling

Export variables like this:
`export const foo = "bar"`

Export function:
`export {capitalizeString}`

Export the above in one line:
```js
... 
const foo = "bar";
export {capitalizeString, foo };
```

`export default` is used usually when there is one export value or you need a fallback value. Only one is allowed per file. Cannot use `export default` with `var`, `let`, or `const`.

```js
export default function() {
  return "hi";
}
```

To `import` a `default export`, do not used the "{}" around the named value, as there is only one thing that can be imported.
```js
import add from "./math)functions"
```





























