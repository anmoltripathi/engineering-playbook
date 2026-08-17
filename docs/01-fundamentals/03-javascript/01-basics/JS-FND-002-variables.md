# Variables

> Module: JavaScript Basics · Brand: **EP**
>
> Reading Time: 12–18 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-FND-002

---

# Overview

Variables store values you can reuse and update. In modern JavaScript you primarily use `let` and `const`. `var` still exists for legacy code, but you should avoid it in new EP projects.

---

# Why This Matters

Almost every React component uses variables: props, state values, derived data, event handlers. Unclear variable rules lead to bugs like unexpected `undefined`, accidental reassignment, and confusion about scope.

---

# Learning Objectives

After this article, you'll be able to:

- Declare variables with `let` and `const`.
- Explain when to prefer `const`.
- Avoid `var` in new code.
- Follow clear naming conventions.
- Describe the temporal dead zone (TDZ) at a high level.

---

# Core Concepts

## Declaring with `let` and `const`

```javascript
let count = 0;
const appName = "EP";

count = 1; // OK — let can be reassigned
// appName = "Other"; // Error — const cannot be reassigned
```

| Keyword | Reassign? | Block-scoped? | Prefer? |
|---------|-----------|---------------|---------|
| `const` | No | Yes | Default choice |
| `let` | Yes | Yes | When the value must change |
| `var` | Yes | Function-scoped | Avoid in new code |

---

## Prefer `const`, use `let` when needed

Start with `const`. Switch to `let` only when you must reassign:

```javascript
const users = [];
users.push("Ada"); // OK — the binding is const; the array contents can change

let page = 1;
page = page + 1; // reassignment requires let
```

`const` protects the **binding** (the name → value link), not deep immutability of objects/arrays.

---

## Naming

Use clear, descriptive names:

```javascript
// Good
const isLoggedIn = true;
const maxRetries = 3;
let activeUserId = null;

// Avoid
const x = true;
const n = 3;
```

Conventions in JS:

- `camelCase` for variables and functions
- `UPPER_SNAKE_CASE` for true constants (config flags, magic numbers you treat as fixed)
- Meaningful names over abbreviations

---

## Reassignment vs mutation

```javascript
let score = 10;
score = 20; // reassignment

const settings = { theme: "dark" };
settings.theme = "light"; // mutation — allowed with const
```

In React you will often create **new** objects/arrays instead of mutating, but that is a later pattern. Here, know the language rule: `const` ≠ frozen object.

---

## Temporal Dead Zone (brief)

`let` and `const` are block-scoped and exist in a **temporal dead zone** from the start of the block until the declaration runs. Accessing them too early throws:

```javascript
{
  // console.log(title); // ReferenceError — TDZ
  const title = "EP";
  console.log(title); // "EP"
}
```

`var` is hoisted and initialized as `undefined`, which hides bugs. That is one reason modern code prefers `let`/`const`.

---

## Why avoid `var`

```javascript
if (true) {
  var legacy = "visible outside";
}
console.log(legacy); // works — function-scoped, surprising

if (true) {
  let modern = "block only";
}
// console.log(modern); // ReferenceError
```

Prefer `let`/`const` for predictable block scope.

---

# Common Mistakes

❌ Using `var` by default from old tutorials.

❌ Using `let` for every variable even when never reassigned.

❌ Assuming `const` makes objects immutable.

❌ Accessing `let`/`const` before their declaration.

---

# Best Practices

- Default to `const`; use `let` only for reassignment.
- Never introduce `var` in new EP code.
- Name variables for intent (`isLoading`, not `flag`).
- Declare variables close to where you use them.

---

# Interview Questions

1. What is the difference between `let`, `const`, and `var`?
2. When should you use `const` vs `let`?
3. Can you mutate an object declared with `const`? Why?
4. What is the temporal dead zone?
5. Why is `var` discouraged in modern JavaScript?

---

# Summary

Use `const` by default and `let` when reassignment is required. Avoid `var`. Clear naming and an awareness of block scope (and the TDZ) prevent entire classes of beginner bugs—and prepare you for React state and props patterns.

---

# Navigation

⬅️ Previous: [JS-FND-001 — What is JavaScript?](JS-FND-001-what-is-javascript.md)

⬆️ Module: [Basics](README.md)

➡️ Next: [JS-FND-003 — Data Types](JS-FND-003-data-types.md)
