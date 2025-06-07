### What is FlatList?
**FlatList** is a performant and optimized React Native component used to render large lists of data. It only renders items that are currently visible on the screen, improving memory usage and performance compared to manually mapping arrays.

| Prop                     | Type        | Description                                              |
| ------------------------ | ----------- | -------------------------------------------------------- |
| `data`                   | `Array`     | List of items to display                                 |
| `renderItem`             | `function`  | Function that returns the UI for each item               |
| `keyExtractor`           | `function`  | Returns a unique key for each item                       |
| `horizontal`             | `boolean`   | Renders list horizontally if true                        |
| `numColumns`             | `number`    | Displays items in grid format                            |
| `columnWrapperStyle`     | `object`    | Styles each row when using `numColumns > 1`              |
| `ListHeaderComponent`    | `component` | Adds a component at the top of the list                  |
| `ListFooterComponent`    | `component` | Adds a component at the bottom                           |
| `ItemSeparatorComponent` | `component` | Renders a separator between items                        |
| `onEndReached`           | `function`  | Called when end of list is reached (for infinite scroll) |

### 🧾 What is ScrollView?
**ScrollView** is a React Native component that enables scrolling when the content inside exceeds the dimensions of the screen. It's ideal for small to moderately long content where all elements can be rendered at once.

| Prop                           | Type        | Description                                       |
| ------------------------------ | ----------- | ------------------------------------------------- |
| `horizontal`                   | `boolean`   | Enables horizontal scrolling                      |
| `contentContainerStyle`        | `object`    | Styles the inner container (useful for alignment) |
| `showsVerticalScrollIndicator` | `boolean`   | Shows/hides the scroll bar                        |
| `onScroll`                     | `function`  | Called during scroll events                       |
| `refreshControl`               | `component` | Adds pull-to-refresh functionality                |
| `keyboardShouldPersistTaps`    | `string`    | Determines keyboard behavior during taps          |

### 📘 What is TextInput?
**TextInput** is a core React Native component that allows users to enter text. It’s used to build forms, login screens, chat interfaces, and more.

| Prop              | Type       | Description                                                    |
| ----------------- | ---------- | -------------------------------------------------------------- |
| `value`           | `string`   | The current value of the input                                 |
| `onChangeText`    | `function` | Callback when the text changes                                 |
| `placeholder`     | `string`   | Placeholder text                                               |
| `keyboardType`    | `string`   | Type of keyboard (`default`, `email-address`, `numeric`, etc.) |
| `secureTextEntry` | `boolean`  | Hides input text (used for passwords)                          |
| `multiline`       | `boolean`  | Allows multiple lines of text                                  |
| `numberOfLines`   | `number`   | Number of visible lines for multiline input                    |
| `maxLength`       | `number`   | Maximum characters allowed                                     |
| `editable`        | `boolean`  | Enables/disables editing                                       |
| `autoFocus`       | `boolean`  | Automatically focuses the input when mounted                   |
| `style`           | `object`   | Styling for the input box                                      |


### 📘 What is Navigation?
**Navigation** in React Native allows users to move between different screens or views in a mobile app—just like navigating between web pages. React Native doesn't include navigation by default, so developers typically use libraries like **React Navigation**.

| Type                  | Description                                           |
| --------------------- | ----------------------------------------------------- |
| **Stack Navigation**  | Manages screens in a stack (like web browser history) |
| **Tab Navigation**    | Displays screens using tabs at the bottom or top      |
| **Drawer Navigation** | Side menu for navigating between screens              |
| **Nested Navigation** | Combining navigators (e.g., Tab inside Stack)         |
