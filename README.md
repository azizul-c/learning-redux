# Learning Redux

# Important Takeaways

Generated by ChatGPT. <br/>

## Redux Components

### **🔹 Actions**

Actions are plain JavaScript objects that describe an event or an intention to modify the state. They carry information (payload) that describes what should be updated in the state. Actions must have a `type` property that indicates the type of action being performed. Here's an example of an action:

```javascript
const incrementCounter = {
  type: "INCREMENT_COUNTER",
  payload: 1,
};
```

Actions are typically dispatched to trigger state updates. They are created using action creators, which are functions that return the action objects.

### **🔹 Reducers**

Reducers are pure functions responsible for specifying how the application's state should change in response to actions. They take the current state and an action as input and return a new state based on that action. Reducers should not modify the original state; instead, they create a new state object reflecting the desired changes.

A reducer typically uses a switch statement to determine the action type and perform the appropriate state update. Here's an example of a reducer:

```javascript
const initialState = {
  counter: 0,
};

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case "INCREMENT_COUNTER":
      return {
        ...state,
        counter: state.counter + action.payload,
      };
    case "DECREMENT_COUNTER":
      return {
        ...state,
        counter: state.counter - action.payload,
      };
    default:
      return state;
  }
}
```

### **🔹 Store**

The store is the central hub that holds the application's state and facilitates interaction between components. It brings together the actions and reducers. The store is created using the `createStore` function from the Redux library and accepts a root reducer as an argument.

The store provides methods like `getState` to access the current state, `dispatch` to dispatch actions, and `subscribe` to register listeners that are called whenever the state is updated.

```javascript
import { createStore } from "redux";

const store = createStore(counterReducer);
```

### **🔹 Middleware (optional)**

Middleware in Redux provides a way to intercept dispatched actions before they reach the reducer. It allows for additional logic to be applied, such as logging, handling asynchronous actions, or modifying actions.

Middleware is applied using the `applyMiddleware` function from Redux. Popular middleware libraries include Redux Thunk, Redux Saga, and Redux-observable.

```javascript
import { createStore, applyMiddleware } from "redux";
import thunk from "redux-thunk";

const store = createStore(counterReducer, applyMiddleware(thunk));
```

These components work together to create a predictable state management system. Actions are dispatched, reducers handle those actions to update the state, and the store holds and provides access to the state. Components can subscribe to the store to receive updates and dispatch actions as needed.

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in your browser.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

