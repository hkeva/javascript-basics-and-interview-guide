# 📦 Variables in JavaScript

Variables are containers for storing data values. In JavaScript, there are three ways to declare a variable: `var`, `let`, and `const`.

&nbsp;

## What is a Variable?

A variable is a named storage location in memory. You can store a value, update it, and refer to it later using its name.

```js
let name = "Eva";
console.log(name); // "Eva"
```

## var

`var` is the old (pre-ES6) way to declare variables. It has some quirky behaviors that often cause bugs.

```js
var age = 25;
var age = 30; // ✅ re-declaration allowed
age = 35; // ✅ re-assignment allowed

console.log(age); // 35
```

**Key behaviors:**

- Function-scoped (not block-scoped)
- Hoisted to the top of its scope and initialized as `undefined`
- Can be re-declared and re-assigned
- Becomes a property of the window object when declared in the global scope (in browsers)

## let

`let` was introduced in ES6 (2015) and is the go-to for variables that will change.

```js
let score = 10;
score = 20; // ✅ re-assignment allowed

let score = 50; // ❌ SyntaxError: Cannot re-declare 'score'
```

**Key behaviors:**

- Block-scoped `{}`
- Hoisted but not initialized (Temporal Dead Zone)
- Cannot be re-declared in the same scope
- Can be re-assigned

## const

`const` is for values that should not be reassigned.

```js
const PI = 3.14;
PI = 3.15; // ❌ TypeError: Assignment to constant variable
```

**Key behaviors:**

- Block-scoped `{}`
- Hoisted but not initialized (Temporal Dead Zone)
- Must be initialized at the time of declaration
- Cannot be re-declared or re-assigned
- BUT: objects and arrays declared with `const` are still mutable!

```js
const user = { name: "Eva" };
user.name = "Hkeva"; // ✅ This works! (mutating the object, not reassigning)
user = {}; // ❌ This fails! (reassigning the variable)

const nums = [1, 2, 3];
nums.push(4); // ✅ Works
nums = []; // ❌ Fails
```

&nbsp;

## ✅ Best Practice

Use `const` by default.

Use `let` when reassignment is needed.

Avoid `var` in modern JavaScript.

&nbsp;

> 📌 **Note:** Scope and Hoisting is discussed in the next section.
