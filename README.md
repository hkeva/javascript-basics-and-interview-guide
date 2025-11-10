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

**Reference Types:** `Object`, `Array`, `Function`, etc.  
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
#### JavaScript Data Types - Tricky Questions

```js
console.log(typeof null); // Output: "object" - null is a primitive, but typeof returns "object" due to historical JS quirk

console.log(typeof NaN); // Output: "number" - NaN is a numeric type even though it means "Not a Number"

console.log([] == false);  // Output: true - [] is converted to "" (empty string), which is falsy (like 0)

console.log([1,2] + [3,4]); // Output: "1,23,4" - arrays are converted to strings and concatenated

console.log(typeof (typeof 1)); // Output: "string" - typeof 1 -> "number", typeof "number" -> "string"

console.log(0 == '0'); // Output: true - '0' is converted to number 0, 0 == 0

console.log([] == ![]); // Output: true - ![] -> false (because [] is truthy), [] == false -> true

console.log([1] == 1); // Output: true - [1] is converted to "1", then "1" == 1 -> true

console.log('5' + 1); // Output: "51" - + triggers string concatenation

console.log(2 + 3 + 4 + '5'); // 2+3+4=9, then 9+'5'='95' (string concatenation)

console.log('5' - 1);       // Output: 4 - triggers numeric conversion ('5' -> 5, 5 - 1 = 4)

console.log('10'-'4'-'3'-2+'5'); // 10-4-3-2=1, then 1+'5'='15' (string concatenation)

console.log([] + []);       // Output: "" - arrays are converted to strings, "" + "" = ""

console.log([] + {});       // Output: "[object Object]" - [] -> "", {} -> "[object Object]", concatenated

console.log({} + []);       // Output: 0 - {} at line start treated as block, +[] -> 0

console.log({} + {});       // Output: NaN - {} treated as block, +{} -> NaN

console.log(false == '0');  // Output: true - '0' -> 0, false -> 0, 0 == 0

console.log(true + false);  // Output: 1 - true -> 1, false -> 0, 1 + 0 = 1

console.log([] == 0);       // Output: true - [] -> "" -> 0, 0 == 0

console.log('' == 0);       // Output: true - '' -> 0, 0 == 0

console.log(0 == []);       // Output: true - [] -> "" -> 0, 0 == 0

console.log(0 == {});       // Output: false - {} -> "[object Object]" -> NaN, 0 == NaN -> false

console.log(null == undefined); // Output: true - special case, null and undefined are equal with ==

```
