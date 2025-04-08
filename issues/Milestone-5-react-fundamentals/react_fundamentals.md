# Milestone: React Fundamentals
## Setting up a React project environment

## Tasks
- [x] **Set up a React project with Tailwind CSS.**
Project:[react-tailwind-demo](https://github.com/surnamej/react-tailwind-demo)
- [x] **Run the project and ensure Tailwind is working.**
- [x] **Push a README.md file explaining how you set up the environment.**
[react-tailwind-demo/README.md](https://github.com/surnamej/react-tailwind-demo/blob/main/README.md)

- [x] **Reflection (in react_fundamentals.md)**:
  - What challenges did you face during setup?
    Setting up this project on Windows was a great learning experience. I built a React app using Vite and integrated Tailwind CSS v4, and I encountered a few challenges along the way.

    **Adapting to Tailwind v4 Changes:**  
    With Tailwind CSS v4, the old initialisation command (`npx tailwindcss init -p`) is no longer required. Instead, I simply added Tailwind’s directives directly into my CSS file. This new approach simplified the setup but also meant I had to update my workflow and understand the zero-config concept.

    **Using JSX:**  
    I chose to use JSX because it allows me to write HTML-like code directly within JavaScript. This results in more readable and maintainable code when building user interfaces. JSX simplifies component creation by letting me seamlessly integrate UI markup with JavaScript logic. Although files containing JSX are commonly named with a .jsx extension, I’ve kept the assignment requirement to use a .js file when needed.

    **Ensuring Proper File Imports:**  
    It was crucial to verify that the CSS file containing Tailwind’s directives was correctly imported in the React entry file (`main.jsx`). This step ensured that all Tailwind styles were applied properly. I double-checked my file paths and import statements, which paid off when I saw the live preview with the expected design.

    **Overall Experience and Lessons Learned:**  
    This setup process reinforced the importance of reading the latest documentation and adapting to changes in tools and frameworks. It also highlighted the need to understand the nuances of the operating system you’re working on. Overall, the experience improved my skills in managing modern development environments and gave me more confidence working with React and Tailwind CSS on Windows.

    In summary, while there were minor challenges, the project setup was a valuable opportunity to enhance my technical knowledge and problem-solving skills.
______________________________________

## Understanding Components & Props
### Goal
Learn the core building blocks of React.

## Tasks

- [x] Create a functional component called HelloWorld.js that displays "Hello, Focus Bear!"
- [x] Pass a prop called name to the component and display it dynamically.
``` JavaScript XML
import React from 'react';

function HelloWorld({ name }) {
  return (
    <div className="flex flex-col items-center p-4">
      <h1>Hello, {name}!</h1>
    </div>
  );
}

export default HelloWorld;
```
- [x] Push this component to GitHub.
[Project-demo](https://github.com/surnamej/react-tailwind-vite-demo)

- [x] Reflection (in react_fundamentals.md):
  - Why are components important in React?
  Components are the core building blocks in React. They enable developers to break the user interface into small, independent, and reusable pieces. This modularity offers several advantages:

    - **Reusability:** Once a component is built, it can be reused across different parts of the application.
    - **Maintainability:** Smaller, focused components are easier to debug, update, and test.
    - **Encapsulation:** Components manage their own state and behavior, reducing complexity in the overall application.
    - **Clarity:** By splitting the UI into self-contained components, the overall structure of the application becomes clearer and more manageable.

    Overall, components allow for better organisation and scalability of applications, making development more efficient.
______________________________________
## Handling State & User Input
### Goal
Learn how to manage state using useState.

### Tasks

- [x] Create a component Counter.js with a button that increments a number when clicked.
- [x] Use useState to manage the count value.
- [x] Display the count value dynamically.
```Javascript XML (jsx)
import React, { useState } from 'react';

function Counter() {
  // Initialise count state with a default value of 0
  const [count, setCount] = useState(0);

  // Function to handle the increment
  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div className="p-4">
      <p className="text-xl mb-2">Count: {count}</p>
      <button 
        onClick={increment} 
        className="bg-blue-500 text-white py-2 px-4 rounded"
      >
        Increment
      </button>
    </div>
  );
}

export default Counter;
```
- [x] Push this component to GitHub.

- [x] Reflection (in react_fundamentals.md):
  - What happens if we modify state directly instead of using setState?
  When I modify state directly, I bypass React’s built-in update system. This can cause a few issues:
    - **No UI Update**: React won’t notice the change, so my UI might not refresh.
    - **Unexpected Bugs**: Changing state directly can lead to unpredictable behavior.
    - **Performance Problems**: I lose React’s optimisations that come from treating state as immutable.

  Always use `setState` (in class components) or the updater function from `useState` (in functional components) to ensure React correctly tracks and updates your UI.
______________________________________

## Styling with Tailwind CSS
### Goal
Learn to style React components using Tailwind CSS.

## Tasks

- [x] Convert Counter.js to use Tailwind CSS classes instead of regular CSS.
- [x] Create a Button component with Tailwind styling.
Now update Counter.js to remove the previous regular CSS and use Tailwind CSS classes. You’ll also import and use the Button component from Button.jsx.
- [x] Add hover and active states using Tailwind utilities.
- [x] Push your styled components to GitHub.
``` JavaScript XML
// Button.jsx
import React from 'react';

const Button = ({ onClick, children, className = '' }) => {
  return (
    <button
      onClick={onClick}
      className={`px-4 py-2 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-300 active:bg-blue-800 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75 ${className}`}
    >
      {children}
    </button>
  );
};

export default Button;
```
``` JavaScript XML
// Counter.jsx
import React, {useState} from "react";
import Button from './style_components/Button';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div className="flex flex-col items-center p-4">
      <h1 className="text-2xl font-bold mb-4">Counter: {count}</h1>
      <div className="space-x-2">
        <Button onClick={() => setCount(count - 1)}>Decrement</Button>
        <Button onClick={() => setCount(count + 1)}>Increment</Button>
      </div>
    </div>
  );
};

export default Counter;
```
- [x] Reflection:
  - What are the advantages of using Tailwind CSS?
    - **Utility-First Approach:**  
    Tailwind provides a rich set of utility classes that allow me to build designs directly in my markup without writing extensive custom CSS.
    - **Rapid Prototyping:**  
    With pre-built classes, I can quickly prototype and iterate on designs, speeding up development.
    - **Consistent Design:**  
    Using standardised classes helps maintain a consistent look and feel across my project.
    - **Responsive Design Made Easy:**  
    Tailwind includes responsive utilities that simplify adapting my UI for different screen sizes.
    - **Customisability:**  
    The configuration file in Tailwind allows me to easily customize themes, colors, spacing, and more to fit my design needs.
    - **Optimised Production Builds:**  
    In my onboarding, I've found that ensuring an optimised production CSS bundle is crucial. [PurgeCSS](https://purgecss.com/) (or Tailwind's built-in purge functionality) is to remove unused styles. PostCSS allows me to use JavaScript plugins to transform my CSS.

  - What are some potential pitfalls?
    - **Learning Curve:**  
    I found that transitioning to a utility-first methodology can be challenging, especially since I always use Bootstrap in my Academic projects. The abundance of utility classes in Tailwind can be overwhelming at first, given my familiarity with the pre-styled components and grid system that Bootstrap provides.

    - **Cluttered Markup:**
    My HTML/JSX can sometimes become hard to read because I have long lists of Tailwind utility classes in one place.

    - **Over-Reliance on Classes:**  
    There is a risk of overusing utility classes, which might lead to repetitive code and less semantic markup if I’m not careful with my approach.
    
    - **Customisation Complexity:**  
    While I enjoy the customisability, managing an extensive custom configuration can sometimes add complexity to my project.

    - **Dependency on Build Tools:**  
    To keep my Tailwind CSS bundle small, tools like PurgeCSS help me to remove unused styles. This extra step can make my project setup more complicated.
______________________________________

## Working with Lists & User Input
### Goal
Learn to handle lists dynamically in React.

## Tasks
- [x] Create a simple form with an input field and a button.
- [x] When the user enters text and clicks the button, add the text to a list.
- [x] Display the list dynamically using .map().
- [x] Push your form component to GitHub.
```JSX
import React, {useState} from "react";

const ListForm = () => { 
  const [inputValue, setInputValue] = useState("");
  const [items, setItems] = useState([]);

  const handleAddItem = (e) => {
    e.preventDefault();
    if(inputValue.trim()) {
      setItems([...items, inputValue]);
      setInputValue("");
    }
  };

  return ( 
    <div className="p-4">
      <form onSubmit={handleAddItem} className="mb-4">
        <input
          type="text" 
          className="border border-gray-300 p-2 mr-2 bg-white rounded"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
          placeholder="Enter an item"
        />
        <button type="submit" className="bg-blue-500 text-white p-2 rounded">
          Add Item
        </button>
      </form>
      <ul>
        {items.map((item, index) => (
          <li key={index} className="border-b border-gray-200 py-1">
            {item}
          </li>
        ))}
      </ul>
    </div>
  );
};

export default ListForm;
```

- [x] Reflection:
  - What are some common issues when working with lists in React?
    - **Missing Key Prop:**  
    I often run into issues when I forget to provide a unique key for each list item. This can cause rendering bugs and inefficient re-renders.

    ```JSX
    // Example: Missing key prop
    const ItemList = ({ items }) => {
      return (
        <ul>
          {items.map((item) => (
            <li>{item}</li> // No key prop provided
          ))}
        </ul>
      );
    };
    ```

    - **Using Index as Key:**  
    While it might be tempting to use the array index as a key, I've learned that it can lead to problems—especially when the list order changes. It may result in improper component re-use or state issues.

    - **State Mutation:**  
    I have encountered bugs when I accidentally mutate the state directly instead of creating a new copy of the list. This can lead to unexpected behavior during re-rendering.

    ```JSX
    // Incorrect: Directly mutating state
    const addItemIncorrectly = (newItem, items, setItems) => {
      items.push(newItem); // Mutating the state directly
      setItems(items);     // May not trigger a re-render
    };
    ```
    Solution
    ```JSX
    // Correct: Updating state immutably
    const addItemCorrectly = (newItem, items, setItems) => {
      setItems([...items, newItem]);
    };
    ```

    - **Performance Concerns:**  
    For larger lists, I need to be mindful of performance. Inefficient re-rendering can occur if I don't optimize how the list updates. In some cases, implementing lazy loading or virtualisation becomes necessary.
_______________________________________

## Navigation with React Router
### Goal
Learn how to navigate between pages in React using React Router.

## Tasks
- [x] Install React Router and set up a basic routing system.
```bash
npm install react-router-dom
```
- [x] Create two pages: Home.js and Profile.js.
- [x] Add navigation between the two pages (e.g., using Link or useNavigate).
- [x] Push your navigation setup to GitHub.

- [x] Reflection (in react_fundamentals.md):
  - What are the advantages of client-side routing?
    - **Faster Navigation:**  
    I appreciate how client-side routing enables smooth transitions between pages without the need for full page reloads, which makes my application feel more responsive.

    - **Improved Performance:**  
    By only updating the necessary components, I notice that my application renders changes much faster than with traditional server-side routing.

    - **Enhanced User Experience:**  
    Client-side routing allows me to implement transitions and animations that create a more engaging and interactive experience for my users.

    - **Reduced Server Load:**  
    Handling routing on the client side means fewer requests to the server, which can help lower the overall load and improve scalability.

    - **Seamless Interactivity:**  
    With client-side routing, I can build dynamic applications where users can interact with the app in real time without interruption.
