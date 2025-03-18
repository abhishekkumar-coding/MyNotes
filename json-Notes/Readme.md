# What is JSON?

- **JSON** stands for **JavaScript Object Notation**.
- JSON is a **lightweight** data-interchange format.
- JSON is **plain text** written in JavaScript object notation.
- JSON is used to **send data between computers**.
- JSON is **language independent**.

Since the format is text-only, JSON data can easily be sent between computers and used by any programming language.

---

## JSON in JavaScript

JavaScript has built-in functions for working with JSON:

- Convert a **JSON string** into a **JavaScript object**:
  ```javascript
  const jsonString = '{"name": "John", "age": 30}';
  const jsonObject = JSON.parse(jsonString);
  console.log(jsonObject.name); // Output: John
