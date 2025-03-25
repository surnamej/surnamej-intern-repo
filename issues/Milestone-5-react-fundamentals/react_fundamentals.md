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
___________________________________________________________________________________________________________________

## Understanding Components & Props
### Goal
Learn the core building blocks of React.

## Tasks

- [x] Create a functional component called HelloWorld.js that displays "Hello, Focus Bear!"
- [x] Pass a prop called name to the component and display it dynamically.
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