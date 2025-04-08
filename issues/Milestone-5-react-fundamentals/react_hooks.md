# Milestone: React Fundamentals

## Understanding React Hooks: useEffect
### Goal
Learn how to use the useEffect hook to handle side effects in React components.

## Tasks
- [x] Research how useEffect works and when to use it.
The `useEffect` hook is a fundamental feature of React that allows developers to perform **side effects** in functional components. Side effects include operations such as data fetching, subscriptions, timers, manually changing the DOM, and logging — actions that can affect components outside the scope of the current render.

`useEffect` is called after the component renders and ensures the DOM is updated before executing its logic. It accepts two arguments" **a callback function** (the effect) and an optional **dependency array**. The dependency array determines when the effect should re-run:
  - If the array is empty `[]`, the effect runs only once after the initial render (similar to `componentDidMount`).
  - If it includes specific variables, the effect runs only when those variables change.
  - If omitted, the effect runs after every render, which can lead to performance issues or infinite loops if not handled correctly.

Another important feature of `useEffect` is its **cleanup function**, which is returned from the callback. This cleanup runs before the component unmounts or before the effect re-runs. It's commonly used to clean up subsccriptions, event listeners, or timers.

Developers typically use `useEffect` for tasks such as:
  - Fetching data from APIs
  - Setting up or cleaning up event listeners
  - Synchronising external systems (e.g., localStorage or web sockets)
  - Running code in response to prop or state changes
Source: [useEffect](https://react.dev/reference/react/useEffect)
According to the official React documentation, "`useEffect` serves the same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in React classes, but unified into a single API".
Source: [Legacy React APIs](https://react.dev/reference/react/legacy)

- [x] Create a component that:
  - Logs a message when it mounts and unmounts.
  - Fetches data from an API when a button is clicked.
  - Implements a cleanup function.

- [x] Push your component to GitHub.

- [x] Reflection (in react_hooks.md):
  - When should you use useEffect instead of handling logic inside event handlers?
    `useEffect` is useful when dealing with **side effects that happen independently** of direct user interactions. For example, logic that runs:
    - when the component mounts (e.g., fetching data on page load),
    - when a value in state or props changes (e.g., syncing with localStorage), or
    - when something needs to be cleaned up when the component unmounts (e.g., removing event listeners or canceling a timer).
  While event handlers are great for actions like clicking buttons or typing into inputs, `useEffect` gives more control over **when and how side effects should occur**, especially when they depend on changes in state or props.
  During testing, I noticed that even without clicking anything, my `useEffect` ran twice. I later discovered this was because **React’s Strict Mode in development deliberately mounts and unmounts components twice** to help catch side-effect bugs. This confirmed why using `useEffect` (with proper cleanup) is important for avoiding unexpected behavior.

  - What happens if you don’t provide a dependency array?
    If no dependency array is provided, the `useEffect` callback runs **after every render**, which can cause:
    - repeated API calls,
    - performance issues,
    - or even **infinite loops** if state is updated inside the effect.

    To prevent this, an **empty array (`[]`)** should be provided if the effect only needs to run once after the component mounts. I used this in my code to log "Component mounted" and "Component unmounted", and it worked exactly once — unless in development mode with StrictMode enabled, where it intentionally runs twice.

  - How can improper use of useEffect cause performance issues?

    Improper usage of `useEffect` can seriously impact performance, especially if:
    - Expensive operations (e.g., API calls or computations) run on **every render** unnecessarily
    - You forget to include proper **dependencies**, causing effects to run too often or too little
    - You don’t implement **cleanup functions**, which could lead to memory leaks or duplicated listeners/timers

    For example, I used a `fetch` call inside `useEffect`, and if I hadn't properly managed dependencies or state, it might have fired repeatedly or failed to clean up. Also, using a button-triggered state change helped limit when the fetch ran — showing the importance of mixing `useEffect` with event handlers correctly.

    React’s Strict Mode also helped me realize that without clean cleanup logic, unmounting and remounting can lead to **duplicate effects**, reinforcing the need to use `return` statements in `useEffect` to cancel or clean up side effects.
______________________________________

## Optimizing Performance with useMemo
### Goal
Understand how useMemo helps optimize expensive calculations in React.

## Tasks
- [x] Research how useMemo works and why it’s useful.
  `useMemo` is a React Hook that allows developers to **memoize the result of an expensive computation**. It returns a cached version of the computed value and only recalculates it when one of the dependencies has changed.

  The `useMemo` hook accepts two arguments:
  1. A function that returns the computed value
  2. A dependency array that determines when the memoized value should be recalculated

  **Why It's Useful**

  In React, any change to state or props can cause a component to re-render. Without `useMemo`, all functions and variables inside the component body—including expensive calculations—will run again during every render.

  `useMemo` helps improve **performance** by preventing these unnecessary recalculations. It is especially useful when:
  - Performing CPU-heavy calculations (e.g., filtering large lists)
  - Rendering large or complex UI components
  - Avoiding re-running logic when unrelated state changes

  **Example Use Case**
  A typical use case might involve a heavy computation, such as sorting a large dataset, where you only want to re-sort if the dataset or sort criteria actually change. With `useMemo`, this computation will only re-run when those specific dependencies change.
  Source: [useMemo](https://react.dev/reference/react/useMemo)

- [x] Create a component that:
  - Renders a large list of numbers.
  - Implements an expensive calculation that runs only when necessary.
  - Uses useMemo to prevent unnecessary re-computation.
- [x] Push your component to GitHub.

- [x] Reflection (in react_hooks.md):
  - How does useMemo improve performance?
    In my experience, useMemo significantly improves performance by memoizing the results of expensive computations. This means that the computation is only re-executed when its dependencies change, which helps avoid unnecessary recalculations. By doing this, useMemo reduces the rendering workload and makes my application faster and more efficient.

  - When should you avoid using useMemo?
    I've learned that it's best to avoid using useMemo for lightweight computations or when the performance gain is negligible. Overusing useMemo can make the code more complex without providing significant benefits. It's important to use it judiciously and only when there's a clear performance advantage.

  - What happens if you remove useMemo from your implementation?
    If I remove useMemo from my implementation, the expensive calculation will run on every render, regardless of whether the inputs have changed. This can lead to performance issues, especially when dealing with large datasets or complex computations. Without useMemo, my application could become slower and less responsive.
________________________________________

## Preventing Unnecessary Renders with useCallback
### Goal
Learn how useCallback helps optimize function references in React.

## Tasks
- [x] Research how useCallback works and when to use it.
  React's `useCallback` hook is designed to optimize performance by memoizing functions, ensuring that the same function instance is used between renders unless its dependencies change. In a React component, functions are re-created on every render, which can lead to unnecessary re-renders of child components if these functions are passed as props. By wrapping a function in `useCallback`, React stores the function and only creates a new instance when one of its dependencies has changed. This is particularly useful when the function is passed to components wrapped with `React.memo` or used in dependency arrays for other hooks, such as `useEffect`.

  For instance, consider a scenario where a parent component passes a callback to a memoized child component. Without `useCallback`, even if the function logic remains the same, its reference will change on each render, causing the child component to re-render unnecessarily. With `useCallback`, the function reference remains stable as long as its dependencies remain unchanged, thus preventing those extraneous renders and potentially improving performance.

  However, it's important to note that `useCallback` isn't a silver bullet for performance issues. It introduces its own overhead by requiring dependency comparisons on every render. Therefore, it should be used selectively—primarily in situations where passing functions as props or using them as dependencies in other hooks leads to significant re-renders that affect performance. In simpler cases, or where the function is not passed to optimized components, the benefits might be negligible, and using inline functions may be preferred for code clarity.

- [x] Create a component that:
  - Passes a function as a prop to a child component.
  - Uses useCallback to prevent unnecessary re-renders.
  - Uses React DevTools to confirm when re-renders occur.
- [x] Push your component to GitHub.

- [x] Reflection (in react_hooks.md):
  - What problem does useCallback solve?
    `useCallback` is used to memoize function references in React. It prevents functions from being re-created on every render, which is especially useful when passing functions as props to child components. This helps avoid unnecessary re-renders in child components that depend on the reference equality of their props (such as components wrapped in `React.memo`).

  - How does useCallback work differently from useMemo?
    - **useMemo:**  
      Memoizes the *result* of an expensive computation. It returns a computed value and only re-computes when its dependencies change.

    - **useCallback:**  
      Memoizes the *function* itself. It returns the same function instance unless its dependencies change. Essentially, `useCallback(fn, deps)` is equivalent to `useMemo(() => fn, deps)`.

  - When would useCallback not be useful?
    - When the function is not passed as a prop to child components or used as a dependency in other hooks, the performance benefit is negligible.
    - In components that do not re-render frequently, memoizing functions may add unnecessary complexity.
    - Overusing `useCallback` can lead to more complex code without significant performance gains, so it should be used selectively in performance-critical scenarios.
________________________________________

