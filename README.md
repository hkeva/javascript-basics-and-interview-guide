# JavaScript Basics & Interview Guide

A complete, well-organized collection of **JavaScript concepts**, **code examples**, and **interview questions** with clear, detailed explanations.  
Ideal for **beginners** building a solid foundation or **developers** preparing for interviews.

---

## Table of Contents

**1.** [Data Types](#data-types)


---

## Data Types

### i. Dynamically typed language
JavaScript is a **dynamically typed language**, because the type of a variable is determined at runtime, not at compile time.  

- You don’t need to declare a variable’s type (like int, string, etc.) — JavaScript figures it out automatically based on the **value** you assign.  
- JavaScript allows **reassigning** a variable with a value of a different type, and this is directly because of its dynamic typing.

### 💬 Example:

```js
let value = 10;       // initially a Number
console.log(typeof value); // "number"

value = "Hello";      // now reassign a String
console.log(typeof value); // "string"

value = true;         // now reassign a Boolean
console.log(typeof value); // "boolean"
```


&nbsp;  
### ii. Types 
JavaScript has **two main types of data**: **Primitive** and **Reference**.  
- **Primitive** stores **actual values** in memory.  
- **Reference** stores a **pointer/address** to objects in memory, not the actual object value directly.

&nbsp;

**Primitive types:** `Number`, `String`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`  

- **Immutable** → their value cannot be changed once created.  
- **Copied by value** → assigning a primitive to another variable creates a **separate copy in memory**. Each variable has its **own memory address**.  

#### 💬 Example:

```js
// Immutable Example
let x = 10;  // x stores value 10 at memory address A
let y = x;   // y stores a copy of 10 at memory address B
y = 20;
console.log(x); // 10 (x remains unchanged)
```

**Reference Types:** In JavaScript, everything that’s not a primitive is an object. For example - `Object`, `Array`, `Function`, `Date`, `Map` etc.  
- **Mutable** → their contents can be changed.  
- **Copied by reference** → assigning an object to another variable stores a **reference (memory address) pointing to the same object in heap memory**.  

#### 💬 Example: Mutable

```js
let obj1 = { name: "Alice" }; // obj1 stores reference to object at memory address C
let obj2 = obj1;               // obj2 stores the same reference (address C)
obj2.name = "Bob";
console.log(obj1.name); // "Bob" (obj1 also changes because both point to same address)
```

&nbsp; 
### iii. Type coercion
**Type coercion** is a process by which JavaScript automatically converts a value from one type to another when it’s required by the context.

- **Implicit Coercion:** JavaScript converts types automatically.  
- **Explicit Coercion:** You manually convert a value to a specific type.

&nbsp;

**Implicit Coercion (Automatic)**

Occurs when an operation expects a certain type, so JavaScript tries to convert the value automatically.

#### Examples:

```js
// Number + String => String
console.log(5 + "5");  // "55" (number 5 is converted to string)

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
let num = Number(str);       // converts string to number
console.log(num + 2);        // 125

let n = 42;
let s = String(n);           // converts number to string
console.log(s + " apples");  // "42 apples"

let bool = Boolean(0);       // false
console.log(bool);
```

&nbsp; 
### iv. Truthy vs Falsy values

In JavaScript, values are evaluated in boolean contexts as either **truthy** or **falsy**.

**Falsy Values** - All values that are not falsy are truthy. Examples:

```js
false, 0, -0, 0n, "", null, undefined, NaN
```

**Truthy Values** - The following values are considered `false` in boolean contexts:

```js
true, 1, -1, "hello", [], {}, function(){}
```
**Example:**
```js
if ("") console.log("Truthy"); // won't run
if ("hello") console.log("Truthy"); // runs
```

&nbsp;

<details>
<summary>📘 <strong>JavaScript Data Types - Tricky Questions</strong> (click to show)</summary>
&nbsp;

```
💡 Note: There is no example using the === operator here. It is discussed later in the Operators section.
```

> **Q: What are the different data types in JavaScript?** 
> **A:** [Go to answer.](#ii-types)

> **Q: What's the main difference between Primitive and Reference types?**  
> **A:** [Go to answer.](#ii-types)

> **Q: Mutable vs Immutable: Which types are mutable or immutable?** 
> **A:** [Go to answer.](#ii-types)

> **Q: What does typeof null return, and why?**
> **A:** null is a primitive that represents “no value,” but typeof null mistakenly returns "object". This is a historical bug in JavaScript.

> **Q: What’s the difference between null and undefined?** 
> **A:** undefined occurs when a variable has been declared but not assigned any value. It happens automatically. null is when a variable is explicitly set to represent “no value”. It’s intentional.
> &nbsp;
> Easy way to remember:
> undefined → “forgot to assign”
> null → “intentionally empty”

> **Q: How does JavaScript handle type coercion?** 
> **A:** [Go to answer.](#iii-type-coercion)

> **Q: What does typeof NaN return and why?**
> **A:** In JavaScript, NaN is actually considered a number—even though it represents an invalid number. So typeof will always return "number" and cannot detect NaN.
```
console.log(typeof NaN); // "number"
```

> **Q: How do you check if a value is NaN?**
> **A:** The recommended way to check for NaN is using Number.isNaN():
```
Number.isNaN(NaN);   // true
Number.isNaN(123);   // false
```
> **Another trick:** NaN is the only value in JavaScript that is not equal to itself. Since it represents an "undefined" or "unrepresentable" number, it cannot be meaningfully compared to anything—even itself.
```
let x = NaN;
console.log(x !== x);  // true
console.log(NaN === NaN); // false
console.log(NaN !== NaN); // true
```

> **Q: What are "truthy" and "falsy" values?** 
> **A:** [Go to answer.](#iv-truthy-vs-falsy-values)

> **Q: What is the output console.log(typeof (typeof 1)); ?** 
> **A:** Output: "string" — the first typeof gives "number", which is a string, so the outer typeof returns "string".

> **Q: What is the output of `console.log('5' + 1);`?**  
> **A:** Output: `"51"` — `'5' + 1` converts `1` to a string and concatenates.  

> **Q: What is the output of `console.log(2 + 3 + 4 + '5');`?**  
> **A:** Output: `"95"` — `2 + 3 + 4 = 9`, then `9 + '5'` concatenates to `"95"`.  

> **Q: What is the output of `console.log('5' - 1);`?**  
> **A:** Output: `4` — `'5'` is converted to a number and `1` is subtracted.  

> **Q: What is the output of `console.log('10'-'4'-'3'-2+'5');`?**  
> **A:** Output: `"15"` — `'10'-'4'-'3'-2 = 1`, then `1 + '5'` concatenates to `"15"`.  

> **Q: What is the output of `console.log(true + false);`?**  
> **A:** Output: `1` — `true + false` is `1 + 0 = 1`.

> **Topic: Truthy / Falsy and Type Coercion**  

> **Q: What is the output of `console.log(false == '0');`?**  
> **A:** Output: `true` — `false` is falsy (converted to `0`) and `'0'` is coerced to number `0`, so they are equal.  

> **Q: What is the output of `console.log(0 == '0');`?**  
> **A:** Output: `true` — `'0'` is coerced to number `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log([] == 0);`?**  
> **A:** Output: `true` — `[]` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log('' == 0);`?**  
> **A:** Output: `true` — empty string `''` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log(0 == []);`?**  
> **A:** Output: `true` — `[]` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log(0 == {});`?**  
> **A:** Output: `false` — `{}` is an object and does not coerce to a number, so `0 == {}` is `false`.

> **Topic: Arrays, Type Checking, and Type Coercion**  

> **Q: What does `typeof` return for an array (e.g., `[1, 2]`)?**  
> **A:** Output: `"object"` — in JavaScript, arrays are objects, so `typeof [1,2]` returns `"object"`.

> **Q: How do you correctly check if a variable is an array?**  
> **A:** Use `Array.isArray(variable)` — returns `true` if it is an array, `false` otherwise.

> **Q: What happens when you do `[] == ![]`?**  
> **A:** Output: `true` — In JavaScript, every object (including `[]`) is truthy. `![]` negates it → `false`. The comparison becomes `[] == false`. During type coercion, `[]` converts to `""` (empty string) → `0`, and `false` converts to `0`. So `0 == 0` → `true`.

> **Q: What is the output of `console.log([] + []);`**  
> **A:** Output: `""` (empty string) — adding two arrays converts them to strings and concatenates.

> **Q: What is the output of `console.log([] + {});`**  
> **A:** Output: `"[object Object]"` — `[]` becomes `""`, `{}` becomes `"[object Object]"`, then concatenated.

> **Q: What is the output of `console.log({} + []);`**  
> **A:** Output: `0` in Node.js / `"[object Object]"` in browser — due to how `{}` is interpreted as a block or object; type coercion differs by environment.

> **Q: What is the output of `console.log({} + {});`**  
> **A:** Output: `NaN` in Node.js / `"[object Object][object Object]"` in browser — again, depends on environment parsing and coercion.

> **Q: What is the output of `console.log([] == false);`**  
> **A:** Output: `true` — `[]` is falsy, coerces to `0`, `false` coerces to `0`, so `0 == 0`.

> **Q: What is the output of `console.log([1,2] + [3,4]);`**  
> **A:** Output: `"1,23,4"` — both arrays are converted to strings and concatenated.

> **Q: What is the output of `console.log([1] == 1);`**  
> **A:** Output: `true` — `[1]` is converted to number `1`, so `1 == 1`.


</details>

