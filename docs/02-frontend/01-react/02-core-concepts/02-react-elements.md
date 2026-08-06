# React Elements

> Module: React Core Concepts
>
> Reading Time: 45–60 Minutes
>
> Difficulty: 🟢 Beginner → 🟡 Intermediate

---

> **📍 Location**
>
> Engineering Playbook
>
> → Docs
>
> → Frontend
>
> → React
>
> → Core Concepts
>
> → React Elements

---

# Overview

In the previous chapter, you learned that JSX is not HTML.

Instead, JSX is transformed into JavaScript before it reaches the browser.

But what exactly does JSX become?

The answer is **React Elements**.

Every JSX tag you write eventually becomes a React Element.

React Elements are one of the most fundamental concepts in React because they describe what the user interface should look like.

Understanding React Elements will help you understand:

- Components
- Rendering
- Virtual DOM
- Reconciliation
- React Fiber

Every React application is ultimately built from React Elements.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | React Elements |
| Level | Beginner → Intermediate |
| Reading Time | 45–60 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 60 Minutes |
| Prerequisites | JSX |
| Next Topic | Components |

---

# Why This Matters

When developers first learn React, it's easy to think:

```text
JSX

↓

HTML

↓

Browser
```

But that isn't what happens.

The real flow is:

```text
JSX

↓

React Element

↓

Virtual DOM

↓

Browser DOM
```

React never works directly with HTML.

Instead, it works with React Elements.

Understanding this distinction is essential for mastering React's rendering model.

---

# Learning Objectives

After completing this article, you'll be able to:

- Explain what a React Element is.
- Understand how JSX creates React Elements.
- Distinguish React Elements from DOM Elements.
- Explain why React Elements are immutable.
- Understand how React uses React Elements during rendering.
- Prepare for learning Components and Rendering.

---

# What is a React Element?

A React Element is a lightweight JavaScript object that describes a piece of the user interface.

It is **not**:

- HTML
- A DOM node
- A browser element

Instead, it is simply a description of what should appear on the screen.

Think of a React Element as a blueprint.

It describes the UI.

It does not create the UI itself.

---

# A Mental Model

Imagine an architect designing a house.

```text
Blueprint

↓

Construction

↓

House
```

The blueprint is not the house.

It merely describes the house.

React works the same way.

```text
React Element

↓

Rendering

↓

DOM

↓

Visible UI
```

The React Element describes the interface.

React builds the actual interface later.

---

# JSX Creates React Elements

Consider the following JSX:

```jsx
<h1>Hello React</h1>
```

During compilation it becomes:

```javascript
React.createElement(
    "h1",
    null,
    "Hello React"
);
```

That function returns a React Element.

Conceptually:

```javascript
{
    type: "h1",
    props: {
        children: "Hello React"
    }
}
```

This object describes:

- which element to create
- its properties
- its children

Nothing has been rendered yet.

---

# Anatomy of a React Element

Although you rarely create React Elements manually, understanding their structure helps explain many React concepts such as rendering, reconciliation, keys, and component updates.

A React Element is simply a JavaScript object with a predefined structure.

Conceptually, it looks like this:

```javascript
{
    type: "h1",
    key: null,
    ref: null,
    props: {
        children: "Hello React"
    }
}
```

Don't worry if every property isn't clear yet.

We'll explore each one individually.

---

# The `type` Property

The `type` property tells React **what should be rendered**.

It can represent:

- An HTML element
- A React Component

Example:

```jsx
<h1>Hello</h1>
```

becomes

```javascript
{
    type: "h1"
}
```

Here, React knows it must create an `<h1>` element.

---

Now consider:

```jsx
<Button />
```

Conceptually:

```javascript
{
    type: Button
}
```

Instead of a string, the type is now a JavaScript function (the component).

This is how React knows whether it should render a native HTML element or execute another component.

---

# The `props` Property

Every React Element contains a `props` object.

Props store all information passed to the element.

Example:

```jsx
<img
    src="/logo.png"
    alt="Engineering Playbook"
/>
```

Conceptually:

```javascript
{
    type: "img",
    props: {
        src: "/logo.png",
        alt: "Engineering Playbook"
    }
}
```

Every attribute written in JSX becomes part of the `props` object.

---

# The `children` Property

Children are stored inside `props`.

Example:

```jsx
<h1>Hello React</h1>
```

Conceptually:

```javascript
{
    props: {
        children: "Hello React"
    }
}
```

Nested elements also become children.

```jsx
<div>

    <h1>Title</h1>

    <p>Description</p>

</div>
```

Conceptually:

```text
div

├── h1

└── p
```

React recursively builds this hierarchy for the entire application.

---

# The `key` Property

Keys help React identify elements inside collections.

Example:

```jsx
users.map(user =>

    <UserCard
        key={user.id}
        user={user}
    />

)
```

Conceptually:

```javascript
{
    key: 42
}
```

Keys are **not available as props**.

Instead, React uses them internally during reconciliation.

You'll learn about keys in detail later in this module.

---

# The `ref` Property

Refs provide direct access to DOM elements or component instances.

Example:

```jsx
<input ref={inputRef} />
```

Conceptually:

```javascript
{
    ref: inputRef
}
```

Like keys, refs are handled internally by React.

We'll study them in the Hooks module.

---

# React Elements are Immutable

One of the most important properties of React Elements is that they are **immutable**.

Once created, a React Element never changes.

Example:

```jsx
const title = <h1>Hello</h1>;
```

The element above cannot be modified.

Instead of changing an existing element, React creates a **new React Element**.

Conceptually:

```text
Old Element

↓

New State

↓

Create New Element

↓

Compare

↓

Update DOM
```

Immutability makes React's rendering model predictable and efficient.

---

# React Elements Form a Tree

Every application is ultimately a tree of React Elements.

Example:

```jsx
<App />
```

might produce:

```text
App

├── Header

│   ├── Logo

│   └── Navigation

│

├── Main

│   ├── Sidebar

│   └── Content

│

└── Footer
```

Each box in this tree represents another React Element.

This tree becomes the foundation for rendering and reconciliation.

---

# React Element vs DOM Element

These two concepts are often confused.

| React Element | DOM Element |
|---------------|-------------|
| JavaScript Object | Browser Object |
| Lightweight | Heavy |
| Immutable | Mutable |
| Created by React | Created by Browser |
| Virtual | Real |

Flow:

```text
React Element

↓

React DOM

↓

Browser DOM Element
```

A React Element describes the UI.

A DOM Element is the actual object displayed by the browser.

---

# React Element vs Component

Another common misunderstanding.

A Component is **not** a React Element.

A component is a JavaScript function.

Example:

```jsx
function Welcome() {

    return <h1>Hello</h1>;

}
```

Here:

```text
Welcome

↓

Function
```

When React executes it:

```text
Welcome()

↓

Returns

↓

React Element
```

A useful mental model:

```text
Component

↓

Creates

↓

React Elements

↓

React renders them
```

Components create React Elements.

React Elements describe the UI.

React renders the UI.

---

# Complete Flow

Let's connect everything you've learned.

```text
Developer

↓

Writes JSX

↓

Compiler

↓

React.createElement()

↓

React Element

↓

React executes Components

↓

Element Tree

↓

Rendering

↓

Virtual DOM

↓

Browser DOM

↓

User Interface
```

This is the complete lifecycle from source code to visible UI.

---

# Engineering Perspective

React Elements are intentionally lightweight and immutable.

They are not designed to manipulate the DOM directly.

Instead, they serve as declarative descriptions of the interface.

This separation allows React to compare two UI descriptions, determine what changed, and update only the necessary parts of the browser DOM.

Understanding React Elements is essential because nearly every advanced React concept—including rendering, reconciliation, Hooks, and Fiber—builds upon them.

---

# Best Practices

When working with React Elements, keep the following principles in mind.

## Think Declaratively

A React Element describes **what** should appear on the screen.

Avoid thinking in terms of manually creating or updating DOM nodes.

Instead, describe the desired UI and let React determine how to update the browser efficiently.

---

## Don't Modify React Elements

React Elements are immutable.

Instead of trying to change an existing element:

```jsx
const heading = <h1>Hello</h1>;
```

Create a new one.

React is optimized for creating and comparing new elements.

---

## Keep Components Small

Components should return a clear hierarchy of React Elements.

Instead of one massive component:

```text
Dashboard

↓

500 Lines

↓

Hard to Understand
```

Prefer:

```text
Dashboard

├── Header

├── Sidebar

├── Content

└── Footer
```

Each component returns its own React Element tree.

---

## Understand the Difference Between Components and Elements

Remember:

```text
Component

↓

Returns

↓

React Element

↓

React Renders
```

Don't use these terms interchangeably.

They solve different problems.

---

# Common Mistakes

## Mistake 1

Thinking React Elements are HTML.

❌ Incorrect

```text
JSX

↓

HTML
```

✅ Correct

```text
JSX

↓

React Element

↓

DOM
```

---

## Mistake 2

Thinking Components and Elements are the same.

Components create React Elements.

React Elements describe the UI.

---

## Mistake 3

Trying to modify a React Element.

Incorrect mindset:

```text
React Element

↓

Modify

↓

Reuse
```

Correct mindset:

```text
State Changes

↓

Create New Element

↓

React Compares

↓

Update DOM
```

---

## Mistake 4

Thinking React Elements are DOM nodes.

A DOM node exists inside the browser.

A React Element exists only as a JavaScript object.

---

# Real-World Example

Consider a simple navigation bar.

```jsx
<Navbar />

↓

<nav>

↓

<ul>

↓

<li>Home</li>

<li>Courses</li>

<li>About</li>

</ul>
```

This isn't one React Element.

It's an entire hierarchy of React Elements.

Conceptually:

```text
Navbar

↓

nav

↓

ul

├── li

├── li

└── li
```

React builds and manages this hierarchy internally before updating the browser.

---

# Interview Questions

## Beginner

### 1. What is a React Element?

---

### 2. Is JSX a React Element?

---

### 3. What does `React.createElement()` return?

---

### 4. Is a React Element the same as a DOM Element?

---

### 5. Are React Elements mutable?

---

## Intermediate

### 6. Explain the lifecycle of a React Element from JSX to the browser.

---

### 7. Why are React Elements immutable?

---

### 8. What is stored inside a React Element?

---

### 9. What is the purpose of the `type` property?

---

### 10. What is the relationship between Components and React Elements?

---

## Advanced

### 11. Why does React create new React Elements instead of modifying existing ones?

---

### 12. How do React Elements help Reconciliation?

---

### 13. How does the immutability of React Elements improve React's rendering performance?

---

### 14. Why does React separate React Elements from DOM Elements?

---

# Hands-on Exercises

## Exercise 1

Create a JSX element.

Inspect its compiled output.

Identify:

- type
- props
- children

---

## Exercise 2

Create a nested component hierarchy.

Example:

```text
App

↓

Header

↓

Navigation

↓

Menu Item
```

Draw the corresponding React Element Tree.

---

## Exercise 3

Compare:

```jsx
<h1>Hello</h1>
```

and

```javascript
React.createElement(
    "h1",
    null,
    "Hello"
);
```

Explain why both produce the same result.

---

## Exercise 4

Take a simple webpage.

Convert every HTML element into React Elements conceptually.

---

# Summary

In this chapter, you learned that React Elements are lightweight, immutable JavaScript objects that describe user interfaces.

You discovered that:

- JSX creates React Elements.
- React Elements are not DOM nodes.
- Components return React Elements.
- React builds an Element Tree before rendering.
- React compares new and old Element Trees during updates.

These concepts form the foundation for React's rendering architecture.

Understanding React Elements makes it much easier to understand Components, Rendering, Virtual DOM, and Reconciliation.

---

# Knowledge Check

Before moving on, verify that you can answer the following questions.

- What is a React Element?
- Is JSX executed by the browser?
- What does `React.createElement()` return?
- What is stored inside a React Element?
- Why are React Elements immutable?
- What is the difference between a Component and a React Element?
- What is the difference between a React Element and a DOM Element?

If you can confidently answer these questions, you're ready for the next chapter.

---

# Further Reading

- 📖 Components
- 📖 Rendering
- 📖 Virtual DOM

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← JSX | ↑ React Core Concepts | 🗺 Module Home | Components → |

---

# Continue Your Journey

You've learned how React represents user interfaces internally using **React Elements**.

Next, you'll learn about **Components**, the reusable building blocks that generate React Elements and make modern React applications modular, maintainable, and scalable.

- ⬅ **Previous:** [01 - JSX](01-jsx.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [03 - Components](03-components.md)