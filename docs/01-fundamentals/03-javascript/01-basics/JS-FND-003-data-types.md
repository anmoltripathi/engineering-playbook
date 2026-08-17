# Data Types

> Module: JavaScript Basics · Brand: **EP**
>
> Reading Time: 12–18 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-FND-003

---

# Overview

Every value in JavaScript has a type. Types fall into two groups: **primitives** (copied by value) and **references** (objects and arrays, shared by reference). Understanding this split prevents subtle bugs with comparison, updates, and React state later.

---

# Why This Matters

React components pass props and store state as JavaScript values. Knowing whether you hold a string or an object—and whether assignment copies or shares—explains bugs like “I changed one variable and another changed too.”

---

# Learning Objectives

After this article, you'll be able to:

- List the main primitive types.
- Contrast primitives with objects/arrays.
- Use `typeof` appropriately (and know its quirks).
- Explain pass-by-value vs pass-by-reference at a practical level.

---

# Core Concepts

## Primitive vs reference

| Kind | Examples | Assignment copies… |
|------|----------|--------------------|
| **Primitive** | string, number, boolean, null, undefined, symbol, bigint | the value itself |
| **Reference** | object, array, function, date, etc. | a reference to the same data |

```javascript
let a = 10;
let b = a;
b = 20;
console.log(a); // 10 — primitives are independent

const user1 = { name: "Ada" };
const user2 = user1;
user2.name = "Grace";
console.log(user1.name); // "Grace" — same object in memory
```

---

## Primitives (brief tour)

### string

Text:

```javascript
const title = "Engineering Playbook";
const brand = "EP";
```

### number

Integers and floats (IEEE-754 doubles under the hood):

```javascript
const lessons = 8;
const pi = 3.14;
```

### boolean

`true` or `false` — used heavily in conditionals and React rendering.

```javascript
const isReady = true;
```

### null

Intentional empty value (“we know there is nothing here”).

```javascript
let selectedItem = null;
```

### undefined

Declared but not assigned, or missing property/return.

```javascript
let score;
console.log(score); // undefined
```

### symbol

Unique identifiers (less common early on; used in advanced APIs).

```javascript
const id = Symbol("user");
```

### bigint

Integers beyond `Number.MAX_SAFE_INTEGER`:

```javascript
const big = 9007199254740993n;
```

---

## `typeof`

```javascript
typeof "EP";        // "string"
typeof 42;          // "number"
typeof true;        // "boolean"
typeof undefined;   // "undefined"
typeof null;        // "object"  ← historic quirk
typeof {};          // "object"
typeof [];          // "object"
typeof function () {}; // "function"
```

Check arrays with `Array.isArray(value)`, not `typeof`.

```javascript
Array.isArray([1, 2, 3]); // true
Array.isArray({ a: 1 });  // false
```

---

## Objects and arrays as references

Objects group named properties. Arrays are ordered lists (also objects under the hood).

```javascript
const profile = {
  name: "Ada",
  role: "Engineer",
};

const skills = ["js", "react", "node"];
```

Updating through another variable mutates the same underlying data. For React state updates you will usually create a **new** object/array so React can detect change—that pattern builds on this foundation.

---

## Equality preview

Primitives compare by value; objects compare by reference:

```javascript
console.log(1 === 1);           // true
console.log({ a: 1 } === { a: 1 }); // false — different objects
```

Prefer `===` over `==` (covered more in the next article).

---

# Common Mistakes

❌ Expecting `typeof null` to be `"null"`.

❌ Using `typeof` to detect arrays.

❌ Assuming copying an object variable clones the object.

❌ Confusing `null` (intentional empty) with `undefined` (missing).

---

# Best Practices

- Treat objects/arrays as shared unless you intentionally copy.
- Use `Array.isArray` for array checks.
- Prefer `null` for “empty on purpose,” leave `undefined` for “not set.”
- Learn immutability patterns before heavy React state work.

---

# Interview Questions

1. What is the difference between primitive and reference types?
2. What are the seven primitive types in modern JavaScript?
3. What does `typeof null` return, and why is that surprising?
4. How do you correctly check if a value is an array?
5. Why can changing `user2.name` also change `user1.name`?

---

# Summary

Primitives are copied by value; objects and arrays are shared by reference. Know the main types, use `typeof` carefully, and use `Array.isArray` for arrays. This mental model is essential before functions, ES6 copying patterns, and React state.

---

# Navigation

⬅️ Previous: [JS-FND-002 — Variables](JS-FND-002-variables.md)

⬆️ Module: [Basics](README.md)

➡️ Next: [JS-FND-004 — Operators and Control Flow](JS-FND-004-operators-and-control-flow.md)
