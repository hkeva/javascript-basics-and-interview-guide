## Truthy vs Falsy values

In JavaScript, values are evaluated in boolean contexts as either **truthy** or **falsy**.

**Falsy Values** - All values that are not falsy are truthy. Examples:

```js
(false, 0, -0, 0n, "", null, undefined, NaN);
```

**Truthy Values** - The following values are considered `false` in boolean contexts:

```js
(true, 1, -1, "hello", [], {}, function () {});
```

**Example:**

```js
if ("") console.log("Truthy"); // won't run
if ("hello") console.log("Truthy"); // runs
```
