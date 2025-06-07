### JavaScript ES6 Features

## 1. `let` and `const`
- `let`: Block-scoped variable.
- `const`: Block-scoped constant (cannot be reassigned).

## 2. Arrow Functions
- Concise syntax for writing functions.
- Lexically bind `this` to the enclosing context.

## 3. Template Literals
- Embed expressions within strings using backticks (`).
- Example: `const name = "John"; const greeting = `Hello, ${name}!`;`

## 4. Destructuring
- Extract values from arrays and objects into distinct variables.
- Example: `const [a, b] = [1, 2]; const { name } = { name: "John", age: 25 };`

## 5. Spread Operator
- Spread elements of an array or object into another array or object.
- Example: `const arr1 = [1, 2, 3]; const arr2 = [...arr1, 4, 5];`

## 6. Default Parameters
- Provide default values for function parameters.
- Example: `function greet(name = "Guest") { return `Hello, ${name}!`; }`

## 7. Classes
- Define blueprints for creating objects with methods and properties.
- Example:
```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    return `Hello, ${this.name}!`;
  }
}
const person = new Person("John");
```

## 8. Modules
- Import and export functions, variables, and classes between files.
- Example: `export function greet(name) { return `Hello, ${name}!`; }` in one file, and `import { greet } from "./greet";` in another.

## 9. Promises
- Handle asynchronous operations in a more organized way.
- Example:
```js
const promise = new Promise((resolve, reject) => {
  // Asynchronous task
  if (success) {
    resolve("Success!");
  } else {
    reject("Error!");
  }
});
promise.then(result => console.log(result)).catch(error => console.error(error));
```

## 10. Async/Await
- Write asynchronous code in a synchronous style.
- Example:
```js
async function fetchData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error(error);
  }
}
fetchData();
```

### 11. Enhanced Object Literals
- Concise syntax for defining object literals.
- Example:
```js
const name = "John";
const age = 25;
const person = { name, age, greet() { return `Hello, ${this.name}!`; } };
```




###  What is React Native?
React Native is a JavaScript framework for building native mobile applications using React. It allows developers to use their existing JavaScript and React knowledge to build mobile apps for both iOS and Android platforms.

### What are the key features of React Native?

React Native is a popular open-source framework developed by Facebook for building mobile applications using JavaScript and React. Its key features include:

1. **Cross-Platform Development**  
   - Write once, run on both iOS and Android platforms using a single codebase.

2. **Native Components**  
   - Uses native components under the hood, which provides near-native performance and look-and-feel.

3. **Hot Reloading / Fast Refresh**  
   - Instantly see changes in the code without recompiling the entire app, improving development speed.

4. **JavaScript & React**  
   - Leverages the power of React and JavaScript to build UI and manage application logic.

5. **Strong Community Support**  
   - Backed by a large community, offering a wide range of third-party libraries and tools.

6. **Modular Architecture**  
   - Encourages separation of concerns and reusable components.

7. **Access to Native APIs**  
   - Allows integration with native modules using Java, Swift, or Objective-C when needed.

8. **Third-Party Plugin Compatibility**  
   - Supports a variety of third-party plugins and native module linking to extend functionality.

9. **Live Reload**  
   - Automatically reloads the app when the code changes, making testing and debugging easier.

10. **Large Ecosystem & Tools**  
    - Compatible with popular tools like Redux, TypeScript, Expo, and more.

React Native significantly reduces development time and cost while enabling a consistent user experience across platforms.


# React Lifecycle Methods

React components go through a lifecycle of phases: **Mounting**, **Updating**, and **Unmounting**. These lifecycle methods are available in **class components** and are useful for executing code at specific points in the component's existence.

---

## 🔹 1. Mounting Phase
Methods called when the component is being **inserted into the DOM**.

| Method | Description |
|--------|-------------|
| `constructor()` | Initializes the component's state and binds methods. |
| `static getDerivedStateFromProps(props, state)` | Syncs state with props before rendering. Rarely used. |
| `render()` | Returns the JSX to render on the screen. |
| `componentDidMount()` | Runs after the component has been rendered and mounted to the DOM. Used for API calls, timers, DOM manipulations. |

---

## 🔹 2. Updating Phase
Methods called when props or state are **updated/re-rendered**.

| Method | Description |
|--------|-------------|
| `static getDerivedStateFromProps(props, state)` | Same as mounting phase; called before every render. |
| `shouldComponentUpdate(nextProps, nextState)` | Determines if component should re-render. Used for performance optimization. |
| `render()` | Re-renders the component with updated props or state. |
| `getSnapshotBeforeUpdate(prevProps, prevState)` | Captures information (like scroll position) before DOM updates. |
| `componentDidUpdate(prevProps, prevState, snapshot)` | Called after component updates. Used for API updates, side effects. |

---

## 🔹 3. Unmounting Phase
Called when the component is **removed from the DOM**.

| Method | Description |
|--------|-------------|
| `componentWillUnmount()` | Cleanup tasks like removing event listeners, cancelling timers, etc. |

---

## 🔹 4. Error Handling Phase (New in React 16+)
Called when an error is thrown in any lifecycle, render, or constructor.

| Method | Description |
|--------|-------------|
| `static getDerivedStateFromError(error)` | Renders a fallback UI when an error is caught. |
| `componentDidCatch(error, info)` | Logs error details (used in error boundaries). |

---

## 🔄 Lifecycle Diagram (Simplified)


# 🧵 Threads in React Native

React Native uses a **multi-threaded architecture** to efficiently manage UI rendering, JavaScript execution, and native operations. Understanding how these threads work helps optimize performance and avoid UI jank or slow interactions.

---

## 🔑 Key Threads in React Native

### 1. 🧠 JavaScript Thread
- Runs your **JavaScript code** (including React components, business logic, etc.).
- Responsible for handling state updates, API calls, touch events, etc.
- Single-threaded, so heavy JS work can block UI if not managed well.
- Runs in a **separate thread from the native UI**.

### 2. 🎨 UI (Main) Thread
- Handles **native UI rendering and user interactions**.
- Draws components on the screen, manages animations, and responds to gestures.
- If blocked, the app becomes unresponsive or lags.
- Same as the **main thread** in native iOS and Android apps.

### 3. 🔗 Shadow Thread (Layout)
- Used by React Native's layout system (Yoga) to calculate **layout** in the background.
- Communicates with the UI thread to apply layout changes.
- Offloads layout calculation from the UI thread to prevent blocking.

### 4. 📦 Native Modules Thread
- Executes **native module** code (e.g., camera, geolocation, etc.) outside of the JS and UI threads.
- Prevents slow native code from affecting UI responsiveness.

---

## 🔁 Communication Between Threads

React Native uses a **bridge** to send asynchronous, batched messages between:
- **JavaScript thread ⬌ Native thread**

### Example:
- JS calls `setState()` ➝ layout calculated on Shadow Thread ➝ UI updated on Main Thread.

---

## ⚠️ Common Performance Issues

| Issue | Cause |
|-------|-------|
| UI jank | Heavy JS operations blocking the JS thread |
| Slow UI updates | Delays in communication between threads |
| Input lag | Main/UI thread is overloaded |

---

## ✅ Optimizing Thread Usage

- Use `useMemo`, `useCallback` to optimize rendering
- Move heavy tasks off JS thread using libraries like:
  - `react-native-reanimated`
  - `react-native-threads`
  - `JSI` for direct native interaction
- Use `InteractionManager` to defer work until after interactions

---

## Summary

| Thread | Purpose |
|--------|---------|
| JavaScript Thread | Executes app logic, React code |
| UI/Main Thread | Renders UI and handles user input |
| Shadow Thread | Computes layout |
| Native Modules Thread | Runs native features (e.g., camera, location) |

Efficient use of threads in React Native ensures smooth and responsive user experiences.

# 📘 Pure Component vs Higher-Order Component in React Native

Understanding component design patterns like **PureComponent** and **Higher-Order Components (HOCs)** is key to writing optimized and reusable React Native code.

---

## ✅ 1. PureComponent

### 🔹 What is a PureComponent?

A `PureComponent` is a **React class component** that **automatically implements a shallow comparison** in `shouldComponentUpdate()`.  
It helps **prevent unnecessary re-renders** when the props or state haven’t changed.

### 🔧 Syntax:

```js
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    return <Text>{this.props.name}</Text>;
  }
}


# 📘 Higher-Order Component (HOC) in React / React Native

## 🔹 What is a Higher-Order Component?

A **Higher-Order Component (HOC)** is an advanced pattern in React that allows **code reuse** by wrapping one component with another.

### 🔁 Definition:

A Higher-Order Component is a **function** that:

- **Takes a component** as input
- **Returns a new component** with enhanced behavior

```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

## 🧾 Object vs StyleSheet in React Native
In React Native, styles can be defined using either **object literals** or **`StyleSheet.create`**. Each has its own use cases, advantages, and disadvantages.

## 🧾 Object Literal Styles
# ✅ Pros:
uick and simple for inline or dynamic styles.
Easy to use with conditional styling (based on state or props).

# 🚫 Cons:
No performance optimization (recreates style object on every render).
No support for media queries or pseudo-selectors.

## 📜 StyleSheet.create
# ✅ Pros:
Optimizes performance by creating a single style object.
Supports media queries and pseudo-selectors.
Easier to manage and debug styles.
Styles are pre-processed and cached, improving performance.
Provides error checking and validation.
Ideal for reusable and static styles.

# 🚫 Cons:
Less readable for inline or dynamic styles.
Can lead to prop drilling for dynamic styles.
Slightly more boilerplate.
