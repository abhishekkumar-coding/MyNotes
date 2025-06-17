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