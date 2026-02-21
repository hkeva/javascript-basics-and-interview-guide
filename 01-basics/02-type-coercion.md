## Type Coercion

**Type coercion** is a process by which JavaScript automatically converts a value from one type to another when it's required by the context.

- **Implicit Coercion:** JavaScript converts types automatically.
- **Explicit Coercion:** You manually convert a value to a specific type.

&nbsp;

**Implicit Coercion (Automatic)**

Occurs when an operation expects a certain type, so JavaScript tries to convert the value automatically.

#### Examples:

```js
// Number + String => String
console.log(5 + "5"); // "55" (number 5 is converted to string)

// Number + String => String
console.log("Age: " + 5); // "Age: 5" (number 5 is converted to string)

// String - Number => Number
console.log("10" - 2); // 8 (string "10" converted to number)

// Boolean in numeric context
console.log(true + 2); // 3 (true → 1, false → 0)

// null and undefined behave differently
console.log(null + 1); // 1   (null → 0)
console.log(undefined + 1); // NaN (undefined → NaN)

/* 
💡 Rule of Thumb: Type Coercion in JavaScript
       + operator → prefers string if any operand is a string
       -, *, / → prefer number
*/
```

&nbsp;

**Explicit Coercion (Manual)**

You can manually convert types using functions:

```js
let str = "123";
let num = Number(str); // converts string to number
console.log(num + 2); // 125

let n = 42;
let s = String(n); // converts number to string
console.log(s + " apples"); // "42 apples"

let bool = Boolean(0); // converts number to boolean
console.log(bool); // false
```

&nbsp;

**Falsy Values**

These are the only values that coerce to `false` in a boolean context — everything else is truthy:

| Value       | Type      |
| ----------- | --------- |
| `0`         | Number    |
| `""`        | String    |
| `null`      | Null      |
| `undefined` | Undefined |
| `NaN`       | Number    |
| `false`     | Boolean   |

&nbsp;

**Loose vs Strict Equality**

Loose equality (`==`) triggers coercion, which can cause unexpected bugs. Strict equality (`===`) does not coerce — it checks both value and type.

```js
console.log(0 == false); // true  (coercion happens)
console.log(0 === false); // false (strict, no coercion)

console.log("" == false); // true
console.log("" === false); // false

// 💡 Prefer === in almost all cases to avoid coercion surprises
```

&nbsp;

**NaN (Not a Number)**

`NaN` is the result of an invalid numeric operation. It's contagious — any arithmetic involving `NaN` returns `NaN`. It also has a unique property: it is never equal to itself.

```js
console.log(NaN === NaN); // false (NaN is never equal to itself)

// Use Number.isNaN() to check for NaN
console.log(Number.isNaN(NaN));   // true
console.log(Number.isNaN("abc")); // false (unlike the older isNaN())

// NaN is contagious
console.log(NaN + 5);  // NaN
console.log(NaN * 10); // NaN
` ` `
```
