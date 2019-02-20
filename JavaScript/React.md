# React
React is composed of 2 libraries: React and ReactNative

React
* Knows how a  component should behave
* Knows how to take a bunch of components and make them work together

React Native (portal to mobile device) 
* Knows how to take the output from a component and place it on the screen
* Provides the default core components (image, text)

The core react library works with components. To insert and render these components into the DOM requires a second library, **react-dom**.

## Fundamentals

`index.js` is the very root of the application on the client side. It contains the initial bootup logic for application. It puts together the data layer considerations of the application (**like redux**)

`App.js` a single component within the index.js that renders the application (**the react portion, and react router portion, what the users sees**)

### Components 
When creating a component, we create a class (a type) of component. We can have many instances of this class.

```jsx
// Class
const App = function () {
  return <div>hi!</div>
}
// Instance of class with content
<App>...</App>
  
// Instance of class without an exta content can be self closing
<App />
```


**One Component per File**

**Function Component**
* A function
* Some info goes in, some JSX comes out 
* `props` is an argument

**Class Component**
* Internal record keeping 
* Make it aware when things change about itself
* Every class component requires a render method *that returns jsx*
* Extend the class with `extends Component` for extra functionality
* `props` can be accessed anywhere with `this.props`

**Naming Convention**
When exporting a class or react component, the name of the file should start with a capital letter. If exporting a function, the name of the file should start with a lowercase letter.

### State
A plain js object that records and reacts to user events. Each class based component we define has its own state object. Whenever a state changes, the component and all of its children rerenders.

**Only class-based components have state**

***Always manipulate state with `this.setState`***. Only in the constructor will you use `this.state=`.

Functional components can contain class components

### Controlled Component

* It's value is set by the state
* It's value only changes when the state changes 
* When asking for the value of an input, for example, you ask for the value of the state
  * Therefore, need to initialize the state first within the constructor

### Downward Dataflow
Only the most parent element should be responsible with fetching the data 

### Arrays
Provide a key to items when iterating through lists to make them unique and searchable for rendering and data

### import
Importing a word imports the entire object
```js
import React from "react";
```
import in { word } will import just the property so we don't need to always reference the object

```js
import React, { Component } from "react"
// could also just work with import { Component }
// Instead of React.Component, can now just say Component
```


### Binding
When we have a callback function in a dom element that makes a reference to `this`, we need to bind the context. 

Example:
```jsx
class SearchBar {
  constructor(props) {
    super(props);
    
    this.onFormSubmit = this.onFormSubmit.bind(this);
  }
}

onFormSubmit(event) {
  this.props.fetchWeather(this.state.term);
}
    
<form onSubmit={this.onFormSubmit} className="input-group">
  ...
</form>
```
