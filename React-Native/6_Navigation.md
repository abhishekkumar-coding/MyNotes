### 📚 What is Stack Navigation?
Stack Navigation allows you to manage a stack of screens, just like a call stack. You can push, pop, and navigate between screens, and each new screen is stacked on top of the previous one.

```
import { View, Text } from 'react-native'
import React from 'react'
import { createStackNavigator } from '@react-navigation/stack'
import { NavigationContainer } from '@react-navigation/native'
import ScreenA from './ScreenA'
import ScreenB from './ScreenB'
import 'react-native-gesture-handler'

const Stack = createStackNavigator()

const StackNavigator = () => {
    return (
        <View style={{ flex: 1,  backgroundColor:"red"}}>
          <NavigationContainer>
              <Stack.Navigator>
                  <Stack.Screen name='ScreenA' component={ScreenA}/>
                  <Stack.Screen name='ScreenB' component={ScreenB}/>
              </Stack.Navigator>
          </NavigationContainer>
        </View>
        // <View>
        //     <ScreenA />
        //     <ScreenB/>
        //     <Text>Hey this is working</Text>
        // </View>
    )
}

export default StackNavigator
```

## 1. navigation.navigate('ScreenName', params)
 - Goes to a new screen.
 - If that screen is already on top, it won't do anything.

## 2. navigation.push('ScreenName', params)
 - Pushes a new instance of the screen on top of the stack.
 - Useful if you want to open the same screen multiple times with different data.

## 3. navigation.replace('ScreenName', params)
 - Replaces the current screen with the new one.
 - Good for login/signup flows.

 ## 4. navigation.goBack()
 - Pops the current screen from the stack and returns to the previous one.

## . navigation.pop(n)
 - Removes an screens from the stack.
 - Useful if you want to go back multiple screens at once.


 ### 📚 What is Tab Navigation?
Tab Navigation displays multiple tabs at the bottom of your app (or top, depending on design). It's perfect for apps where users frequently switch between main sections like Home, Profile, Settings, etc.

```
// App.js
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import HomeScreen from './screens/HomeScreen';
import ProfileScreen from './screens/ProfileScreen';
import SettingsScreen from './screens/SettingsScreen';

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator initialRouteName="Home">
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Profile" component={ProfileScreen} />
        <Tab.Screen name="Settings" component={SettingsScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
```

| Feature                            | Description                                                                 |
| ---------------------------------- | --------------------------------------------------------------------------- |
| `initialRouteName`                 | Set which tab opens first.                                                  |
| `tabBarOptions`                    | Customize tab bar (style, colors, icon behavior, etc.)                      |
| `tabBarIcon`                       | Show custom icons for each tab.                                             |
| `tabBarLabel`                      | Customize label under icons.                                                |
| `screenOptions`                    | Set common styling/config for all screens.                                  |
| `tabBarVisible` (deprecated in v6) | Use `tabBarStyle: { display: 'none' }` to hide tab bar for certain screens. |
| Feature                      | Purpose                 | Example                                  |
| ---------------------------- | ----------------------- | ---------------------------------------- |
| `createBottomTabNavigator()` | Create tab navigator    | `const Tab = createBottomTabNavigator()` |
| `navigation.navigate()`      | Navigate to another tab | `navigation.navigate('Cart')`            |
| `tabBarIcon`                 | Add custom icon         | `Ionicons name="cart"`                   |
| `initialRouteName`           | Set first screen        | `"Home"`                                 |
| `tabBarStyle`                | Hide/show tab bar       | `{ display: 'none' }`                    |


### 📚 What is Drawer Navigation?
Drawer Navigation provides a side menu (usually from the left) that slides out. It’s perfect for apps with multiple main sections or less frequently used screens.

You’ve seen it in apps like Gmail, Facebook, and YouTube — where tapping a hamburger menu opens a drawer with links.

| Prop / Option      | Description                                            |
| ------------------ | ------------------------------------------------------ |
| `drawerType`       | Type of drawer (`front`, `back`, `slide`, `permanent`) |
| `drawerStyle`      | Style object for drawer (width, bgColor, etc.)         |
| `drawerPosition`   | Left (default) or right                                |
| `drawerContent`    | Provide custom drawer menu component                   |
| `initialRouteName` | Set the first screen that shows up                     |


| Function                    | Description                              | Example                          |
| --------------------------- | ---------------------------------------- | -------------------------------- |
| `navigation.openDrawer()`   | Opens the drawer manually                | `navigation.openDrawer()`        |
| `navigation.closeDrawer()`  | Closes the drawer                        | `navigation.closeDrawer()`       |
| `navigation.toggleDrawer()` | Toggles drawer (open/close)              | `navigation.toggleDrawer()`      |
| `navigation.navigate()`     | Navigate to another screen inside drawer | `navigation.navigate("Profile")` |
