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

### ii. Assignment Operators

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
