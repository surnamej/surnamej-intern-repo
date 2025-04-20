# Milestone: Set Up Tools

## Set Up AI Tools for Development

### Tasks

### Research and install an AI coding assistant (choose one or more)

GitHub Copilot and ChatGPT are excellent AI coding assistants, but they serve slightly different purposes:

- GitHub Copilot: Best for real-time code completion inside VS Code, JetBrains IDEs, or Neovim. It suggests code snippets, functions, and even entire implementations based on comments and existing code.
- ChatGPT: Best for explaining code, debugging, and problem-solving. It allows more in-depth discussions, code reviews, and conceptual help.

### Experiment with using AI for development

#### Generate code snippets and analyze how useful they are

``` JavaScript
// Function to check if a string is a palindrome
function isPalindrome(str) {
    const reversed = str.split("").reverse().join("");
    return str === reversed;
}

// Example usage
console.log(isPalindrome("racecar")); // Output: true
console.log(isPalindrome("hello"));   // Output: false
```

- AI-generated snippets are great for quickly solving common problems.
- They often provide a good starting point but may require refinement for edge cases or specific requirements.

#### Use AI for debugging a simple problem

``` JavaScript
// Function to reverse a string
function reverseString(str) {
    return str.split("").reverse().join;
}

// Example usage
console.log(reverseString("hello")); // Expected output: "olleh"
```

**Debugging with AI**

1. Problem Identification:
   - The .join method is missing parentheses, so it’s not being called as a function.
2. AI-Suggested Fix:

``` JavaScript
function reverseString(str) {
    return str.split("").reverse().join("");
}
```

3. Testing the Fix:

``` JavaScript
console.log(reverseString("hello")); // Output: "olleh"
console.log(reverseString("world")); // Output: "dlrow"
```

#### Ask AI for explanations on a new concept you're learning

**Question to AI:**
"What is TypeScript, and how is it different from JavaScript?"

**AI Explanation:**
TypeScript is a strongly typed superset of JavaScript that compiles to plain JavaScript. It adds optional static typing, interfaces, and other features to help developers write more robust and maintainable code.

**Key differences between TypeScript and JavaScript:**

1. Static Typing: TypeScript allows you to define types for variables, function parameters, and return values, which helps catch errors during development.

``` typescript
let age: number = 25; // TypeScript
let age = 25; // JavaScript
```

2. Interfaces: TypeScript supports interfaces to define the structure of objects.

```typescript
interface User {
    name: string;
    age: number;
}
let user: User = { name: "Alice", age: 30 };
```

3. Compilation: TypeScript code needs to be compiled into JavaScript before it can run in the browser or Node.js.

### Document your experience in ai_tools.md

#### Which AI tools did you try?

I always use ChatGPT, so I choose to explore GitHuB Copilot in this task.

#### What worked well? What didn’t?

GitHub Copilot worked well for generating code snippets and providing suggestions for common coding patterns. It was particularly helpful in reducing the time spent on boilerplate code and catching minor syntax errors. However, it sometimes suggested solutions that were not contextually relevant or overly complex for simple problems.

#### When do you think AI is most useful for coding?

I think AI is highly effective for catching syntax errors, suggesting fixes for common mistakes, and explaining why a piece of code isn’t working.
