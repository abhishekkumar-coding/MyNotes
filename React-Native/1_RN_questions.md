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
Quick and simple for inline or dynamic styles.
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

### Virtual Dom : 
THE VIRTUAL dom is a programming concept where an ideal or virtual representation is kept in memory and synced with real dom by a library such as ReactDom. This process is called reconcilation.

## 🧠 What is JSI (JavaScript Interface)?

JSI is a lightweight and fast system in React Native that allows JavaScript to directly call native code (like C++ or Java/Swift) without using the old Bridge.

✅ It helps in:
- Faster communication between JS and native
- Lower memory usage
- Better performance in apps

---

## ⚙️ What is Codegen?

Codegen is a tool in React Native that automatically generates the native code (Java/Swift/C++) from JavaScript or TypeScript interfaces.

✅ It helps in:
- Reducing manual native code
- Creating TurboModules and Fabric UI components
- Making JS-to-native communication type-safe and faster

---

🔥 Together, JSI + Codegen = High performance + Easier native module development in React Native.


### What is yoga ?
yoga is an open source cross plateform layout engine that that was developed by Facebook. It was designed to work with React Native and provides a flexible high-performance layout system that can be used to build complex responsive UIs. Yoga is based on the Flexbox layout model, which provides a simple and intuitive way to define the layout of a user interface.

### What is EVENR LOOP ?
The Event loop is a. machanesim that allows js to handle multiple tasks, such as rendering UI updates,handleing user inputs, and processing network request in a non-blocking way. It oprates in a singel thread envirnment but. can hanlde asynchronous operations efficiently by delegating tasks to other

### 1. What is React Native, and how is it different from React?
React Native is a JavaScript framework developed by Meta (Facebook) for building mobile applications for iOS and Android using React.
React (ReactJS) is used for building web applications using HTML and the DOM.
React Native uses native mobile components like View, Text, and Image instead of web elements like div, span, and img.
React Native apps are compiled into native code, offering better performance on mobile devices.

### 2. What are the core components of React Native?
Answer:
Key core components in React Native include:
View – The basic container for layout and styling, similar to a <div>.
Text – Used to render text on the screen.
Image – Displays images.
ScrollView – A container that supports scrolling.
TextInput – For user input fields.
TouchableOpacity / Pressable – Used for touchable/tap interactions.
FlatList / SectionList – For rendering scrollable lists.

### 3. How does React Native work under the hood?
Answer:
React Native uses a JavaScript bridge to connect JavaScript code to native platform APIs:
The JavaScript code runs in a separate thread using the JavaScript engine (e.g., Hermes or JavaScriptCore).
UI commands (like rendering a View or Text) are sent to the native side via a bridge.
The native platform renders the UI components and handles native gestures.
This allows React Native to provide a native look and feel with JavaScript logic.

### 4. How do you create a new React Native project?
Using React Native CLI:

** npx @react-native-community/cli init  **

### 5. What are some differences between View, Text, and ScrollView components?
Answer:
View: A basic container used to style and arrange elements. Similar to a <div> in web.
Text: Used only to display text. Must wrap any text content in React Native.
ScrollView: Used to display scrollable content. Suitable for small lists or vertical scrollable content. For large lists, use FlatList.

### 6. How does styling work in React Native?
Answer:
React Native uses JavaScript objects for styling instead of CSS.
You can use StyleSheet.create() or inline styles:

### 7. How is state managed in React Native?
Answer:
React Native uses the same state management approach as React:
Local state with useState() or this.setState() in class components.
For global state, libraries like Context API, Redux, Recoil, or Zustand can be used.

### 8. What is the difference between props and state?
Answer:

- props: Short for "properties". Passed from parent to child. Read-only.
- state: Maintained within the component. Can be changed using setState() or useState().

| Feature | Props            | State                  |
| ------- | ---------------- | ---------------------- |
| Source  | Parent component | Local to the component |
| Mutable | No               | Yes                    |
| Usage   | Configuration    | Dynamic data           |

### 9. How do you handle user input in React Native?
Answer:
Using TextInput and useState():

### ⚙️ 10. What is React Navigation? How do you implement Stack Navigation?
React Navigation is a popular library in React Native used for routing and navigating between different screens (pages) in a mobile app. It supports various types of navigators like Stack, Tab, Drawer, etc., and helps manage the app's navigation state.

### ⚙️ 11. What is the difference between Stack, Tab, and Drawer Navigation?

| Navigation Type       | Description                                                                                   | UI/Usage                                                               |
| --------------------- | --------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Stack Navigation**  | Navigates like a stack of cards (push/pop). Best for moving between screens in a linear flow. | Back button supported; like moving from login to dashboard to details. |
| **Tab Navigation**    | Shows multiple tabs at the bottom (or top) for switching between screens.                     | Ideal for apps with separate sections like Home, Profile, Settings.    |
| **Drawer Navigation** | Uses a sidebar drawer that slides in from the left/right.                                     | Great for adding menu or side options like Gmail or YouTube.           |

### ⚙️ 12. How do you pass parameters between screens in React Navigation?

# ✅ Passing parameters:
```
// Navigate to Details screen and pass a parameter
navigation.navigate('Details', { userId: 42 });

```
# ✅ Receiving parameters in the destination screen:
```
// DetailsScreen.js
import React from 'react';
import { View, Text } from 'react-native';

export default function DetailsScreen({ route }) {
  const { userId } = route.params;
  
  return (
    <View>
      <Text>User ID: {userId}</Text>
    </View>
  );
}
```
### 13. How can you write platform-specific code in React Native?
React Native allows you to write platform-specific code for Android and iOS using:

✅ File Name Extensions:
Use different files for different platforms:
MyComponent.ios.js
MyComponent.android.js
React Native will automatically load the correct file depending on the platform.

### 14. What is a Native Module? When would you use one?
A Native Module is a bridge between JavaScript code and native platform code (Java/Kotlin for Android and Objective-C/Swift for iOS).

✅ When to use a Native Module:
To access native device features not available in React Native APIs.
When you need high performance or want to reuse existing native SDKs.

 - Examples:
Accessing Bluetooth, file system, or background services
Integrating third-party native libraries
Performing heavy computation tasks

### 15. How can you access native device features (e.g., Camera, GPS, etc.) in React Native?
You can access native device features using community libraries or native modules:
| Feature            | Library                                                  |
| ------------------ | -------------------------------------------------------- |
| Camera             | `react-native-camera` or `expo-camera`                   |
| GPS/Location       | `@react-native-community/geolocation` or `expo-location` |
| Contacts           | `react-native-contacts`                                  |
| Sensors            | `react-native-sensors`                                   |
| Push Notifications | `react-native-push-notification`                         |

### 16. What is the use of useEffect in React Native?
The useEffect hook is used to run side effects in functional components. It replaces lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount in class components.

✅ Common use cases:
Fetching data from an API
Subscribing to events (e.g., device orientation)
Setting up timers or intervals
Cleaning up resources (like listeners)

### 17. How does the component lifecycle differ in class vs. functional components?
| Aspect       | Class Components                | Functional Components                      |
| ------------ | ------------------------------- | ------------------------------------------ |
| Mounting     | `componentDidMount()`           | `useEffect(() => {}, [])`                  |
| Updating     | `componentDidUpdate()`          | `useEffect(() => {}, [dependencies])`      |
| Unmounting   | `componentWillUnmount()`        | `useEffect(() => { return () => {} }, [])` |
| State        | `this.state`, `this.setState()` | `useState()`                               |
| Props access | `this.props`                    | function parameter                         |


### 18. What state management libraries have you used?
Common state management libraries in React Native include:
✅ Libraries I have used:
Redux – For managing global state using actions and reducers
Context API – For lightweight global state sharing
Zustand – A simple and minimal state management library
MobX (optional, if used) – For observable-based state management
Each library has its own use cases. For large apps with complex state, Redux is widely preferred.

### 19. What is React Native Reanimated, and how is it used?
React Native Reanimated is a library for creating high-performance, smooth animations in React Native.
It allows you to run animations on the UI thread, which improves performance and eliminates jank, especially on low-end devices.

✅ Use cases:
Gesture-based animations
Smooth transitions
Interactions using react-native-gesture-handler

### 20. What is Axios, and how is it different from fetch()?
✅ Axios:
A promise-based HTTP client for JavaScript.
Used to make HTTP requests from the browser or Node.js.
✅ Differences between Axios and fetch():

| Feature                       | `fetch()`                     | `axios`                         |
| ----------------------------- | ----------------------------- | ------------------------------- |
| Built-in                      | Yes                           | No (need to install)            |
| Response JSON parsing         | Manual (`res.json()`)         | Automatic                       |
| Request/Response Interceptors | No                            | Yes                             |
| Timeout support               | No (manual setup)             | Yes                             |
| Error handling                | Only throws on network errors | Throws on network + HTTP errors |

### 21. What are common debugging techniques in React Native?
Console Logs – Use console.log() for tracking variables and flow.
React Native Debugger – Standalone tool with Redux DevTools integration.
Flipper – Meta’s debugging tool to inspect UI, logs, network, and performance.
Chrome DevTools – Use Debug JS Remotely for JavaScript debugging in Chrome.
Breakpoints – Set breakpoints in Chrome or VS Code.
Error Boundaries – Catch runtime errors in UI components.

### 22. How do you test React Native applications?
There are three levels of testing:
Unit Testing – Test functions/components in isolation.
Integration Testing – Test interactions between components/services.
End-to-End Testing (E2E) – Test user behavior using tools like Detox.

### 23. How do you handle performance optimization in React Native?
Use FlatList for large lists instead of ScrollView.
 - Memoization:
React.memo to prevent unnecessary re-renders.
useCallback and useMemo for functions and values.
Lazy load images using libraries like react-native-fast-image.
Avoid anonymous functions in JSX.
Use native drivers in animations (e.g., useNativeDriver: true).
Minimize re-renders using shouldComponentUpdate or React.memo.

### 24. What is Metro bundler?
Metro is the JavaScript bundler used by React Native. It:
Transforms and bundles your JS code and assets.
Watches for file changes and updates in real-time.
Optimizes code in production builds.

### 25. What is CodePush, and how does it help in updating apps without going through app stores?
CodePush is a cloud service (by Microsoft) that allows you to push JavaScript code and asset updates directly to users without app store approval.

✅ Benefits:
No need to resubmit to Play Store or App Store.
Faster bug fixes and UI updates.
Works with React Native CodePush SDK.

✅ Usage:
Install the CodePush SDK.
Register your app on App Center.
Push updates using:

### 26. How does the React Native bridge work?
The React Native Bridge connects JavaScript (JS) and native code (Java for Android / Objective-C for iOS).

✅ How it works:
JS runs on its own thread.
Native modules run on a separate thread.
The bridge is asynchronous and communicates using JSON messages.
JS sends commands/data via the bridge to native modules and vice versa.

✅ Limitation:
The asynchronous bridge can cause performance issues during heavy interactions (e.g., animations), which led to the development of JSI (JavaScript Interface) and React Native Fabric for improved performance.

### 27. What are the performance differences between React Native and Flutter?
| Feature            | React Native                        | Flutter                                 |
| ------------------ | ----------------------------------- | --------------------------------------- |
| Language           | JavaScript                          | Dart                                    |
| Performance        | Slower UI performance due to bridge | Faster UI; no bridge (uses Skia engine) |
| Native Look & Feel | Uses native components              | Custom-rendered widgets                 |
| Ecosystem          | Mature, huge community              | Growing fast, smaller community         |
| Hot Reload         | Yes                                 | Yes (more stable)                       |

### 28. How would you implement offline support in a React Native app?
✅ Strategies:
Store data locally using:
AsyncStorage
react-native-mmkv
Realm or SQLite
Use a cache layer for API responses.
Queue actions (like updates) and sync when online.
Detect connection status using:
```
import NetInfo from '@react-native-community/netinfo';
NetInfo.fetch().then(state => {
  console.log("Connection type", state.type);
  console.log("Is connected?", state.isConnected);
});
```

### 29. What are the best practices for optimizing images and assets in React Native?
✅ Tips:
Use appropriate image sizes (don’t load 4K for thumbnails).
Use @2x, @3x suffixes for different screen densities.
Compress images using tools like TinyPNG or Squoosh.
Use SVGs for icons (with react-native-svg).
Lazy-load images using react-native-fast-image for caching and better performance.
Avoid inline base64 images (bad for memory).

### 30. How would you secure sensitive data (e.g., API keys, user data) in a React Native app?
| Goal                                 | Solution                                                           |
| ------------------------------------ | ------------------------------------------------------------------ |
| **Store API Keys**                   | Use `.env` + `react-native-config`, don’t hardcode in JS           |
| **User Data Storage**                | Use `react-native-keychain`, `SecureStore`, or encrypted storage   |
| **Secure APIs**                      | Use HTTPS, auth tokens (JWT, OAuth)                                |
| **Obfuscation**                      | Use JS minifiers + ProGuard (Android)                              |
| **Prevent Reverse Engineering**      | Use native obfuscation tools, avoid exposing secrets to the client |
| **Detect Rooted/Jailbroken Devices** | Use libraries like `react-native-root-check`                       |
