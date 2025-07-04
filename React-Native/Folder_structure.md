### __tests__
The __tests__ folder is used to store test files for your app. These test files help check if your app's code is working correctly.

### .bundle
A JavaScript file created when you build your app for release.

Contains all your code in one file.

Used when the app runs without Metro server (offline/production mode).

### android
All files needed to build and run your app on Android phones.

Written in Java/Kotlin.

You open this with Android Studio if you want to change native Android stuff.

### ios
All files needed to build and run your app on iPhones (iOS).

Written in Swift/Objective-C.

You open this with Xcode.

### node_modules
Contains all libraries and packages installed by npm or yarn.

Auto-generated when you run npm install.

Don’t edit anything manually in this folder.

### .eslintrc
ESLint configuration file.

Helps find and fix coding mistakes automatically.

Controls the rules for code style (like semicolons, spacing).

### .gitignore
Tells Git which files/folders to ignore.

Example: node_modules, android/build, etc.

Keeps your Git repo clean and lightweight.

### .prettierrc.js
Configuration for Prettier, a tool that formats your code.

Example: Controls things like indentation, quotes, trailing commas.

### .watchmanconfig
Used by Watchman, a tool by Facebook.

Helps React Native detect file changes faster.

Mostly used on macOS/Linux.

### App.js
The main component of your app.

It contains the starting UI and connects all screens and components.

You edit this to build your app’s homepage or layout.

### app.json
Basic configuration file for your app.

Example:

json
Copy
Edit
```
{
  "name": "MyApp",
  "displayName": "MyApp"
}

```
Used by React Native CLI and tools like Expo.

### babel.config.js
Tells Babel how to convert modern JavaScript into a version React Native can understand.

Important for using latest JS features like async/await, optional chaining, etc.

### gemfile
Only seen in iOS projects (Ruby-based).

Used by CocoaPods, a package manager for iOS.

You don't touch this unless you’re working on iOS native stuff.

### index.js
The entry point of your app.

It tells React Native to start running the App.js file.

You rarely need to change this.

### jest.config.js
Configuration file for Jest, a testing tool.

Helps you test your components and functions automatically.

### metro.config.js
Configuration for Metro bundler (used in development).

Lets you customize how assets and files are bundled (like custom fonts or images).

### package-lock.json
Auto-generated when you install packages.

Locks the exact version of each package.

Ensures that your project works the same on every device.

### package.json
The heart of your project.

Lists your app’s name, version, dependencies (libraries), and scripts.

### README.md
A description file for your project (written in Markdown).

You can write what your app does, how to install it, etc.

Shown on GitHub if you upload your project there.

### tsconfig.json
Only used if you’re using TypeScript (instead of JavaScript).

It tells TypeScript how to check and compile your .ts or .tsx files.


| File/Folder         | Use                             |
| ------------------- | ------------------------------- |
| `.bundle`           | JS code bundle for production   |
| `android/`          | Android app code                |
| `ios/`              | iOS app code                    |
| `node_modules/`     | Installed libraries             |
| `.eslintrc`         | Linting rules                   |
| `.gitignore`        | Tells Git what to ignore        |
| `.prettierrc.js`    | Prettier code formatting rules  |
| `.watchmanconfig`   | Watchman config (file watching) |
| `App.js`            | Main app component              |
| `app.json`          | App metadata/config             |
| `babel.config.js`   | Babel settings                  |
| `Gemfile`           | iOS dependency file             |
| `index.js`          | Entry point                     |
| `jest.config.js`    | Jest testing settings           |
| `metro.config.js`   | Metro bundler config            |
| `package-lock.json` | Locked versions of packages     |
| `package.json`      | Project info and scripts        |
| `README.md`         | Project guide                   |
| `tsconfig.json`     | TypeScript config               |
