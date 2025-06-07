## Type Coercion in JavaScript

**Type Coercion** is the automatic or implicit conversion of values from one data type to another (such as a string to a number, or a boolean to a string) by JavaScript.

### Example:

```javascript
let result = '5' + 3;
console.log(result); // "53" - Number 3 is coerced to string

let sum = '5' - 2;
console.log(sum); // 3 - String '5' is coerced to number

let isTrue = '5' == 5;
console.log(isTrue); // true - Both values are coerced to the same type 
```
      