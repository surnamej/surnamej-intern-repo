# Milestone: Redux 

## Introduction to Redux Toolkit (State Management)
### Goal
Manage global state effectively using Redux Toolkit.

## Tasks
- [x] Install Redux Toolkit and React Redux.
Install by using following command in my React project root:
```bash
npm install @reduxjs/toolkit react-redux
```

- [x] Create a Redux store and configure a slice for a counter.
Firstly, I modified the folder structure:
- `app/` is for global app setup
- `feature/` is for feature specific logic group together
- Make it scalable when I add more slice like `auth`, `user`, etc.
```
src/
├── app/
│   └── store.js
├── features/
│   └── counter/
│       └── counterSlice.js
│       └── Counter.jsx
```
Secondly, the task is given me to create a Redux store and configure a slice for a counter. In this task, I learned that:
  - Centralized State: Redux store provides a single source of truth for managing shared state across the app. 
  - Modular Structure: `createSlice` organizes state, reducers, and actions in a clean, scalable way.
  - Redux Toolkit simplifies Redux setup by auto-generating action creators.
  - Slices improve code readability and make updates easier to manage.
  - `configureStore` includes built-in support for debugging and middleware.

- [x] Use useSelector and useDispatch to connect Redux to the Counter.js component.
  - `useSelector()` is used to select a specific part of the global state and use it in the component.
  - `useDispatch()` is used to dispatch actions to update the Redux store.

- [x] Push your Redux setup to GitHub.
- [x] Reflection (in redux_fundamentals.md):
  - When should you use Redux instead of useState?
    From my perspective, I will prefer using useState when the state is local to a single component and doesn't need to be shared. It's quick, simple, and gets the job done for small pieces of UI — like toggling modals or tracking input values.
    However, I turn to Redux (especially Redux Toolkit) when the state needs to be accessed or updated by multiple components. It's especially helpful when the app grows and things start to feel messy with props or too many useState hooks scattered around.
    Redux gives me a centralized way to manage state, and I like how slices organize both the state and logic in one place. Plus, with useSelector and useDispatch, connecting components to that global state feels clean and maintainable.
    So, for larger apps or anything with shared, complex, or interdependent state, I’d definitely reach for Redux over useState.

  🤔 Think of Redux like a shared whiteboard in a room.
  - Any component (person) can read from it (useSelector)
  - Any component can change it (useDispatch)
___________________________________________________________

## Using Selectors in Redux Toolkit
### Goal
Learn how to extract state efficiently from Redux.

## Tasks
- [x] Create a selector function to get the current counter value from Redux.
- [x] Use useSelector to access the counter value in multiple components.
- [x] Modify the app to display different messages based on the counter value.
From the following steps, I created a second component (CounterMessage.jsx) that also uses `useSelector` to show a message'
```jsx
iimport React from 'react';
import { useSelector } from 'react-redux';

function CounterMessage() {
  const count = useSelector((state) => state.counter.value);

  return (
    <p className="text-gray-500 mt-2">
      {count >= 10
        ? "High score!"
        : count >= 5
          ? "Halfway there!"
          : `Keep going: ${count}`}
    </p>
  );
}

export default CounterMessage;
```
Then in Counter.jsx, import and use:
```jsx
import CounterMessage from './CounterMessage';
// ...
<CounterMessage />
```
Now I have used `useSelector` in multiple components both Counter.jsx and CounterMessage.jsx. Both are reading from the same Redux state, and will always show the same, updated value — no props needed.

- [x] Push your Redux setup to GitHub.
- [x] Reflection (in redux_fundamentals.md):
  - What are the benefits of using selectors instead of directly accessing state?
    
    I find that using selectors makes my code cleaner and more maintainable. Instead of repeating the same `state.counter.value` logic in multiple components, I can just create a selector once and reuse it anywhere I need that piece of state. This helps reduce duplication and keeps things consistent across my app.
    Selectors also make it easier to update the shape of my state later. If the state structure changes, I only need to update the selector function, not every component that uses it.
    Another benefit is that selectors are easier to test. Since they're just plain functions, I can write unit tests for them without needing to set up a full Redux environment. If I want to optimize performance later, I can also memoize selectors to avoid unnecessary re-renders.
    Overall, using selectors helps me write more modular, reusable, and scalable Redux code.
___________________________________________________________
