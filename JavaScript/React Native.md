# React Native

#### Components
One component per file

All stylings go in the component file

Props allow us to reuse components

**Index**
The index app component can only return 1 single tag. So if returning mutltiple components, wrap in View tag

In any React Native app, must register one component to the application. And the name of the string must match with the project 

**Functional Components**
* return jsx
* can't fetch data
* present static data

**Class Component**
* used for dynamic sources of data
* knows when it gets rerendered 
* more functional, but require more code
* Do not require semi-colons at the end of a class

*Class components* require a render method, which can wrap the return statement
*Class components* have *lifecycle* methods 
* Class components know when they are going to be rendered to the screen 
* Lifecycle methods are placed on a class and eventually called at some point

ex: *componentWillMount()* is called right before the component is going to be rendered. Good place to fetch data

### Network Request & States**
Because the process is asynchronous, the components can be rendered before the data is received -- therefore, need to render the components again as well. The asynchronous nature is good because it means the user can continue to interact with the device before the data is received rather than have to wait until all the data is loaded.

A **state** is a plain js object available to only class components that records and responds to user-triggered events

Functional components cannot access state

***Always modify and change state with `this.setState` only*** However, you can *initialize* a state with `state = `

**Do not** change state with `this.state`

### States vs Props
When communicating from parent component to child component, **use props**
For internal record keeping, **use states**


Whenever rendering elements inside of an array, each component inside the array must have a key a unique key property that doesn't change (don't use the index in the array because that can change) -- this is so the computer knows which component it is rendering.



