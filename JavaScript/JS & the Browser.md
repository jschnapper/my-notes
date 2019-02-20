# JS & the Browser

Document Object Model
* It is the structured representation of an html document
* The DOM is used to connect webpages to scripts, such as javascript
* It is a **fully object oriented representation**
* For each HTML element, there is an object in the DOM that can be accessed and manipulated
* JS and the DOM are different -- use JS methods to interact and manipulate the DOM

Events
* like notifications that something happened on the page 
* Event Listener: waits for a specific even and triggers an action based on the event 
* An event is handleded once an execution stack is emptied
* Message queue
  * where all the events from the browser are put
  * Occurs once the stack is emptied
  * the callback function in an event listener does not require `()` since that is implicit.And if we use the `()`, then it would be called immediately, and we only want it called when the event listener is triggered.

An **anonymous function** is a function that does not have a name. It can be included directly as the callback function. It cannot be reused. 

*Inheritance* in JS is done through the **prototype property** that every object has

The *prototype chain* end with the object class, and then null. If the prototype method goes up the full chain is not in the object class, then it is null. 

A constructors prototype is not the prototype of the constructor, but the prototype of all instances created through it. Example: The person prototype, would be all the people created from this person object. 

The prototype properties contain properties belonging to the entire class rather than each instantiated object. These are the properties that are inhertited when instantiation occurs.

The `new` variable points `this` at the new empty object rather than the global object.

Can use `Object.create(prototype, ...)` to specify the prototype


Expressions are wrapped in parantheses. Craete an **Immediately Invoked Functions Epxression (IIFE)** by wrapping an an anonymous function without a name in parantheses
```js
(function() {
  // Function stuff
})();
```
This is good for data privacy -- the function cannot be accessed client-side. But it can only be used once since there is no name to access it again.Does not interfere with global variables. 

### call, apply, bind

`.call` allows us to set what the `this` points to. This allows for method borrowing between objects. Same with `.apply` where `.call` takes all the properties as individual argument and `.apply`takes them as an array. The functions are immediately called in this scenario

`.bind` does the above as well, but stores a copy of the function rather than calling it. 

The first argument for all three of these functions are what `this` should be set to.

This presets the parameters -- also called **currying**. 

### Closures
An inner function always has access to the a variables and parameters of the outer function, even after the outer function has returned.The scope chain keeps the information.The scope chain always stays intact

