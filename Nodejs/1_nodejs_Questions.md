## ❓ Q: What is Node.js?

### ✅ Answer:

**Node.js** is an **open-source, cross-platform JavaScript runtime environment** that allows you to run JavaScript code **outside the browser**, typically on the **server-side**.

It is built on **Google Chrome’s V8 JavaScript engine**, which makes it fast and efficient.

---

## 🚀 Key Features of Node.js:

- 🧠 **JavaScript Everywhere**: Use JavaScript for both frontend and backend development.
- ⚡ **Asynchronous and Event-Driven**: Non-blocking I/O operations make Node.js highly scalable.
- 🧩 **Built-in Modules**: Core modules like `http`, `fs`, and `path` are available out of the box.
- 🌐 **NPM (Node Package Manager)**: World's largest ecosystem of open-source libraries and packages.
- 🔁 **Single-threaded with Event Loop**: Handles multiple client requests efficiently using non-blocking architecture.

---

## 🧪 Example: Simple Node.js Server

```js
// app.js
const http = require('http');

const server = http.createServer((req, res) => {
  res.end('Hello from Node.js server!');
});

server.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});


## Q: What is the difference between JavaScript and Node.js?

### ✅ Answer:

| Feature                 | JavaScript                            | Node.js                                         |
|-------------------------|----------------------------------------|-------------------------------------------------|
| 📍 Where It Runs        | Runs in the **browser**                | Runs **outside the browser** on the **server**  |
| 🛠️ Environment          | Used for **client-side** scripting     | Used for **server-side** development            |
| 🚀 Engine               | Any browser’s JS engine (like V8, SpiderMonkey) | Uses **Chrome V8 engine** internally         |
| 📚 Usage                | DOM manipulation, UI interaction       | Backend logic, server creation, APIs            |
| 🧩 Modules/Packages     | No built-in module system              | Comes with **modules** (e.g., fs, http, path)   |
| 🌐 Access to OS         | Cannot access file system or OS        | Can access file system and OS modules           |
| 📦 Package Manager      | No package manager                    | Uses **npm** (Node Package Manager)             |
| 🔁 Multithreading       | Single-threaded                        | Single-threaded but non-blocking with event loop|

---

## 🧠 In Simple Terms:

- **JavaScript** is a **programming language** used mainly in web browsers.
- **Node.js** is a **runtime environment** that allows JavaScript to run on the **server**.

---

## 🧪 Example:

### JavaScript (Browser)
```html
<script>
  alert("Hello from JavaScript!");
</script>
```
