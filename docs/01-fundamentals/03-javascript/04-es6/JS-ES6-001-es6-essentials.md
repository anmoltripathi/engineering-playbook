# ES6 Essentials

> Module: JavaScript ES6 · Brand: **EP**
>
> Reading Time: 15–20 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-ES6-001

---

# Overview

This article is a **React-focused** tour of modern JavaScript syntax. You do not need every ES feature—just the ones that appear constantly in components, props, and modules.

---

# Why This Matters

Most React examples use ES6+ without explanation. If template literals, destructuring, and spread feel foreign, React looks harder than it is. Learn these once; reuse them everywhere in EP.

---

# Learning Objectives

After this article, you'll be able to:

- Write template literals.
- Destructure objects and arrays confidently.
- Use spread and rest.
- Explain `import` / `export` at a high level.
- Use optional chaining (`?.`) and nullish coalescing (`??`).

---

# Core Concepts

## Template literals

Backticks allow interpolation and multi-line strings:

```javascript
const brand = "EP";
const message = `Welcome to ${brand}`;

const htmlHint = `
  <section>
    <h1>${brand}</h1>
  </section>
`;
```

In React you’ll still use JSX for UI, but template literals remain useful for URLs, messages, and className helpers.

---

## Destructuring

```javascript
const user = { name: "Ada", role: "Engineer", city: "London" };

const { name, role } = user;
const { city: location } = user; // rename

const pair = ["js", "react"];
const [lang, lib] = pair;
```

### Defaults

```javascript
const { theme = "light" } = settings;
```

### Function parameters (very React)

```javascript
function UserCard({ name, role }) {
  return `${name} — ${role}`;
}
```

---

## Spread and rest

### Spread — expand into place

```javascript
const base = { brand: "EP", level: "beginner" };
const lesson = { ...base, id: "JS-ES6-001" };

const a = [1, 2];
const b = [...a, 3]; // [1, 2, 3]
```

Immutable-style updates:

```javascript
const next = { ...user, role: "Mentor" };
```

### Rest — collect the remainder

```javascript
const { id, ...rest } = lesson;
// id isolated; rest has the other properties

function sum(...nums) {
  return nums.reduce((total, n) => total + n, 0);
}
```

---

## Modules: `import` / `export` (overview)

Modern apps split code into files (modules).

```javascript
// math.js
export function add(a, b) {
  return a + b;
}

export const brand = "EP";

export default function multiply(a, b) {
  return a * b;
}
```

```javascript
// app.js
import multiply, { add, brand } from "./math.js";
```

| Style | Syntax |
|-------|--------|
| Named export | `export function add` → `import { add }` |
| Default export | `export default` → `import multiply` |

React components are typically default- or named-exported from their files. Bundlers (Vite, etc.) understand this syntax.

---

## Optional chaining (`?.`)

Safely access nested values without crashing on `null` / `undefined`:

```javascript
const user = { profile: { email: "ada@ep.dev" } };

user.profile?.email;   // "ada@ep.dev"
user.address?.city;    // undefined (no throw)
user.prefs?.theme?.id; // undefined
```

Also works for calls:

```javascript
api.getUser?.();
```

---

## Nullish coalescing (`??`)

Provide a fallback only when the left side is `null` or `undefined` (not other falsy values):

```javascript
const count = 0;

count || 10; // 10 — bad if 0 is valid
count ?? 10; // 0  — keeps valid 0
```

```javascript
const title = inputTitle ?? "Untitled";
```

Combine with optional chaining:

```javascript
const theme = user.settings?.theme ?? "light";
```

---

# Common Mistakes

❌ Using `||` for defaults when `0` or `""` are valid.

❌ Spreading without understanding you get a shallow copy.

❌ Mixing up default vs named imports.

❌ Optional-chaining so deeply that missing data stays silent too long.

---

# Best Practices

- Prefer `??` over `||` for default values.
- Use spread for shallow immutable updates.
- Keep one React component export style consistent per project.
- Destructure props at the function boundary for readability.

---

# Interview Questions

1. What problem do template literals solve?
2. What is the difference between spread and rest?
3. Named export vs default export—what’s the difference?
4. When should you use `??` instead of `||`?
5. What does optional chaining do when a mid-chain value is `null`?

---

# Summary

ES6 essentials—templates, destructuring, spread/rest, modules, `?.`, and `??`—are the dialect of modern React. With these, you can read most beginner React code. Next: a light look at the DOM so you understand what React abstracts.

---

# Navigation

⬅️ Previous: [JS-OBJ-001 — Objects and Arrays](../03-objects/JS-OBJ-001-objects-and-arrays.md)

⬆️ Module: [ES6](README.md)

➡️ Next: [JS-BRW-001 — DOM Basics](../06-browser/JS-BRW-001-dom-basics.md)
