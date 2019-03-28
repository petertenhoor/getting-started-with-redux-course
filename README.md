# Getting started with Redux course

## Lesson 1

The state tree of your application is a single javascript object.

## Lesson 2

- Changing the state tree can only be done by dispatching an action.
- Actions always have a type. E.g. ```INCREMENT``` or ```DECREMENT```

## Lesson 3

Functions that you're going to write in Redux have to be pure, and you need to be mindful of that.

```
// Pure functions
function square(x) {
  return x * x;
}
function squareAll(items) {
  return items.map(square);
}

// Impure functions
function square(x) {
  updateXInDatabase(x);
  return x * x;
}
function squareAll(items) {
  for (let i = 0; i < items.length; i++) {
    items[i] = square(items[i]);
  }
}
```

## Lesson 4

To describe state mutations, you have to write a function that takes the previous state of the app, the action being dispatched, and returns the next state of the app. This function has to be pure. This function is called the Reducer.

## Lesson 5

Simple reducer function:

```
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}
```

## Lesson 6

```npm install redux```

```
import {createStore} from Redux

//create reducer
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1
    case 'DECREMENT':
      return state - 1
    default:
      return state
  }
}

//create store
const store = createStore(counter)

//get current state of store
console.log(store.getState())

//dispatch an action
store.dispatch({type: "INCREMENT"})

const render = () => document.body.innerText = store.getState()

//execute method on state change
store.subscribe(render)

//initial render
render()

//increment on body click
document.addEventListener("click", () => store.dispatch({type: "INCREMENT"})

```
