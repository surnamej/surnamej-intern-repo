# Milestone: Debugging

## Research Best Debugging Techniques for React

### Goal

Understand and apply effective debugging techniques in React development.

## Tasks

- [x] Research best debugging techniques for React applications.
  - Explore tools like React DevTools, browser console, and VS Code debugger.
    1. Console Logging
      The most basic but widely used method. `console.log`, `console.error`, and `console.warn` can help to trace data and control flow.

    Tip: Avoid overusing logs in production; use feature flags or logging libraries like [debug](https://www.npmjs.com/package/debug) for more structured output.

    2. [React Developer Tools](https://react.dev/learn/react-developer-tools)
      React DevTools is a browser extension for Chrome and Firefox that lets you:
    - Inspect React component trees.
    - View props and state in real-time.
    - Highlight re-rendered components.
    3. [VS Code Debugger](https://code.visualstudio.com/docs/debugtest/debugging)
      VS Code provides a built-in debugger that can be configured to:
    - Set breakpoints in React code (even JSX).
    - Step through code execution.
    - Inspect local variables and call stacks.
  
  - Learn about error boundaries and how to handle runtime errors.
    Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of crashing the whole app.

    They work for:
    - Render phase errors
    - Lifecycle methods
    - Constructors of child components
  
    They don’t catch errors in:
    - Event handlers
    - Asynchronous code (e.g., setTimeout, fetch)
    - Server-side rendering
  
    Error boundaries must be **class components**.

    Source: [Use react-error-boundary to handle errors in React](https://kentcdodds.com/blog/use-react-error-boundary-to-handle-errors-in-react)

  - Investigate debugging performance issues using the React Profiler.
    The [React Profiler](https://react.dev/reference/react/Profiler) is a tool within React Developer Tools that lets you measure performance by recording how components render and update over time.

    It helps answer:
    "Which components are re-rendering too often or taking too long?"

    When using the React Profiler, the following key metrics and features are available to aid in performance analysis:
    - Commit Duration: Indicates the amount of time required to apply changes to the DOM after a component update. This helps identify render cycles that are costly in terms of performance.
    - Component Render Durations: Displays the time taken for each individual component to render. Components with unusually long render times may be candidates for optimization.
    - “Why Did This Render?” Feature: Provides insight into the specific reasons why a component re-rendered, such as changes in props or internal state. This is particularly helpful for tracing unnecessary re-renders.
    - Visualization Modes – Flamegraph and Ranked View:
      - Flamegraph: Offers a visual representation of the component tree, with colors indicating relative render times. Useful for identifying slow components in context.
      - Ranked View: Lists components in order of render cost, allowing developers to quickly pinpoint the most performance-intensive components.

    These features collectively enable a detailed examination of rendering behavior, empowering developers to make data-driven decisions when optimizing React applications.

- [x] Summarize key debugging strategies in react_debugging.md.
  - What are the most common debugging techniques?
    1. Console Logging (console.log, console.error): Quick inspection of variable values, control flow, and component lifecycle.
    2. Breakpoints & Step Debugging: Use browser DevTools or VS Code to pause execution and inspect call stacks.
    3. Error Boundaries: Catch and handle runtime rendering errors in component trees.
    4. React Developer Tools: Inspect props, state, and component hierarchy in real-time.
    5. Testing (Jest + React Testing Library): Prevent regressions and validate component behavior through unit/integration tests.

  - Which tools are most effective for React debugging?

    | Tool               | Use Case                                                             |
    |--------------------|----------------------------------------------------------------------|
    | **React DevTools** | Inspect props/state, detect re-renders, analyze performance          |
    | **VS Code Debugger** | Set breakpoints, step through JSX and TypeScript                  |
    | **Chrome DevTools** | Log inspection, network analysis, memory profiling                 |
    | **React Profiler** | Identify unnecessary re-renders and slow components                  |
    | **Sentry / LogRocket** | Monitor runtime errors and session data in production           |
    | **ESLint / TypeScript** | Catch syntax and type-related issues during development        |

  - How do you debug issues in large React codebases?
    - Break down the codebase into small, reusable components and separate concerns (Use folder structures like `components/`, `hooks/`, `services/`, `utils/`). This makes individual units easier to debug in isolation.
    - Debug with DevTools
      - Use VS Code debugger for server/client-side breakpoints.
      - Use React DevTools to inspect component state/props in real-time.
      - Use Chrome DevTools to monitor network requests and trace async bugs.
    - Automated Testing and CI
      - Write unit tests and integration tests to catch regressions.
      - Use Jest and React Testing Library to test logic and UI interactions.
      - Set up CI/CD pipelines to ensure tests run before merges.
    - Use the React Profiler to identify slow components and unnecessary re-renders, especially in large UIs with frequent state updates.
    - Add “debug mode” flags to expose internal state or logs when needed.
    - Keep documentation up to date to make debugging faster for all contributors.
    - Use Git history and `git blame` to track when bugs were introduced.

- [x] Commit and push your changes to GitHub.
