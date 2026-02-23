> **Q: What are the different data types in JavaScript?** 👉 [View explanation](./01-data-types.md#i-dynamically-typed-language)

> **Q: What's the main difference between Primitive and Reference types?** 👉 [View explanation](./01-data-types.md#ii-types)

> **Q: Mutable vs Immutable: Which types are mutable or immutable?** 👉 [View explanation](./01-data-types.md#ii-types)

> **Q: What does typeof null return, and why?** null is a primitive that represents “no value,” but typeof null mistakenly returns "object". This is a historical bug in JavaScript.

> **Q: What’s the difference between null and undefined?** undefined occurs when a variable has been declared but not assigned any value. It happens automatically. null is when a variable is explicitly set to represent “no value”. It’s intentional.
> &nbsp;
> Easy way to remember:
> undefined → “forgot to assign”
> null → “intentionally empty”

> **Q: How does JavaScript handle type coercion?** 👉 [View answer](./02-type-coercion.md#type-coercion)

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

> **Q: What are "truthy" and "falsy" values?** 👉 [View answer](./03-truthy-falsy.md#truthy-vs-falsy-values)

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

> **Q: Difference between == and === ?** checks only the value and performs type conversion if needed, while === checks both value and type without converting. For example, 5 == '5' is true, but 5 === '5' is false.

> **Q: How does null == undefined and null === undefined evaluate?** null == undefined is true because they are considered loosely equal, but null === undefined is false since their types are different.

> **Q: Difference between 0 == false and 0 === false ?** 0 == false is true due to type coercion, but 0 === false is false because their types do not match.

> **Q: What is the result of '5' > 3 and why?** JavaScript converts the string '5' to the number 5 before comparing. So '5' > 3 evaluates to true.

> **Q: What will true || false && false return?** Logical && has higher precedence than ||, so false && false is false, and then true || false is true. The final result is true.

> **Q: Can logical operators return non-boolean values?** Yes. Logical operators return the actual value of operands, not just true or false. For example, 0 || 'hello' returns 'hello' and 'hi' && 0 returns 0.

> **Q: Can you chain multiple ternary operators? Show an example.** Yes, you can chain them. Example:
>
> ```js
> let age = 20;
> let type = age < 13 ? "kid" : age < 20 ? "teen" : "adult";
> console.log(type); // 'adult'
> ```

> **Q: Explain the result of true + true in JS.** JavaScript automatically converts true to 1 when used in arithmetic. This is like using Number(true), so true + true equals 2.

> **Q: How does NaN behave in comparisons?** NaN == NaN is false and NaN === NaN is also false because NaN is not equal to anything, including itself. Use isNaN() or Number.isNaN() to check for NaN.

> **Q: What is the difference between `var`, `let`, and `const`?**
>
> | Feature              | `var`            | `let`      | `const`    |
> | -------------------- | ---------------- | ---------- | ---------- |
> | Introduced           | ES1              | ES6 (2015) | ES6 (2015) |
> | Scope                | Function         | Block      | Block      |
> | Re-declarable        | ✅               | ❌         | ❌         |
> | Re-assignable        | ✅               | ✅         | ❌         |
> | Must initialize      | ❌               | ❌         | ✅         |
> | Hoisting             | ✅ (`undefined`) | ✅ (TDZ)   | ✅ (TDZ)   |
> | Global `window` prop | ✅               | ❌         | ❌         |

> **Q: Is const truly immutable?** No. `const` prevents reassignment of the variable, but the value itself can still be mutated if it's an object or array.

```js
const obj = { a: 1 };
obj.a = 99; // ✅ works
obj = {}; // ❌ TypeError
```

> **Q: What is the difference between undefined and undeclared?**
> undefined — variable is declared but no value assigned
> undeclared — variable was never declared, and accessing it throws ReferenceError

```js
let x;
console.log(x); // undefined
console.log(y); // ❌ ReferenceError: y is not defined
```

> **Q: Does var attach to the window object?** Yes, in browsers, `var` declared in the global scope (non-module) becomes a property of window. `let` and `const` do not.

```js
var a = 10;
console.log(window.a); // 10 ✅
```

> **Q: Can you use a variable before declaring it with `var`?** Yes. Due to hoisting, `var` declarations are registered and initialized with undefined during the creation phase, so the variable exists before its declaration but has the value undefined.

> **Q: What is the output?**

```js
var a = 1;
{
  var a = 2;
}
console.log(a); // 2 ❗
```

var is not block-scoped, so both declarations refer to the same variable.
