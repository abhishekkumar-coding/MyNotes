### 🧠 1. useState
Used for managing local state in functional components.

```
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';

export default function Counter() {
  const [count, setCount] = useState(0);
  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increment" onPress={() => setCount(count + 1)} />
    </View>
  );
}
```

### 🧠 2. useEffect
Runs side effects like data fetching, timers, or subscriptions.

```
import React, { useEffect, useState } from 'react';
import { Text } from 'react-native';

export default function Example() {
  const [data, setData] = useState(null);

  useEffect(() => {
    // Fetch data on mount
    fetch('https://jsonplaceholder.typicode.com/posts/1')
      .then(res => res.json())
      .then(json => setData(json));
  }, []);

  return <Text>{data?.title}</Text>;
}
```

### 🧠 3. useRef
useRef() is a React hook that gives you a mutable object which:
- persists across renders, 
- doesn't trigger a re-render when updated.
1. Accessing DOM or Component Elements
In React Native, this is typically used to focus a TextInput, scroll a list, etc.
2. Storing Mutable Values Without Re-render
Sometimes you want to track values (like timers, previous state, counters) without causing re-renders.
3. Preserve Previous State Value

```
function Timer() {
  const intervalRef = React.useRef(null);

  useEffect(() => {
    intervalRef.current = setInterval(() => {
      console.log("Tick");
    }, 1000);
    return () => clearInterval(intervalRef.current);
  }, []);

  return <Text>Check your console</Text>;
}
```
### 4. useReducer
An alternative to useState, useful for complex state logic.

```
function reducer(state, action) {
  switch (action.type) {
    case 'increment': return { count: state.count + 1 };
    case 'decrement': return { count: state.count - 1 };
    default: return state;
  }
}

function Counter() {
  const [state, dispatch] = React.useReducer(reducer, { count: 0 });

  return (
    <View>
      <Text>Count: {state.count}</Text>
      <Button title="+" onPress={() => dispatch({ type: 'increment' })} />
      <Button title="-" onPress={() => dispatch({ type: 'decrement' })} />
    </View>
  );
}
```

### 5. useCallback
Memoizes a function to prevent re-creating it unless dependencies change.

```
function Example({ onAction }) {
  const handleClick = React.useCallback(() => {
    onAction("clicked");
  }, [onAction]);

  return <Button title="Click" onPress={handleClick} />;
}
```

### 6. useMemo
Memoizes a computed value to avoid expensive recalculations.

```
const expensiveCalculation = (num) => {
  console.log("Calculating...");
  return num * 2;
};

function Example({ number }) {
  const result = React.useMemo(() => expensiveCalculation(number), [number]);
  return <Text>Result: {result}</Text>;
}
```

### 7.useContext
Access data from React Context.

```
const ThemeContext = React.createContext();

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Child />
    </ThemeContext.Provider>
  );
}

function Child() {
  const theme = React.useContext(ThemeContext);
  return <Text>Theme is {theme}</Text>;
}
```
