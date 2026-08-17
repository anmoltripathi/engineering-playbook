# DOM Basics

> Module: JavaScript Browser · Brand: **EP**
>
> Reading Time: 12–18 Minutes
>
> Difficulty: 🟢 Beginner
>
> ID: JS-BRW-001

---

# Overview

The **DOM** (Document Object Model) is the browser’s tree representation of a web page. JavaScript can query nodes, change text and attributes, create elements, and listen for events. React builds on this model—but usually you do not manipulate the DOM by hand.

---

# Why This Matters

Understanding the DOM explains *what* React is abstracting. When tutorials say “React updates the DOM efficiently,” you should know what that means at a high level—even if day-to-day you write components, not `querySelector` calls.

---

# Learning Objectives

After this article, you'll be able to:

- Describe what the DOM is.
- Select elements with `querySelector`.
- Create elements and set `textContent`.
- Attach events with `addEventListener`.
- Explain why React abstracts direct DOM manipulation.

---

# Core Concepts

## What the DOM is

HTML is text. The browser parses it into a tree of nodes (elements, text, etc.):

```text
document
  └── html
        ├── head
        └── body
              ├── h1
              └── button
```

JavaScript talks to that live tree through the DOM API (`document`, element methods, events).

---

## Selecting elements

```javascript
const title = document.querySelector("h1");
const button = document.querySelector("#save");
const items = document.querySelectorAll(".item");
```

| Method | Returns |
|--------|---------|
| `querySelector` | First match (or `null`) |
| `querySelectorAll` | List of matches |

CSS selectors work: `#id`, `.class`, `tag`, `[attr]`, etc.

---

## Creating and updating nodes

```javascript
const el = document.createElement("p");
el.textContent = "Hello from EP";
document.body.appendChild(el);
```

Prefer `textContent` for plain text (avoids interpreting HTML). Use `innerHTML` only when you intentionally need HTML and trust the content.

```javascript
title.textContent = "Engineering Playbook";
```

---

## Events with `addEventListener`

```javascript
const button = document.querySelector("#save");

button.addEventListener("click", () => {
  console.log("clicked");
});
```

Common events: `click`, `input`, `submit`, `keydown`.

Handlers are callbacks—the same idea from Functions Essentials.

---

## A tiny vanilla example

```html
<button id="counter">Count: 0</button>
<script>
  let count = 0;
  const button = document.querySelector("#counter");

  button.addEventListener("click", () => {
    count += 1;
    button.textContent = `Count: ${count}`;
  });
</script>
```

This works—but as UIs grow, manual updates scatter across listeners and become hard to maintain.

---

## Why React abstracts this

Vanilla DOM code mixes **what the UI should look like** with **how to update nodes**.

React’s approach:

1. You describe UI as a function of state (components).
2. When state changes, React computes what should change.
3. React updates the DOM for you (via its reconciler / renderer).

```text
State change → React re-render → minimal DOM updates
```

You still need DOM literacy for:

- Understanding browser behavior and accessibility
- Integrating non-React libraries
- Debugging (inspecting elements in DevTools)
- Rare escape hatches (`ref` to a DOM node)

For EP’s React path, keep vanilla DOM **light**—know the ideas, then prefer components.

---

# Common Mistakes

❌ Updating the DOM in many places without a single source of truth.

❌ Using `innerHTML` with untrusted user input (XSS risk).

❌ Forgetting that `querySelector` can return `null`.

❌ Learning only React and never opening DevTools Elements panel.

---

# Best Practices

- Know selectors and events; don’t build large apps via manual DOM if React is the stack.
- Prefer `textContent` for plain text updates.
- Null-check query results before use.
- Use browser DevTools to inspect the live DOM while learning React.

---

# Interview Questions

1. What is the DOM?
2. What does `document.querySelector` return when nothing matches?
3. Why prefer `textContent` over `innerHTML` for plain text?
4. How do you listen for a button click in vanilla JS?
5. Why does React abstract direct DOM manipulation?

---

# Summary

The DOM is the browser’s live document tree. You can select nodes, create elements, set text, and listen for events. React sits above this layer so you describe UI declaratively instead of micromanaging updates. With this React-Ready Path complete, you are ready for React Fundamentals.

---

# Navigation

⬅️ Previous: [JS-ES6-001 — ES6 Essentials](../04-es6/JS-ES6-001-es6-essentials.md)

⬆️ Module: [Browser](README.md)

➡️ Next: [React Fundamentals](../../../02-frontend/01-react/01-react-fundamentals/README.md)

🗺 Path home: [React-Ready Path](../00-react-ready-path.md)
