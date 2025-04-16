# Milestone: Clean code

## Understanding Clean Code Principles
### Goal
Understand the core principles of clean code and why they matter in real-world development.

## Tasks
- [x] Research and summarize the following clean code principles in clean_code.md:
  - Simplicity – Keep code as simple as possible.
  - Readability – Code should be easy to understand.
  - Maintainability – Future developers (including you!) should be able to work with the code easily.
  - Consistency – Follow style guides and project conventions.
  - Efficiency – Write performant, optimized code without premature over-engineering.
  
  **🧼 Clean Code Principles**
  Clean code is code that is easy to read, understand, and maintain. It minimizes cognitive load and helps developers write better software over time. Below are key principles of clean code, supported by well-known industry references.

  1. **Simplicity**
    Code should be as simple as possible—no more, no less. It should do what it needs to do and nothing more.
    
    Simple code is easier to test, debug, and refactor.

    *"The art of programming is the art of organizing complexity, of mastering multitude and avoiding its bastard chaos as effectively as possible."*
    — Edsger W. Dijkstra

    Best practice: Avoid cleverness or premature abstraction; prioritize clarity over ingenuity.

  2. **Readability**
    Code should be written for humans first, and machines second.
    
    Readable code reduces onboarding time and makes collaboration smoother.

    *"Code is read much more often than it is written."*
    — Robert C. Martin, Clean Code

    Best practice: Use descriptive naming, consistent formatting, and clear logic.

  3. **Maintainability**
    Code should be easy to change, extend, or refactor without breaking existing functionality.
    
    Most of the cost in software comes after the initial development. Maintainable code keeps long-term costs low.

    *"Clean code always looks like it was written by someone who cares."*
    — Robert C. Martin

    Best practice: Write modular code with minimal dependencies and clear boundaries.

  4. **COnsistency**
    Code should follow a uniform style across the entire project.
    
    Consistency allows developers to predict how code is structured, which speeds up understanding.

    *"A foolish consistency is the hobgoblin of little minds…"*
    — Ralph Waldo Emerson (often quoted in programming style guides)

    Best practice: Use linting tools, code formatters, and follow agreed-upon conventions (e.g., PEP 8 for Python).

  5. **Efficiency**
    Code should be performant and make good use of resources, but not at the cost of readability.
    
    Efficient code scales better and can reduce infrastructure costs.

    *"Premature optimization is the root of all evil."*
    — Donald Knuth

    Best practice: Write correct and clean code first, then profile and optimize only when needed.

  Sources:
Robert C. Martin, Clean Code: A Handbook of Agile Software Craftsmanship, 2008

Steve McConnell, Code Complete, 2nd Edition, 2004

[PEP 8 – Python Enhancement Proposal](https://peps.python.org/pep-0008/)

- [x] Find an example of messy code online (or write one yourself) and describe why it's difficult to read.
```js
function f(n){if(n==0){return 1;}else{return n*f(n-1);}}

// Example usage:
console.log(f(5)); // Should print 120
```
Issues:
- Lack of Descriptive Naming: The function name f doesn't convey its purpose.
- Poor Formatting: The entire function is written on a single line, making it hard to read.
- Inconsistent Spacing: There's no space around operators and after commas, which hampers readability.
- No Input Validation: The function doesn't handle negative inputs or non-integer values.

- [x] Rewrite the code in a cleaner, more structured way.
```js
/**
 * Calculates the factorial of a non-negative integer.
 * @param {number} number - A non-negative integer.
 * @returns {number} - The factorial of the input number.
 * @throws {Error} - If the input is not a non-negative integer.
 */
function calculateFactorial(number) {
  if (!Number.isInteger(number) || number < 0) {
    throw new Error('Input must be a non-negative integer.');
  }

  if (number === 0) {
    return 1;
  }

  return number * calculateFactorial(number - 1);
}

// Example usage:
console.log(calculateFactorial(5)); // Output: 120
```
Improvements:
- Descriptive Naming: Renamed the function to calculateFactorial to clearly indicate its purpose.
- Proper Formatting: Structured the code with appropriate indentation and spacing for better readability.
- Input Validation: Added checks to ensure the input is a non-negative integer, throwing an error otherwise.
- Documentation: Included a JSDoc comment to explain the function's purpose, parameters, return value, and potential errors.

- [x] Commit and push your changes to GitHub.
___________________________________________________________

## Code Formatting & Style Guides
### Goal
Understand the importance of code formatting and how to use tools like linters to enforce consistency.

## Tasks
- [x] Research the importance of consistent code style.
Consistent code style improves collaboration, readability, and maintainability. When everyone follows the same conventions, developers can:
  - Quickly understand each other's code
  - Avoid style-based merge conflicts in version control
  - Catch bugs early with static analysis tools
  - Focus on solving problems rather than debating formatting

Using automated tools like ESLint and Prettier ensures style consistency across a project, regardless of who’s writing the code.

- [x] Review the Airbnb javascript style guide.
The Airbnb JavaScript Style Guide is one of the most widely adopted JavaScript style guides. It provides opinionated rules and best practices. Some key takeaways include:
  - Use `const` and `let` instead of var
  - Prefer arrow functions (`const add = (a, b) => a + b`)
  - Always use semicolons
  - Use triple equals (`===`) for comparisons
  - Use single quotes for strings ('hello' instead of "hello")
  - Use object and array shorthand when possible
  - Avoid unnecessary nesting
  - Handle errors explicitly using `try/catch`

- [x] Install and configure ESLint and Prettier in your development environment.
  Step 1: Initialize the project with `npm init -y`

  STep 2: Install both tools and their recommended configs:
  ```bash
  npm install --save-dev eslint prettier eslint-config-prettier eslint-plugin-prettier
  ```
  `eslint`: Finds and reports on problems in your code.

  `prettier`: Formats your code.

  `eslint-config-prettier`: Turns off ESLint rules that conflict with Prettier.

  `eslint-plugin-prettier`: Runs Prettier as an ESLint rule.

  Step 3: Run the ESLint initialization wizard to configure ESLint:
  ```bash
  npx eslint --init
  ```
  The system will prompt some questions like:
  ```bash
  √ What do you want to lint? · javascript
  √ How would you like to use ESLint? · problems
  √ What type of modules does your project use? · esm
  √ Which framework does your project use? · none
  √ Does your project use TypeScript? · no / yes
  √ Where does your code run? · browser
  The config that you've selected requires the following dependencies:

  eslint, @eslint/js, globals, eslint-plugin-react
  √ Would you like to install them now? · No / Yes
  √ Which package manager do you want to use? · npm
  ☕️Installing...
  ```
  This creates a .eslintrc config file.
  
  If not, create a .eslintrc.json file manually:
  ```json
  {
    "extends": ["prettier"],
    "plugins": ["prettier"],
    "rules": {
      "prettier/prettier": "error"
    }
  }
  ```

  Step 4: Add a Prettier Config by creating a .prettierrc file
  ```json
  {
    "semi": true,
    "singleQuote": true,
    "tabWidth": 2,
    "printWidth": 80,
    "trailingComma": "es5"
  }
  ```

  Step 5: Add Scripts to package.json
  ```json
  "scripts": {
    "lint": "eslint .",
    "format": "prettier --write ."
  }
  ```

- [x] Run the formatter and linter on your codebase and fix any issues.
  - Run ESLint using `npm run lint`.
  - Fix errors manually or with: `npx eslint . --fix`
  - Run Prettier `npm run format`
  
  After running the following command, I investigated that some code files have changed their structure.
  From:
  ```js
  function f(n){if(n==0){return 1;}else{return n*f(n-1);}}

  // Example usage:
  console.log(f(5)); // Should print 120
  ```
  To:
  ```js
  function f(n) {
  if (n == 0) {
      return 1;
    } else {
      return n * f(n - 1);
    }
  }

  // Example usage:
  console.log(f(5)); // Should print 120
  ```


- [x] Write reflections in clean_code.md:
  - Why is code formatting important?
    Consistent code formatting makes a codebase easier to read, navigate, and maintain. It reduces misunderstandings, minimizes merge conflicts in teams, and promotes shared ownership of the code. Well-formatted code is also easier to debug and refactor because structure and logic are visually clear.

    *"Style is not a matter of taste. It's a matter of making your code easier to read, understand, and change."*
    — Airbnb JavaScript Style Guide

  - What issues did the linter detect?
    While using ESLint, the linter detected several common code issues:
    - Missing semicolons: Some statements weren’t properly terminated.
    - Inconsistent spacing: There were extra or missing spaces around operators and keywords.
    - Unused variables: Some variables were declared but never used.
    - No newline at end of file: ESLint flagged missing final newlines as a style issue.
    - Incorrect indentation: Blocks of code were not indented consistently.

    These errors don’t necessarily break the code, but they make it harder to read, maintain, or debug.

  - Did formatting the code make it easier to read?
    Yes. Running Prettier and fixing linting issues dramatically improved readability. The code now has:
    - Clear, consistent spacing
    - Logical line breaks
    - Uniform indentation
    - Better organization overall

    It’s easier to scan visually, especially when switching between files or returning to the project after a break. The formatter also helped ensure that all team members would produce code that "looks the same."

- [x] Commit and push your changes to GitHub.
