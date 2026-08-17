# Operators and Control Flow

> Module: JavaScript Basics · Brand: **EP**
>
> Reading Time: 15–20 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-FND-004

---

# Overview

Operators compute and compare values. Control flow (`if`, `switch`, loops) decides which code runs. Together they form the logic inside functions, React event handlers, and conditional UI.

---

# Why This Matters

React rendering often looks like: “if loading, show spinner; else show data.” That is JavaScript control flow expressed in JSX. Solid operator and branching skills make those patterns obvious instead of mysterious.

---

# Learning Objectives

After this article, you'll be able to:

- Use arithmetic, comparison, and logical operators.
- Write `if` / `else` and `switch` branches.
- Loop with `for` and `while`.
- Recognize truthy and falsy values.
- Prefer `===` over `==`.

---

# Core Concepts

## Arithmetic operators

```javascript
const a = 10;
const b = 3;

console.log(a + b); // 13
console.log(a - b); // 7
console.log(a * b); // 30
console.log(a / b); // 3.333...
console.log(a % b); // 1  (remainder)
```

Useful shorthand:

```javascript
let n = 1;
n += 2; // 3
n++;    // 4
```

---

## Comparison operators

```javascript
5 > 3;   // true
5 >= 5;  // true
"a" < "b"; // true (lexicographic)
```

### `===` vs `==`

| Operator | Meaning |
|----------|---------|
| `===` / `!==` | Strict equality — no type coercion |
| `==` / `!=` | Loose equality — coerces types (surprising) |

```javascript
0 === false; // false
0 == false;  // true  ← avoid this class of bug

"5" === 5;   // false
"5" == 5;    // true
```

**EP rule:** always prefer `===` and `!==`.

---

## Logical operators

```javascript
true && false; // false — AND
true || false; // true  — OR
!true;         // false — NOT
```

Short-circuit patterns (common in React-era JS):

```javascript
const name = userName || "Guest";
const canEdit = isAdmin && hasPermission;
```

Prefer nullish coalescing (`??`) when `0` or `""` are valid values—covered in ES6 essentials.

---

## `if` / `else`

```javascript
const score = 85;

if (score >= 90) {
  console.log("Excellent");
} else if (score >= 70) {
  console.log("Good");
} else {
  console.log("Keep practicing");
}
```

Ternary for simple expressions:

```javascript
const label = score >= 70 ? "Pass" : "Retry";
```

Keep ternaries readable; nest sparingly.

---

## `switch`

```javascript
const status = "loading";

switch (status) {
  case "loading":
    console.log("Loading…");
    break;
  case "success":
    console.log("Done");
    break;
  case "error":
    console.log("Failed");
    break;
  default:
    console.log("Unknown");
}
```

Remember `break` (or intentional fall-through).

---

## Loops: `for` and `while`

```javascript
for (let i = 0; i < 3; i++) {
  console.log(i); // 0, 1, 2
}

let n = 3;
while (n > 0) {
  console.log(n);
  n--;
}
```

For arrays, you will often prefer `map` / `filter` / `forEach` later—but `for`/`while` remain essential.

---

## Truthy and falsy

Values coerced to `false` in boolean context are **falsy**:

```javascript
false, 0, -0, 0n, "", null, undefined, NaN
```

Everything else is **truthy** (including `[]` and `{}`).

```javascript
if ("EP") {
  console.log("runs"); // truthy string
}

if (0) {
  console.log("skipped");
}
```

Be careful: empty array `[]` is truthy, so `if (items)` does not mean “has items.” Check `items.length` instead.

---

# Common Mistakes

❌ Using `==` and getting coerced comparisons.

❌ Forgetting `break` in `switch`.

❌ Treating `[]` or `{}` as falsy.

❌ Infinite `while` loops (condition never becomes false).

---

# Best Practices

- Prefer `===` / `!==` always.
- Keep conditions simple; extract complex checks to named booleans.
- Use `switch` for multi-equal branches; `if` for ranges and compound logic.
- Check array length explicitly when emptiness matters.

---

# Interview Questions

1. What is the difference between `==` and `===`?
2. List the falsy values in JavaScript.
3. Why is `[]` considered truthy?
4. When would you choose `switch` over `if` / `else`?
5. What does short-circuit evaluation mean for `&&` and `||`?

---

# Summary

Operators and control flow express decisions and repetition. Prefer strict equality, know truthy/falsy traps, and write clear branches and loops. Next you will package this logic into **functions**—the building block React components rely on.

---

# Navigation

⬅️ Previous: [JS-FND-003 — Data Types](JS-FND-003-data-types.md)

⬆️ Module: [Basics](README.md)

➡️ Next: [JS-FUN-001 — Functions Essentials](../02-functions/JS-FUN-001-functions-essentials.md)
