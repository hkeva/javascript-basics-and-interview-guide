# JavaScript Basics & Interview Guide

A complete, well-organized collection of **JavaScript concepts**, **code examples**, and **interview questions** with clear, detailed explanations.  
Ideal for **beginners** building a solid foundation or **developers** preparing for interviews.

---

## Table of Contents

**1.** [Data Types](#data-types)
**2.** [Operators](#operators)

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

> **Q: What are the different data types in JavaScript?** [Go to answer.](#ii-types)

> **Q: What's the main difference between Primitive and Reference types?** [Go to answer.](#ii-types)

> **Q: Mutable vs Immutable: Which types are mutable or immutable?** [Go to answer.](#ii-types)

> **Q: What does typeof null return, and why?** null is a primitive that represents “no value,” but typeof null mistakenly returns "object". This is a historical bug in JavaScript.

> **Q: What’s the difference between null and undefined?** undefined occurs when a variable has been declared but not assigned any value. It happens automatically. null is when a variable is explicitly set to represent “no value”. It’s intentional.
> &nbsp;
> Easy way to remember:
> undefined → “forgot to assign”
> null → “intentionally empty”

> **Q: How does JavaScript handle type coercion?** [Go to answer.](#iii-type-coercion)

> **Q: What does typeof NaN return and why?** In JavaScript, NaN is actually considered a number—even though it represents an invalid number. So typeof will always return "number" and cannot detect NaN.
```
console.log(typeof NaN); // "number"
```

> **Q: How do you check if a value is NaN?** The recommended way to check for NaN is using Number.isNaN():
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

> **Q: What are "truthy" and "falsy" values?** [Go to answer.](#iv-truthy-vs-falsy-values)

> **Q: What is the output console.log(typeof (typeof 1)); ?** Output: "string" — the first typeof gives "number", which is a string, so the outer typeof returns "string".

> **Q: What is the output of `console.log('5' + 1);`?** Output: `"51"` — `'5' + 1` converts `1` to a string and concatenates.  

> **Q: What is the output of `console.log(2 + 3 + 4 + '5');`?** Output: `"95"` — `2 + 3 + 4 = 9`, then `9 + '5'` concatenates to `"95"`.  

> **Q: What is the output of `console.log('5' - 1);`?** Output: `4` — `'5'` is converted to a number and `1` is subtracted.  

> **Q: What is the output of `console.log('10'-'4'-'3'-2+'5');`?** Output: `"15"` — `'10'-'4'-'3'-2 = 1`, then `1 + '5'` concatenates to `"15"`.  

> **Q: What is the output of `console.log(true + false);`?** Output: `1` — `true + false` is `1 + 0 = 1`.
 
> **Q: What is the output of `console.log(false == '0');`?** Output: `true` — `false` is falsy (converted to `0`) and `'0'` is coerced to number `0`, so they are equal.  

> **Q: What is the output of `console.log(0 == '0');`?** Output: `true` — `'0'` is coerced to number `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log([] == 0);`?** Output: `true` — `[]` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log('' == 0);`?** Output: `true` — empty string `''` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log(0 == []);`?** Output: `true` — `[]` is falsy and coerces to `0`, so `0 == 0` is `true`.  

> **Q: What is the output of `console.log(0 == {});`?** Output: `false` — `{}` is an object and does not coerce to a number, so `0 == {}` is `false`.

> **Topic: Arrays, Type Checking, and Type Coercion**  

> **Q: What does `typeof` return for an array (e.g., `[1, 2]`)?** Output: `"object"` — in JavaScript, arrays are objects, so `typeof [1,2]` returns `"object"`.

> **Q: How do you correctly check if a variable is an array?** Use `Array.isArray(variable)` — returns `true` if it is an array, `false` otherwise.

> **Q: What happens when you do `[] == ![]`?** Output: `true` — In JavaScript, every object (including `[]`) is truthy. `![]` negates it → `false`. The comparison becomes `[] == false`. During type coercion, `[]` converts to `""` (empty string) → `0`, and `false` converts to `0`. So `0 == 0` → `true`.

> **Q: What is the output of `console.log([] + []);`** Output: `""` (empty string) — adding two arrays converts them to strings and concatenates.

> **Q: What is the output of `console.log([] + {});`** Output: `"[object Object]"` — `[]` becomes `""`, `{}` becomes `"[object Object]"`, then concatenated.

> **Q: What is the output of `console.log({} + []);`** Output: `0` in Node.js / `"[object Object]"` in browser — due to how `{}` is interpreted as a block or object; type coercion differs by environment.

> **Q: What is the output of `console.log({} + {});`** Output: `NaN` in Node.js / `"[object Object][object Object]"` in browser — again, depends on environment parsing and coercion.

> **Q: What is the output of `console.log([] == false);`** Output: `true` — `[]` is falsy, coerces to `0`, `false` coerces to `0`, so `0 == 0`.

> **Q: What is the output of `console.log([1,2] + [3,4]);`** Output: `"1,23,4"` — both arrays are converted to strings and concatenated.

> **Q: What is the output of `console.log([1] == 1);`** Output: `true` — `[1]` is converted to number `1`, so `1 == 1`.
</details>

---
&nbsp;

## Operators 

### i. Arithmetic Operators
Arithmetic operators are used to perform mathematical operations: `+`, `-`, `*`, `/`, `%`, `**`, `++`, `--`
&nbsp;
**For example:** 
```
let a = 2;
let b = a ** 3; // 2 raised to 3 = 8
a++;             // a becomes 3
```

&nbsp;
### ii. Arithmetic Operators
Assignment operators are used to assign values to variables, often combining assignment with arithmetic operations: `=`, `+=`, `-=`, `*=`, `/=`, `%=`
&nbsp;
**For example:**  
```
let a = 5;   // assigns 5 to a
a += 3;      // equivalent to a = a + 3 → a becomes 8
a /= 3;      // equivalent to a = a / 3 → a becomes 4
a %= 3;      // equivalent to a = a % 3 → a becomes 1
```

&nbsp;
### iii. Comparison Operators
Comparison operators are used to compare values and return a boolean (true or false), such as: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`
&nbsp;
**For example:**  
```
let x = 5;
let y = '5';

console.log(x == y);   // true (value is equal, type is ignored, JS may coerce the type)
console.log(x === y);  // false (value is equal but type is different, no type coercion)
console.log(x != 3);   // true (x is not equal to 3)
console.log(x > 3);    // true (x is greater than 3)
console.log(x <= 5);   // true (x is less than or equal to 5)
```

&nbsp;
### iv. Logical Operators
Logical operators are used to combine or manipulate boolean values (true or false), such as: `&&`, `||`, `!`, `??`, `!!`
&nbsp;
**For example:**  
```
let x = true;
let y = false;

let andResult = x && y; // false, because both are not true
let orResult  = x || y; // true, because at least one is true
let notX      = !x;     // false, negates the value of x

// Nullish coalescing operator (??)
// If the value on the left is null or undefined, it returns the value on the right
let a;                 
let b = a ?? 10;       // b becomes 10 because a is undefined

// Double NOT operator (!!)
// Converts any value to a boolean (true or false)
let c = "hello";
let d = !!c;           // d becomes true because "hello" is a non-empty string (truthy)
```

&nbsp;
### v. Ternary Operator
The ternary operator is a shorthand for if-else statements. It uses the syntax:
condition ? valueIfTrue : valueIfFalse

&nbsp;
**For example:** 
```
let age = 18;
let canVote = (age >= 18) ? "Yes" : "No";
console.log(canVote); // "Yes"
```

&nbsp;

<details>
<summary>📘 <strong>JavaScript Operators - Tricky Questions</strong> (click to show)</summary>
&nbsp;

> **Q: Difference between == and === ?** checks only the value and performs type conversion if needed, while === checks both value and type without converting. For example, 5 == '5' is true, but 5 === '5' is false.

> **Q: How does null == undefined and null === undefined evaluate?** null == undefined is true because they are considered loosely equal, but null === undefined is false since their types are different.

> **Q: Difference between 0 == false and 0 === false ?** 0 == false is true due to type coercion, but 0 === false is false because their types do not match.

> **Q: What is the result of '5' > 3 and why?** JavaScript converts the string '5' to the number 5 before comparing. So '5' > 3 evaluates to true.

> **Q: What will true || false && false return?** Logical && has higher precedence than ||, so false && false is false, and then true || false is true. The final result is true.

> **Q: Can logical operators return non-boolean values?** Yes. Logical operators return the actual value of operands, not just true or false. For example, 0 || 'hello' returns 'hello' and 'hi' && 0 returns 0.

> **Q: Can you chain multiple ternary operators? Show an example.** Yes, you can chain them. Example:  
> ```js
> let age = 20;
> let type = age < 13 ? 'kid' : age < 20 ? 'teen' : 'adult';
> console.log(type); // 'adult'
> ```

> **Q: Explain the result of true + true in JS.** JavaScript automatically converts true to 1 when used in arithmetic. This is like using Number(true), so true + true equals 2.

> **Q: How does NaN behave in comparisons?** NaN == NaN is false and NaN === NaN is also false because NaN is not equal to anything, including itself. Use isNaN() or Number.isNaN() to check for NaN.
</details>