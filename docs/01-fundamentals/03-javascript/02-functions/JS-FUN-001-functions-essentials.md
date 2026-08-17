# Functions Essentials

> Module: JavaScript Functions · Brand: **EP**
>
> Reading Time: 15–20 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-FUN-001

---

# Overview

A function is a named (or anonymous) block of code you can call with inputs and optionally get a return value. Mastering functions is non-negotiable before React: **React components are functions that return UI descriptions**.

---

# Why This Matters

Without functions, code repeats and becomes hard to test. With functions, you isolate behavior—exactly how React isolates UI into components and handlers.

---

# Learning Objectives

After this article, you'll be able to:

- Write function declarations, expressions, and arrow functions.
- Use parameters and return values.
- Pass a function as a callback.
- Explain why functions matter for React components later.

---

# Core Concepts

## Function declaration

```javascript
function greet(name) {
  return `Hello, ${name}`;
}

console.log(greet("EP")); // "Hello, EP"
```

Declarations are hoisted (you can call them before the line they appear). Prefer clarity of order anyway.

---

## Function expression

```javascript
const greet = function (name) {
  return `Hello, ${name}`;
};
```

The function is stored in a variable. It is not hoisted like a declaration.

---

## Arrow functions

```javascript
const greet = (name) => {
  return `Hello, ${name}`;
};

// Concise body — implicit return
const double = (n) => n * 2;
```

Arrow functions are common in React (handlers, `.map` callbacks). They also have different `this` behavior than traditional functions—important later; for now, use them as compact function values.

```javascript
const add = (a, b) => a + b;
```

---

## Parameters and return

```javascript
function createUser(name, role = "learner") {
  return {
    name,
    role,
  };
}

const user = createUser("Ada");
// { name: "Ada", role: "learner" }
```

- Parameters are inputs.
- Default parameters fill in when an argument is `undefined`.
- `return` exits and sends a value back; without `return`, the result is `undefined`.

---

## Callbacks (intro)

A **callback** is a function passed into another function to be called later:

```javascript
function withLog(fn) {
  console.log("before");
  fn();
  console.log("after");
}

withLog(() => {
  console.log("doing work");
});
```

Array methods and browser events use callbacks heavily:

```javascript
[1, 2, 3].forEach((n) => {
  console.log(n);
});
```

In React you will pass callbacks as props (e.g. `onClick={handleClick}`).

---

## Why functions matter for React later

A simple React component looks like a function:

```javascript
function Welcome({ name }) {
  return <h1>Hello, {name}</h1>;
}
```

Even before JSX:

```javascript
function Welcome(props) {
  return "Hello, " + props.name;
}
```

Mental model:

```text
function → inputs (props) → output (UI)
event handler → function called on user action
```

If you are comfortable writing and composing functions, React’s component model feels natural.

---

# Common Mistakes

❌ Forgetting `return` and wondering why you get `undefined`.

❌ Confusing calling `fn` with passing `fn` (callbacks need the function, not always the result).

❌ Overusing nested arrow functions until readability collapses.

❌ Treating React components as magical—they are still JS functions.

---

# Best Practices

- Name functions for verbs/intent (`fetchUser`, `formatDate`).
- Keep functions focused (one job).
- Prefer arrow functions for short callbacks; declarations for top-level named APIs is fine.
- Return early to reduce deep nesting.

---

# Interview Questions

1. What is the difference between a function declaration and a function expression?
2. What is an arrow function, and when is it commonly used?
3. What is a callback function?
4. What does a function return if there is no `return` statement?
5. How do React components relate to JavaScript functions?

---

# Summary

Functions declare reusable behavior with parameters and returns. Declarations, expressions, and arrows are the three styles you’ll see daily. Callbacks unlock events and array methods—and prepare you for React components and handlers next to objects and arrays.

---

# Navigation

⬅️ Previous: [JS-FND-004 — Operators and Control Flow](../01-basics/JS-FND-004-operators-and-control-flow.md)

⬆️ Module: [Functions](README.md)

➡️ Next: [JS-OBJ-001 — Objects and Arrays](../03-objects/JS-OBJ-001-objects-and-arrays.md)
