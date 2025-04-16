# Milestone: Debugging

## Practise React Debugging in a Test Repo
### Goal
Apply debugging techniques to a real React codebase and learn through hands-on practice.

## Tasks
- [x] Read the article ["Three Buggy React Code Examples And How To Fix Them"](https://css-tricks.com/three-buggy-react-code-examples-and-how-to-fix-them/).
- [x] Recreate at least one of the buggy examples in your own React project. (in Buggy.jsx)
-----------------------------------------------------------
#### Buggy: Stale State in useEffect
Scenario: There’s a "Save" button that should auto-save a message after a delay. But after updating the message, it still saves the old one.
```jsx
import { useEffect, useState } from "react";
import { Link } from "react-router-dom";

function AutoSaveMessage() {
  const [message, setMessage] = useState("");
  const [savedMessage, setSavedMessage] = useState("");

  useEffect(() => {
    const timeout = setTimeout(() => {
      setSavedMessage(message);
    }, 2000);

    return () => clearTimeout(timeout);
  }, []);

  return (
    <div className="flex flex-col items-center justify-center min-h-screen p-4 bg-gray-100">
      <textarea
        value={message}
        onChange={(e) => setMessage(e.target.value)}
        placeholder="Type something..."
      />
      <p><strong>Saved message:</strong> {savedMessage}</p>
      <Link to="/" className="bg-blue-500 text-white px-4 py-2 rounded">
        Go to Home
      </Link>
    </div>
  );
}

export default AutoSaveMessage;
```

- [x] Use debugging techniques to identify and fix the issues.

**Debugging Method**:
I likely used a combo of:
- UI observation — noticing that “Saved message” never updates.
- `console.log` in the effect or setSavedMessage to see what's actually being passed in.
  ```js
  console.log("Current message in effect:", message);
  ```

**Bug Summary**:
```jsx
useEffect(() => {
  const timeout = setTimeout(() => {
    setSavedMessage(message);
  }, 2000);
  return () => clearTimeout(timeout);
}, []);
```
I am using  an empty dependency array ([]) in useEffect, which means:
 - This effect runs only once on mount.
 - It captures the initial value of message, which is an empty string ("").
 - So the timeout always sets savedMessage to "", no matter what the user types afterward.

To fix it, I updated the effect like this:
```jsx
useEffect(() => {
  const timeout = setTimeout(() => {
    setSavedMessage(message);
  }, 2000);

  return () => clearTimeout(timeout);
}, [message]);
```
Adding message to the dependency array ensures that every time message changes:
- The effect re-runs.
- A new timeout is created with the latest value of message.
- `setSavedMessage(message)` reflects the correct message after 2 seconds.

- [x] Document the process in debugging_practice.md:
  - What was the issue?
    The `AutoSaveMessage` component was supposed to "auto-save" the latest user input from a textarea after a 2-second delay. However, it always saved the initial empty string, even after typing new input.

  - What debugging method did you use?
    I observed that the "Saved message" display never updated after typing. I added a `console.log(message)` inside the `setTimeout` function to see what value was being captured. It turned out the `useEffect` closure was capturing the initial value of `message`, due to an empty dependency array.

  - How did you resolve the problem?
    To ensure the effect always had access to the latest `message` state, I added `message` to the `useEffect` dependency array. This allows the timeout to update correctly every time the user types something new.

- [x] Commit and push your changes to GitHub.