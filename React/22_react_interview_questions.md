📄 22_react_interview_questions.md - Common React Interview Questions & Answers


## Q: What is the difference between a functional component and a class component in React?

Functional Components:
Are written as plain JavaScript functions.
Use React Hooks (like useState, useEffect) for state and lifecycle features.
Are generally shorter, cleaner, and easier to test.
Are the modern standard in React.

Class Components:
Use ES6 class syntax.
Handle state with this.state and lifecycle methods like componentDidMount, componentDidUpdate.
Were the standard before Hooks came out in React 16.8.

## Q2:What is the purpose of the useEffect hook in React? When is it commonly used?

The useEffect hook lets you perform side effects in functional components.
Side effects include:
Fetching data from an API
Subscribing to events (like WebSocket or window resize)
Manually manipulating the DOM
Setting timers (like setInterval or setTimeout)
It runs after the component renders and can be controlled with a dependency array:
useEffect(() => { ... }, []) → runs once on mount
useEffect(() => { ... }, [count]) → runs when count changes
Also, you can return a cleanup function for things like removing event listeners or clearing intervals.

## What is the difference between props and state in React?

Props are used to pass data from parent to child.
State is used within a component to manage dynamic data.
Props are not global — they're scoped to the component they are passed into.
State is local to the component unless lifted or passed down.
You’re right that props are immutable (can’t be changed by the child).
State is mutable (can be updated using setState or useState).

## What is the virtual DOM in React and how does it improve performance?

The Virtual DOM is a lightweight JavaScript object that represents the actual DOM.
When state or props change, React:
Creates a new virtual DOM
Compares it with the previous version (using a diffing algorithm)
Calculates the minimum number of changes
Efficiently updates the real DOM — this process is called reconciliation

## What is the difference between useState and useEffect in React?

useState is a hook that lets you add state to functional components.
Example: const [count, setCount] = useState(0)

useEffect lets you perform side effects (like data fetching, timers, subscriptions, DOM updates) after render.
You can also clean up effects by returning a function from useEffect.

## Explain the React component lifecycle.

## React Component Lifecycle (Class Components)
React class components go through three main phases:
Mounting – When the component is being added to the DOM
constructor()
getDerivedStateFromProps()
render()
componentDidMount()

Updating – When the component is being re-rendered due to changes in props or state
getDerivedStateFromProps()
shouldComponentUpdate()
render()
getSnapshotBeforeUpdate()
componentDidUpdate()
Unmounting – When the component is removed from the DOM
componentWillUnmount()

## Lifecycle using Hooks (Functional Components)
In functional components, we use the useEffect hook to handle lifecycle behavior:

Lifecycle Phase	Hook Equivalent
componentDidMount	useEffect(() => { ... }, [])
componentDidUpdate	useEffect(() => { ... }, [deps])
componentWillUnmount	useEffect(() => { return () => {...} }, [])
So using useEffect, you can:
Run code on mount (empty dependency array [])
Run code on updates (with dependencies like [count])
Cleanup on unmount (returning a function inside useEffect)

## What is lifting state up in React? When and why would you use it?

Lifting state up means moving the state from a child component to a common parent component so that multiple child components can share and sync that state.

🧠 Example:
Let’s say you have two child components:
InputBox (user types something)
DisplayText (shows that text)

If both need access to the same data, instead of managing state in InputBox, you lift the state up to their parent (e.g. App) and pass it as props to both.

jsx
Copy
Edit
function App() {
  const [text, setText] = useState('');

  return (
    <>
      <InputBox onChange={setText} />
      <DisplayText text={text} />
    </>
  );
}
✅ Why Use It?
To avoid duplicate state in different components
To make data flow predictable and one-directional
To help sibling components communicate via the parent

🔁 You’ll often need this when:
Handling form inputs
Building filters/search bars
Making components talk to each other via shared data

## Why are keys used in React when rendering lists?

Keys help React identify which items have changed, been added, or removed in a list.
They provide a stable identity for each element in the list.
Without keys or with incorrect keys (like using index), React may re-render the entire list inefficiently or cause UI bugs (like losing focus or incorrect DOM updates).

##  What is conditional rendering in React?

Conditional rendering means displaying different UI based on a condition.
In React, you can use if, ? :, &&, or switch-case logic.

## What is React Context API and when to use it?

React Context API is used for global state management — to share data across components without passing props manually at every level.
Best for things like theme, language, user authentication, etc.

Steps:
Create a Context
Wrap your component tree with the Provider
Use useContext() in child components

## What is the purpose of React Router?

React Router enables navigation between pages in a single-page application (SPA) without refreshing the page.
It lets you define multiple routes with different components rendered based on the URL.

