## Type Coercion

**Type coercion** is a process by which JavaScript automatically converts a value from one type to another when it’s required by the context.

- **Implicit Coercion:** JavaScript converts types automatically.
- **Explicit Coercion:** You manually convert a value to a specific type.

&nbsp;

**Implicit Coercion (Automatic)**

Occurs when an operation expects a certain type, so JavaScript tries to convert the value automatically.

#### Examples:

```js
// Number + String => String
console.log(5 + "5"); // "55" (number 5 is converted to string)

// String - Number => Number
console.log("10" - 2); // 8 (string "10" converted to number)

// Boolean in numeric context
console.log(true + 2); // 3 (true → 1, false → 0)

/* 
💡 Rule of Thumb: Type Coercion in JavaScript
       + operator → prefers string if any operand is a string
       -, *, / → prefer number
*/
```

**Explicit Coercion (Manual)**

You can manually convert types using functions:

```js
let str = "123";
let num = Number(str); // converts string to number
console.log(num + 2); // 125

let n = 42;
let s = String(n); // converts number to string
console.log(s + " apples"); // "42 apples"

let bool = Boolean(0); // false
console.log(bool);
```
