# Objects and Arrays

> Module: JavaScript Objects · Brand: **EP**
>
> Reading Time: 15–20 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-OBJ-001

---

# Overview

Objects store keyed properties. Arrays store ordered lists. Together they model almost every piece of application data you’ll pass into React: users, products, form fields, and UI lists.

---

# Why This Matters

React lists use arrays. Component props are objects. State updates often create new objects/arrays. If objects and arrays feel natural, React data flow feels natural.

---

# Learning Objectives

After this article, you'll be able to:

- Create object literals and access properties.
- Create arrays and read/update elements.
- Use `map`, `filter`, and `find` for common transforms.
- Apply a light form of destructuring.

---

# Core Concepts

## Object literals

```javascript
const user = {
  name: "Ada",
  role: "Engineer",
  isActive: true,
};
```

### Property access

```javascript
user.name;      // "Ada" — dot notation
user["role"];   // "Engineer" — bracket notation

const key = "isActive";
user[key];      // true — dynamic keys need brackets
```

### Nested objects

```javascript
const lesson = {
  id: "JS-OBJ-001",
  meta: { brand: "EP", level: "beginner" },
};

lesson.meta.brand; // "EP"
```

### Shorthand and methods

```javascript
const name = "Ada";
const user = {
  name, // shorthand for name: name
  greet() {
    return `Hi, ${this.name}`;
  },
};
```

---

## Arrays

```javascript
const skills = ["javascript", "react", "node"];

skills[0];          // "javascript"
skills.length;      // 3
skills.push("css"); // add to end
```

Arrays are ordered and zero-indexed. They are reference types (see Data Types).

---

## Essential array methods

These three appear constantly in React list rendering and data prep.

### `map` — transform each item

```javascript
const nums = [1, 2, 3];
const doubled = nums.map((n) => n * 2);
// [2, 4, 6]
```

In React: `items.map((item) => <Row key={item.id} {...item} />)`.

### `filter` — keep items that match

```javascript
const nums = [1, 2, 3, 4];
const evens = nums.filter((n) => n % 2 === 0);
// [2, 4]
```

### `find` — first match (or `undefined`)

```javascript
const users = [
  { id: 1, name: "Ada" },
  { id: 2, name: "Grace" },
];

const grace = users.find((u) => u.id === 2);
// { id: 2, name: "Grace" }
```

`map` / `filter` return **new arrays** (they do not mutate the original). That immutability-friendly behavior aligns well with React state updates.

---

## Destructuring (light intro)

Pull values out of objects/arrays into variables:

```javascript
const user = { name: "Ada", role: "Engineer" };
const { name, role } = user;

const skills = ["js", "react"];
const [first, second] = skills;
```

In React you’ll see this constantly:

```javascript
function Avatar({ name, src }) {
  // props object destructured in the parameter list
}
```

More destructuring patterns appear in the ES6 article.

---

## Spreading a taste (preview)

Copying into a new object/array (full detail in ES6):

```javascript
const nextUser = { ...user, role: "Mentor" };
const nextSkills = [...skills, "typescript"];
```

---

# Common Mistakes

❌ Mutating arrays/objects in place when a new copy was intended.

❌ Using `map` when you only needed `forEach` (or vice versa).

❌ Forgetting that `find` returns `undefined` when nothing matches.

❌ Accessing nested properties without checking they exist (see optional chaining later).

---

# Best Practices

- Model entities as objects; collections as arrays of objects with stable `id`s.
- Prefer `map` / `filter` / `find` for readable data transforms.
- Destructure props and config objects for clarity.
- Avoid deep mutation; favor new objects/arrays when updating state-like data.

---

# Interview Questions

1. How do dot notation and bracket notation differ for object access?
2. What does `array.map` return?
3. When would you use `filter` vs `find`?
4. What is object destructuring?
5. Why do React list renders typically use `map`?

---

# Summary

Objects group named data; arrays hold ordered collections. `map`, `filter`, and `find` cover most day-one transforms. Light destructuring cleans up access patterns and foreshadows React props. Next: modern ES6 syntax React assumes you know.

---

# Navigation

⬅️ Previous: [JS-FUN-001 — Functions Essentials](../02-functions/JS-FUN-001-functions-essentials.md)

⬆️ Module: [Objects](README.md)

➡️ Next: [JS-ES6-001 — ES6 Essentials](../04-es6/JS-ES6-001-es6-essentials.md)
