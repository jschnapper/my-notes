# React & Redux

These two libraries are disconnected

## React
Provides the views 

React's `<Provider store={store}><App /></Provider>` (provider tag) reads the redux store. Whenver the redux store is updated, the provider can inform all of its children to update. The `<Provider>` is in the `index.js`.

## Redux
Handles the data 

It holds the collection of data the encompasses the whole app 

This is the actual data, as well as the meta data that comes from the actual data

*All of the data is contained in a single, plain js object.* This object is the **application state**

Application state is different from component state, which can still say `this.state.something`, which will be different from the application state.

Redux manages global state and data -- allowing states to be accessed across multiple components instead of having to be passed down a component

### React-Redux
In order to connect react and redux, need a separate library: react-redux, and then connect through **containers** 

A **container** is a react component that has direct connection to the state managed by Redux 

Redux sometimes refers to these containers as "smart components". Regular components to redux are "dumb components"

Should put these containers in separate directory from components

We want the *most parent component that cares about a particular state* to be a container. We only create containers for components that care about a state -- if a parent component doesn't care about that state, then it should not be the container (i.e. the App does not need to be the container just because it contains all the components) 

Whenever the state changes, the container automatically rerenders 

### Reducers
* A **reducer** is a function that returns a piece of the application state -- it returns the value of the state 
* There can be various pieces of state and, thus, many reducers 
* The reducers make up the application state

**Reducers** get two arguments:
1) the current state
2) an action

* Reducers are only called when an action occurs
* The state argument is *not the application state*, only the state that this reducer is responsible for
* The reducer functions are called whenever an application action occurs, even if unrelated to this reducer. For this reason, the reducers should check what action has occurred and do nothing if it is unrelated to the reducer's state
* A reducer ***cannot return undefined***, but `null` is okay. But make checks since when the application first starts, redux sends a few actions to check things... so if you return null and one of your actions is using the state already to get some property, it will be null and you'll get an error. **Should create check in the render methods that are creating a errors**
* A reducer must always return a clean state -- it ***cannot mutate the state***

All reducers should ne imported into a main reducer file in the reducer directory, like `index`. And within the file, all reducers should be within the `combineReducers` function where the reducer is a value to some key. 

**All keys in the `combineReducers` function becomes a key in the global state**. Each key is assigned to one reducer. Whatever that reducer returns is available as that key's piece of application state.

***NEVER MANIPULATE STATE DIRECTLY***
If need to use array, don't do `state.push(...)`, use this instead because it creates a new array: `state.concat(...)`
ES5 where the new item is at back of array:
```jsx
state.concat([ action.payload.data ]);
```
ES6 where the new item is at the front of the array:
```jsx
[ action.payload.data, ...state];
```
Both of the above create **NEW ARRAYS**

### Notes Implementation  

the function `mapStateToProps` takes the app's state as an argument and returns it as `this.props` in the component

export the above function and use the react-redux function `connect` thats take a function like `mapStateToProps` and a component to produce a container
```js
export default connect(mapStateToProps)(ComponentName);
```

```js
export default connect(mapStateToProps, mapDispatchToProps)(ComponentName);
```

### Actions & Connect
An action creator is a function that returns an action

An action is an object that flows through all of the reducers and normally has two values:
1) A type that describes the purpose of the action
2) A payload that further describes the action that has been triggered; holds some data

An action **always contains a type** and **sometimes contains a payload**. The 'type' and 'payload' are keys. 

Reducers use that action to produce a different value for their state, if needed 

An action creator is intitiated by any event from a click to an ajax request

Flow:
1) An event occurs that triggers an action creator
2) The action creator returns an object which is called an action
3) That action is automatically sent to **all** reducers 
4) Depending on the action, the reducer will then determine if it will return a different piece of state or the same, current state 
5) This new state goes to the application state 
6) The application state goes into the react application which causes all the components to rerender  

The **container** class requires to import `connect` from `react-redux`, the action creator function from the actions directory and whatever file, and `bindActionCreators` from `redux`.

`bindActionCreators` takes the return value from the action creator function and provides it to all of the reducers. This is done by passing the action creator *which is set as a value to a key* and `dispatch` function to the `bindActionCreators`

`mapDispatchToProps` is a function that returns `bindActionCreators`. The return of this function returns props to the container.

**Consistency**
To keep action types consistent between creators and reducers, consider storing the type value as a variable. Example:
```js
// Need to export since it needs to be accessed by exported action creator
export const FETCH_WEATHER = "FETCH_WEATHER";

// Action creators return actions
// An action is an object that always needs a type
export function fetchWeather() {
  return {
    type: FETCH_WEATHER
  };
}
```
This prevents the need to copy and paste strings between files and to have accidental typos since we are now exporting and importing a variable. Also change whatever the variable is stored as rather than have to go through each file to change it. 


### Middleware
Follows the same *flow* as a reducer with one additional step inserted in the middle: **Middleware**

**Middleware**: depending on an actions type, payload, and any other number of things, middleware will determine if it will let the action:
* pass
* be manipulated
* be logged
* stop

This occurs before passing it to the reducers (if it decides to let it go to the reducers)

There can be many steps of middlewares or zero steps of middleware. They are all functions for actions that occur before passed to the reducer. 

*Essentially: All actions flow through the middleware step and the middlewares can modify these actions*

Once a middleware package is installed, import and apply it in the main directory in `index.js`. Also known as *hooking* the middleware in to the application. 

Example:
```js
// The first argument in this example is the middleware package
const createStoreWithMiddleware = applyMiddleware(ReduxPromise)(createStore);
```


### Redux and Ajax
Uses promises and middleware 
1) Action enters middleware
**(redux promise middleware flow)**
2) does the action have a promise as a payload
----
3) If has promise as payload: 
  * stop action
  * after promise is resolved, create new action and send to reducer 
----
3) If no promise as payload:
  * Let go to reducer

