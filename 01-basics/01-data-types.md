## Data Types

### i. Dynamically typed language

JavaScript is a **dynamically typed language**, because the type of a variable is determined at runtime, not at compile time.

- You don’t need to declare a variable’s type (like int, string, etc.) — JavaScript figures it out automatically based on the **value** you assign.
- JavaScript allows **reassigning** a variable with a value of a different type, and this is directly because of its dynamic typing.

### 💬 Example:

```js
let value = 10; // initially a Number
console.log(typeof value); // "number"

value = "Hello"; // now reassign a String
console.log(typeof value); // "string"

value = true; // now reassign a Boolean
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
let x = 10; // x stores value 10 at memory address A
let y = x; // y stores a copy of 10 at memory address B
y = 20;
console.log(x); // 10 (x remains unchanged)
```

**Reference Types:** In JavaScript, everything that’s not a primitive is an object. For example - `Object`, `Array`, `Function`, `Date`, `Map` etc.

- **Mutable** → their contents can be changed.
- **Copied by reference** → assigning an object to another variable stores a **reference (memory address) pointing to the same object in heap memory**.

#### 💬 Example: Mutable

```js
let obj1 = { name: "Alice" }; // obj1 stores reference to object at memory address C
let obj2 = obj1; // obj2 stores the same reference (address C)
obj2.name = "Bob";
console.log(obj1.name); // "Bob" (obj1 also changes because both point to same address)
```
