## 📦 APK vs AAB

### ✅ APK (Android Package Kit)
- `.apk` is the **file format used to install apps on Android** devices.
- It contains all the components: code, resources, assets, certificates, and manifest.
- Used for **manual installation** and was the standard upload format for Play Store before.
- You can directly install an APK on any Android device.

**Example:** When you download an app from a website or share it via Bluetooth, it's usually an `.apk` file.

---

### ✅ AAB (Android App Bundle)
- `.aab` is a **newer publishing format introduced by Google**.
- It contains **all configurations and resources** for your app but **is not directly installable**.
- When uploading to Google Play, it automatically generates **optimized APKs** for each user’s device.
- Improves performance by **reducing app size** and only delivering what's needed.

---

### 📌 Summary Table

| Format | Full Form                | Purpose                              | Installable Directly |
|--------|--------------------------|---------------------------------------|-----------------------|
| APK    | Android Package Kit      | Installation on Android devices       | ✅ Yes                |
| AAB    | Android App Bundle       | Upload to Play Store for optimization | ❌ No (needs Google Play) |

---

### 🚀 Tip
Use `.aab` when **publishing to the Play Store**, and `.apk` when you want to **test or distribute directly**.


# 🚀 Splash Screen / Launch Screen in React Native

## ✅ What is a Splash Screen?
A **Splash Screen** (also called a Launch Screen) is the **first screen** shown to users when the app starts. It usually displays the **app logo, name, or branding** while the app loads in the background.

### 🎯 Purpose:
- Shows branding (logo, app name)
- Improves user experience
- Hides loading/setup time
- Makes the app look professional

---

## 🛠️ How to Create a Basic Manual Splash Screen

### Step 1: Create `SplashScreen.js`

```js
import React, { useEffect } from 'react';
import { View, Text, StyleSheet, Image } from 'react-native';

const SplashScreen = ({ navigation }) => {
  useEffect(() => {
    const timer = setTimeout(() => {
      navigation.replace('Home'); // Navigates to main screen
    }, 2000);

    return () => clearTimeout(timer);
  }, []);

  return (
    <View style={styles.container}>
      <Image source={require('../assets/logo.png')} style={styles.logo} />
      <Text style={styles.title}>Welcome to My App</Text>
    </View>
  );
};

export default SplashScreen;

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#fff',
  },
  logo: {
    width: 120,
    height: 120,
    marginBottom: 20,
  },
  title: {
    fontSize: 22,
    fontWeight: 'bold',
  },
});
```

### 📘 SectionList in React Native
The SectionList component in React Native is used to render grouped lists of data, where each group (called a section) has a title and items.

# Features
- Grouped data display
- Built-in support for section headers
- Scroll performance optimized
- Similar to FlatList but supports sections

### 🔥 What is Firebase?
Firebase is a Backend-as-a-Service (BaaS) platform developed by Google that helps you build and scale mobile and web apps quickly.

It offers many ready-to-use backend services so that you don't have to build the backend from scratch.

# 🧠 Why Firebase is Used in React Native?
Firebase makes mobile app development faster and easier because it provides:
| Feature                | Purpose                                     |
| ---------------------- | ------------------------------------------- |
| **Authentication**     | Sign up, login, Google/Facebook login, etc. |
| **Firestore Database** | Real-time NoSQL database to store data      |
| **Firebase Storage**   | Store images, videos, files                 |
| **Cloud Functions**    | Run backend logic without a server          |
| **Firebase Hosting**   | Host web apps easily                        |
| **Push Notifications** | Send messages to users (via FCM)            |
| **Analytics**          | Track user behavior in the app              |


### 📄 Dimensions in React Native
`Dimensions` is a built-in API in React Native used to get the **device screen's width, height, and scale**. It helps make your app responsive across different screen sizes.


## 📌 Notes
 - Dimensions.get('window') returns size excluding status bar.
 - Dimensions.get('screen') includes everything (use only if necessary).
 - Always test on multiple devices and orientations.

