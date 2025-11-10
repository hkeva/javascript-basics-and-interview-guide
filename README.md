# JavaScript Basics & Interview Guide

A complete, well-organized collection of **JavaScript concepts**, **code examples**, and **interview questions** with clear, detailed explanations.  
Ideal for **beginners** building a solid foundation or **developers** preparing for interviews.

---

## Table of Contents

1. [Data Types](#data-types)


---

## Data Types

1. JavaScript is a **dynamically typed language**, because the type of a variable is determined at runtime, not at compile time.  

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