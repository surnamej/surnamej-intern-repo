# Milestone: Jest for unit tests

## Introduction to Unit Testing with Jest

### Goal

Learn the basics of unit testing in React using Jest.

### Why is this important?

Focus Bear relies on automated testing to ensure the stability of features across updates. Writing unit tests prevents regressions and improves code reliability.

## Tasks

- [x] Research what Jest is and why unit tests are important.
  Jest is a JavaScript testing framework built by Meta, often used with React. It lets you write tests to:
  - Verify your code works correctly.
  - Catch bugs before they reach users.
  - Make changes without breaking existing functionality (regression testing).

  Source: [Testing with Jest](https://www.geeksforgeeks.org/testing-with-jest/)

  My project use Vite. **Vite** is designed for native ESM and uses its own plugin system for fast frontend tooling (like dev server, hot reload, etc).
  
  Jest is not officially supported by Vite, because:
  - Jest uses its own bundler and mocking system.
  - Vite’s plugin architecture doesn’t integrate cleanly with Jest.

- [x] Set up Jest in your React project (if not already included).
  **Step 1: Install Required Packages**

  ```bash
    npm install --save-dev jest babel-jest @babel/preset-env @babel/preset-react jest-environment-jsdom
  ```

  **Step 2: Create babel.config.mjs**
  This lets Jest understand modern React code.

  ```mjs
  // babel.config.js
  export default {
    presets: ['@babel/preset-env', '@babel/preset-react'],
  };
  ```

  **Step 3: Created a Jest config for ESM**

  ```mjs
  // jest.config.mjs
  export default {
    transform: {
      '^.+\\.[jt]sx?$': ['babel-jest', {
        presets: ['@babel/preset-env', '@babel/preset-react']
      }],
    },
    extensionsToTreatAsEsm: ['.jsx'], // ✅ removed '.js' to avoid warning
    testEnvironment: 'jsdom',
  };
  ```

  **Step 4: Updated your test script in `package.json`**
  This avoids the shell script error on Windows and enables ESM support.

  ```json
  "scripts": {
  "test": "node --experimental-vm-modules ./node_modules/jest/bin/jest.js"
  }
  ```

- [x] Write a simple test for a utility function (e.g., a function that adds two numbers).

  ```js
  // math.js
  export function add(a, b) {
    return a + b;
  }
  ```

  Test file:

  ```js
  // math.test.js
  import { add } from '../app/math';

  test('adds two positive numbers', () => {
    expect(add(2, 3)).toBe(5);
  });

  test('adds negative and positive numbers', () => {
    expect(add(-1, 4)).toBe(3);
  });

  test('adds two negative numbers', () => {
    expect(add(-3, -2)).toBe(-5);
  });
  ```

- [x] Run the test and check that it passes.
![Pass](./Pass-test.png)

- [x] Push your test to GitHub.
- [x] Reflection (in unit_tests.md):
  - Why is automated testing important in software development?
  Automated testing is really important to me as a developer because it brings a lot of value to the development process:
  - It helps prevent regressions
    When I make changes to my code, automated tests catch bugs that might break existing features — which saves me from introducing new issues.
  - It boosts my confidence
    Knowing I have tests in place gives me peace of mind when refactoring or adding new features, because I know I’ll be alerted if something breaks.
  - It saves a ton of time
    Instead of manually checking every detail, my tests run in seconds and catch things I might miss by hand.
  - It helps me write better code
    Writing tests forces me to think more clearly about the structure and logic of my code, which usually leads to cleaner, more modular solutions.
  - It makes collaboration easier
    When working with a team, automated tests make it clear how the code is supposed to behave, and they help prevent accidental breakage when others make changes.

  - What did you find challenging when writing your first Jest test?
    Writing my first Jest test was definitely a bit tricky because of a few things:
    1. Unfamiliar syntax
       - Functions like describe(), test(), and expect() were completely new to me, especially since I wasn’t used to test-driven development.
    2. Setting up the environment
       - Working with modern stacks like Vite, ESM, and React made things more confusing — getting Babel configured properly, setting up jsdom, and handling module transforms took some trial and error.
    3. Mocking complexity
       - I found mocking things like APIs (fetch, axios) or child components to be harder than expected. It took some practice to understand how and when to mock correctly.
    4. Mental shift
       - The biggest challenge was probably the mindset change — instead of building features, I had to think about how those features might break and write tests to catch those failures in advance.

___________________________________________________________

## Testing Redux with Jest

### Goal

Learn how to test Redux slices and actions using Jest.

### Why is this important?

State management is central to Focus Bear’s functionality. Writing tests for Redux ensures that reducers and actions work as expected.

## Tasks

- [x] Research how to test Redux reducers and actions in Jest.

- [x] Create a simple Redux slice (if not already created).

- [x] Write a test that checks if a reducer updates state correctly.

- [x] Write a test for an asynchronous Redux action (if applicable).

- [x] Run the tests and check that they pass.

- [x] Push your test to GitHub.

- [x] Reflection (in unit_tests.md):
  - What was the most challenging part of testing Redux?
  - How do Redux tests differ from React component tests?
