## Truthy vs Falsy Values

In JavaScript, every value is either **truthy** or **falsy** when evaluated in a boolean context (e.g., `if` statements, `&&`, `||`, `!`).

&nbsp;

### Falsy Values

The following values evaluate to false in a boolean context:

```js
(false, 0, -0, 0n, "", null, undefined, NaN);
```

### Truthy Values

Any value that is **not falsy** is truthy. Some common examples:

```js
(true, 1, -1, "hello", "0", " ", [], {}, function () {});
```

> ⚠️ `"0"`, `" "` (space), `[]`, and `{}` are all **truthy**, a common source of bugs!

| Value | Why Truthy                                                                                                               |
| ----- | ------------------------------------------------------------------------------------------------------------------------ |
| `" "` | Non-empty string - JS only considers `""` falsy, even a single space makes it truthy                                     |
| `[]`  | Truthy because it is an object. Objects are reference values stored in memory, and all objects are truthy in JavaScript. |
| `{}`  | Truthy for the same reason - it is an object, and all objects are truthy.                                                |

&nbsp;

### Example

```js
if ("") console.log("Truthy"); // ✗ won't run — "" is falsy
if ("hello") console.log("Truthy"); // ✓ runs    — non-empty string is truthy
if ([]) console.log("Truthy"); // ✓ runs    — empty array is truthy
if (" ") console.log("Truthy"); // ✓ runs    — space string is truthy
```

&nbsp;

### Converting to Boolean

You can explicitly convert any value to a boolean using `!!` or `Boolean()`:

```js
!!0; // false
!!null; // false
!!"hello"; // true
!![]; // true

Boolean(undefined); // false
Boolean("0"); // true
```
