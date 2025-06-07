# 📘 Core Components vs Custom Components in React Native

React Native provides a powerful set of built-in components and the ability to create your own. Understanding the difference between **core** and **custom** components is essential for scalable app development.

---

## 🧱 Core Components

These are built-in components provided by React Native. They are essential building blocks for any React Native app.

### ✅ Common Core Components:

| Component         | Purpose |
|------------------|---------|
| `View`            | Container for layout, like `<div>` in HTML. |
| `Text`            | Renders text on the screen. |
| `Image`           | Displays images from local or remote sources. |
| `ScrollView`      | Creates a scrollable container. |
| `FlatList`        | Efficient way to render lists. |
| `TextInput`       | Allows user input (e.g., forms). |
| `Button`          | Simple clickable button. |
| `TouchableOpacity`| Makes any component touchable with fade effect. |
| `Pressable`       | Advanced press event handler. |
| `Modal`           | Displays content over current view. |
| `ActivityIndicator`| Shows loading spinner. |
| `SafeAreaView`    | Prevents overlap with system UI like notches. |
| `KeyboardAvoidingView` | Adjusts view when keyboard appears. |
| `StatusBar`       | Customize status bar appearance. |

> 📌 These components are available out of the box and require no extra installation.

---

## 🛠️ Custom Components

Custom components are user-defined components created by combining core components into reusable UI blocks or functional units.

### 🧩 Examples of Custom Components:

```js
// ButtonCard.js
import React from 'react';
import { TouchableOpacity, Text, StyleSheet } from 'react-native';

const ButtonCard = ({ label, onPress }) => (
  <TouchableOpacity onPress={onPress} style={styles.button}>
    <Text style={styles.text}>{label}</Text>
  </TouchableOpacity>
);

const styles = StyleSheet.create({
  button: {
    backgroundColor: '#1e90ff',
    padding: 12,
    borderRadius: 10,
    alignItems: 'center',
  },
  text: {
    color: 'white',
    fontWeight: 'bold',
  },
});

export default ButtonCard;
```
## What is `View`?

In **React Native**, the `View` component is one of the **core building blocks** used to design the layout of the user interface (UI). It works similarly to a `<div>` in HTML and acts as a **container** for other components like `Text`, `Image`, `ScrollView`, etc.

---

## 🧠 Purpose of `View`:

- To **group** components together
- To **structure layouts** using Flexbox
- To apply **styling** such as padding, margin, background color, borders, etc.
- To build **nested and reusable layout structures**

---

## 🛠 Example:

```jsx
import React from 'react';
import { View, Text } from 'react-native';

export default function App() {
  return (
    <View style={{ padding: 20, backgroundColor: '#f2f2f2' }}>
      <Text>Hello from inside a View!</Text>
    </View>
  );
}
```
# 📱 Useful Components in React Native

React Native offers a set of built-in components that help you build mobile applications efficiently. Below is a list of some of the **most useful components** with their purposes.

---

## 1. **View**
- The most fundamental component for layout and styling.
- Acts as a container for other components (similar to `<div>` in HTML).

## 2. **Text**
- Used to display text in the app.
- Supports styling, nesting, and touch events.

## 3. **Image**
- Displays images using URI or static assets.
- Supports resizing, borders, and overlays.

## 4. **ScrollView**
- Provides a scrollable container for content.
- Good for small lists or vertical scrolling content.

## 5. **FlatList**
- Optimized for rendering large lists of data.
- Efficient with recycling views and only rendering visible items.

## 6. **SectionList**
- Similar to `FlatList` but with support for sections with headers.

## 7. **TouchableOpacity**
- Makes any component tappable with a fade-in/out opacity effect on press.
- Ideal for buttons or clickable items.

## 8. **TouchableHighlight**
- Similar to `TouchableOpacity`, but provides a color highlight when pressed.

## 9. **Pressable**
- A newer and more powerful touch responder component.
- Allows fine-grained control over press states.
- !IMPORTANT

## 10. **TextInput**
- Used to accept user input (text, email, password, etc.).
- Supports focus, placeholder, keyboard types, and validation.

## 11. **Modal**
- Displays content in an overlay layer on top of the current screen.
- Useful for dialogs, pop-ups, or forms.

## 12. **ActivityIndicator**
- Shows a loading spinner to indicate background processing.
- Commonly used during data fetch or form submission.

## 13. **SafeAreaView**
- Ensures your content doesn’t overlap with notches or the status bar.
- Recommended for iOS devices with screen cutouts.
- !IMPORTANT

## 14. **KeyboardAvoidingView**
- Adjusts layout when the keyboard appears so that input fields aren’t hidden.
- Crucial for building user-friendly forms.

## 15. **StatusBar**
- Allows you to configure the status bar appearance (background color, style).

## 16. **Switch**
- A toggle switch component (like an on/off slider).
- Often used in settings screens.

## 17. **Button**
- A simple built-in button component.
- Can be customized via styles or replaced with a custom `TouchableOpacity`.

## 18. **CheckBox**
- A checkbox component for selecting multiple options.
- Useful in forms and settings screens.

## 19. **Picker**
- A dropdown component for selecting from a list of options.
- Commonly used in forms and settings screens.

## 20. **Slider**
- A component for selecting a value from a range.
- Often used in settings screens for adjusting volume, brightness, etc.

## 21. **useColorScheme**
- A hook to access the user's preferred color scheme (light/dark mode).
- Useful for theming and adaptive UI design.

## 22. **useWindowDimensions**
- A hook to access the current window dimensions (width, height).
- Useful for responsive design and layout adjustments.

## 23. **useEffect**
- A hook for managing side effects in functional components.
- Useful for data fetching, subscriptions, and manual DOM updates.



---

## 💡 Bonus (Third-Party UI Libraries):
- **React Native Paper**: Material Design components.
- **React Native Elements**: Customizable cross-platform UI toolkit.
- **NativeBase**: UI toolkit with accessibility and theme support.
- **Lottie**: For animated illustrations.

---

## 🧠 Tips:
- Use `FlatList` over `ScrollView` for long lists.
- Use `KeyboardAvoidingView` with `TextInput` for better UX.
- Prefer `Pressable` for advanced touch interaction logic.

