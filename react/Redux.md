# Redux
 - [Redux](https://redux.js.org/) is a predictable state container for JavaScript apps.
 - It is commonly use with React with a large ecosystem of addons available.
 - The Redux core library is available as a package on NPM for use with a module bundler or in a Node application.
```bash
npm i redux
```

This is a small example of "one-way data flow":

 - State describes the condition of the app at a specific point in time
 - The UI is rendered based on that state
 - When something happens (such as a user clicking a button), the state is updated based on what occurred
 - The UI re-renders based on the new state
![One Way Data Flow](https://redux.js.org/assets/images/one-way-data-flow-04fe46332c1ccb3497ecb04b94e55b97.png)
 - The **state**, the source of truth that drives our app.
 - The **view**, a declarative description of the UI based on the current state.
 - The **actions**, the events that occur in the app based on user input, and trigger updates in the state.

## Actions
 - An action is a plain JavaScript object that has a `type` field. You can think of an action as an event that describes something that happened in the application.

 - The `type` field should be a string that gives this action a descriptive name, like `"todos/todoAdded"`. We usually write that type string like `"domain/eventName"`, where the first part is the feature or category that this action belongs to, and the second part is the specific thing that happened.

 - An action object can have other fields with additional information about what happened. By convention, we put that information in a field called `payload`.

 - A typical action object might look like this:
```ts
const addTodoAction = {
  type: 'todos/todoAdded',
  payload: 'Buy milk'
}
```

## Reducers
 - A reducer is a function that receives the current state and an action object, decides how to update the state if necessary, and returns the new state: (state, action) => newState. You can think of a reducer as an event listener which handles events based on the received action (event) type.
 - Reducers must always follow some specific rules:
    - They should only calculate the new state value based on the state and action arguments
    - They are not allowed to modify the existing state. Instead, they must make immutable updates, by copying the existing state and making changes to the copied values.
    - They must not do any asynchronous logic, calculate random values, or cause other "side effects"
 - The logic inside reducer functions typically follows the same series of steps:
   - Check to see if the reducer cares about this action
     - If so, make a copy of the state, update the copy with new values, and return it
   - Otherwise, return the existing state unchanged
 - Here's a small example of a reducer, showing the steps that each reducer should follow:

```ts
const initialState = { value: 0 }

function counterReducer(state = initialState, action) {
  // Check to see if the reducer cares about this action
  if (action.type === 'counter/incremented') {
    // If so, make a copy of `state`
    return {
      ...state,
      // and update the copy with the new value
      value: state.value + 1
    }
  }
  // otherwise return the existing state unchanged
  return state
}
```

## Store
 - The current Redux application state lives in an object called the store.

 - The store is created by passing in a reducer, and has a method called getState that returns the current state value:
```ts
import { configureStore } from '@reduxjs/toolkit'

const store = configureStore({ reducer: counterReducer })

console.log(store.getState())
// {value: 0}
```

## Dispatch
 - The Redux store has a method called dispatch. The only way to update the state is to call store.dispatch() and pass in an action object. The store will run its reducer function and save the new state value inside, and we can call getState() to retrieve the updated value:
```ts
store.dispatch({ type: 'counter/incremented' })

console.log(store.getState())
// {value: 1}
```
 - You can think of dispatching actions as "triggering an event" in the application. Something happened, and we want the store to know about it. Reducers act like event listeners, and when they hear an action they are interested in, they update the state in response.

## Selectors
 - Selectors are functions that know how to extract specific pieces of information from a store state value. As an application grows bigger, this can help avoid repeating logic as different parts of the app need to read the same data:
```ts
const selectCounterValue = state => state.value

const currentValue = selectCounterValue(store.getState())
console.log(currentValue)
// 2
```

## Core Concepts and Principles
 - The global state of your application is stored as an object inside a single store. Any given piece of data should only exist in one location, rather than being duplicated in many places.
 - The only way to change the state is to dispatch an action, an object that describes what happened.
 - To specify how the state tree is updated based on actions, you write reducer functions. Reducers are pure functions that take the previous state and an action, and return the next state. Like any other functions, you can split reducers into smaller functions to help do the work, or write reusable reducers for common tasks.

## Redux Application Data Flow
 - State describes the condition of the app at a specific point in time
 - The UI is rendered based on that state
 - When something happens (such as a user clicking a button), the state is updated based on what occurred
 - The UI re-renders based on the new state

### For Redux specifically, we can break these steps into more detail:

 - Initial setup:
   - A Redux store is created using a root reducer function
   - The store calls the root reducer once, and saves the return value as its initial state
   - When the UI is first rendered, UI components access the current state of the Redux store, and use that data to decide what to render. They also subscribe to any future store updates so they can know if the state has changed.
 - Updates:
   - Something happens in the app, such as a user clicking a button
   - The app code dispatches an action to the Redux store, like dispatch({type: 'counter/incremented'})
   - The store runs the reducer function again with the previous state and the current action, and saves the return value as the new state
   - The store notifies all parts of the UI that are subscribed that the store has been updated
   - Each UI component that needs data from the store checks to see if the parts of the state they need have changed.
   - Each component that sees its data has changed forces a re-render with the new data, so it can update what's shown on the screen
 - Here's what that data flow looks like visually:

![Redux Data Flow Diagram](https://redux.js.org/assets/images/ReduxDataFlowDiagram-49fa8c3968371d9ef6f2a1486bd40a26.gif)

## Redux Toolkit
 - Redux Toolkit allows us to write shorter logic that's easier to read, while still following the same Redux behavior and data flow.
 - RTK includes utilities that help simplify many common use cases, including [store setup](https://redux-toolkit.js.org/api/configureStore), [creating reducers](https://redux-toolkit.js.org/api/createreducer) and writing immutable update logic, and even [creating entire "slices" of state at once](https://redux-toolkit.js.org/api/createslice).
 - Redux Toolkit is available as a package on NPM for use with a module bundler or in a Node application.
```bash
npm i @reduxjs/toolkit
```
```ts
// Basic Redux
import { createStore } from 'redux'

function counterReducer(state = { value: 0 }, action) {
  switch (action.type) {
    case 'counter/incremented':
      return { value: state.value + 1 }
    case 'counter/decremented':
      return { value: state.value - 1 }
    default:
      return state
  }
}

let store = createStore(counterReducer)

store.subscribe(() => console.log(store.getState()))

store.dispatch({ type: 'counter/incremented' }) // {value: 1}
store.dispatch({ type: 'counter/incremented' }) // {value: 2}
store.dispatch({ type: 'counter/decremented' }) // {value: 1}
```
 - Instead of mutating the state directly, you specify the mutations you want to happen with plain objects called actions. Then you write a special function called a reducer to decide how every action transforms the entire application's state.
 - In a typical Redux app, there is just a single store with a single root reducing function. As your app grows, you split the root reducer into smaller reducers independently operating on the different parts of the state tree. This is exactly like how there is just one root component in a React app, but it is composed out of many small components.
 - This architecture might seem like a lot for a counter app, but the beauty of this pattern is how well it scales to large and complex apps. It also enables very powerful developer tools, because it is possible to trace every mutation to the action that caused it. You can record user sessions and reproduce them just by replaying every action.
```ts
// Basic Redux Toolkit (RTK)
import { createSlice, configureStore } from '@reduxjs/toolkit'

const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    incremented: state => { state.value += 1 },
    decremented: state => { state.value -= 1 }
  }
})

export const { incremented, decremented } = counterSlice.actions

const store = configureStore({
  reducer: counterSlice.reducer
})

store.subscribe(() => console.log(store.getState()))

store.dispatch(incremented()) // {value: 1}
store.dispatch(incremented()) // {value: 2}
store.dispatch(decremented()) // {value: 1}
```
