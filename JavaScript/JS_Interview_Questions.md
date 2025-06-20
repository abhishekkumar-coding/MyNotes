📄 01_basics.md - JS Basics (Variables, Data Types, Operators, etc.)


### Different Data Types in JavaScript
JavaScript has two main categories of data types:

Primitive Data Types (immutable, stored by value)

Non-Primitive (Reference) Data Types (mutable, stored by reference)

### Primitive
Number	Represents integers & floating-point numbers	let x = 10;
String	Represents a sequence of characters	let name = "John";
Boolean	Represents true or false values	let isActive = true;
BigInt	Used for very large integers	let bigNum = 1234567890123456789n;
Symbol	Unique & immutable identifier (mostly for object properties)	let sym = Symbol("id");
Undefined	A variable declared but not assigned a value	let x;
Null	Represents an intentional absence of value	let y = null;

### Non-Primitive

Object	Collection of key-value pairs	let user = { name: "John", age: 25 };
Array	Ordered list of values	let arr = [1, 2, 3, 4];
Function	A block of reusable code	function greet() { return "Hello"; }

## ❓ Q: `require` aur `import` mein kya antar hai?

### ✅ Answer:

| Feature            | `require()`                             | `import`                                |
|--------------------|------------------------------------------|------------------------------------------|
| Module System      | CommonJS                                | ES6 Modules                              |
| Platform           | Node.js (backend)                       | React, Next.js, Modern JS (frontend)     |
| Syntax             | `const fs = require('fs')`              | `import fs from 'fs'`                    |
| Synchronous        | Haan (line-by-line load hota hai)       | Nahin (compile time par decide hota hai) |
| Dynamic Import     | Possible directly                       | Possible with `import()` syntax          |
| Use in Browser     | Nahin                                   | Haan (after transpile via Babel/Webpack) |

---

## 📌 Kab kya use karein?

- **Node.js backend project**: `require()` use karein.
- **React / Next.js / Frontend apps**: `import` use karein.

---

## 🧪 Examples

### 🔹 Using `require` (Node.js):
```js
const fs = require('fs');
const express = require('express');