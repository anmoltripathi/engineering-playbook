# JSX

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
> → JSX

---

# Overview

JSX is the first React concept that every developer encounters.

At first glance, JSX looks like HTML written inside JavaScript.

However, JSX is **not HTML**, and it is **not a template language**.

JSX is a JavaScript syntax extension that allows developers to describe user interfaces using a syntax that is easier to read and write than manually creating React Elements.

Although it resembles HTML, JSX is compiled into JavaScript before the browser executes your application.

Understanding JSX is essential because almost every React component you write will return JSX.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | JSX |
| Level | Beginner → Intermediate |
| Reading Time | 45–60 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 60–90 Minutes |
| Prerequisites | React Fundamentals |
| Next Topic | React Elements |

---

# Why This Matters

Without JSX, building React applications would require manually creating every UI element using JavaScript function calls.

For example, creating a simple heading would look significantly more verbose.

JSX provides a cleaner, more declarative way to describe user interfaces.

Instead of telling React **how** to construct the UI, you describe **what** the UI should look like.

This improves readability, maintainability, and developer productivity.

---

# Learning Objectives

After completing this article, you'll be able to:

- Explain what JSX is.
- Explain why JSX exists.
- Distinguish JSX from HTML.
- Understand how JSX is compiled.
- Write valid JSX.
- Embed JavaScript expressions inside JSX.
- Use fragments correctly.
- Understand JSX attributes.
- Explain the relationship between JSX and React Elements.
- Avoid common JSX mistakes.

---

# What is JSX?

JSX stands for:

> **JavaScript XML**

It is a syntax extension for JavaScript introduced by the React team to simplify the creation of user interfaces.

JSX allows developers to write UI structures using an HTML-like syntax directly within JavaScript code.

For example:

```jsx
function App() {
    return <h1>Hello React</h1>;
}
```

Although this looks like HTML, it is **not HTML**.

The browser never executes JSX directly.

Instead, JSX is transformed into JavaScript during the build process.

---

# JSX is NOT HTML

This is one of the biggest misconceptions among beginners.

JSX resembles HTML because it uses familiar tags and nesting, but it follows JavaScript rules.

For example:

| HTML | JSX |
|------|-----|
| `class` | `className` |
| `for` | `htmlFor` |
| Inline strings | JavaScript expressions |
| Browser parser | JavaScript compiler |

JSX eventually becomes JavaScript objects, not HTML strings.

---

# Why Was JSX Created?

Before JSX, React components were written using `React.createElement()`.

For example:

```javascript
React.createElement(
    "h1",
    null,
    "Hello React"
);
```

As applications became more complex, this style quickly became difficult to read.

JSX was introduced to make component code more expressive and maintainable.

The previous example becomes:

```jsx
<h1>Hello React</h1>
```

Both approaches produce the same result, but JSX is significantly easier to read.

---

# JSX is Syntactic Sugar

JSX is not a new language.

It is simply a different way of writing JavaScript.

The following JSX:

```jsx
<h1>Hello React</h1>
```

is transformed into JavaScript during compilation.

Conceptually:

```text
Developer

↓

Writes JSX

↓

Compiler (Babel / SWC)

↓

React.createElement()

↓

React Element

↓

React renders the UI
```

JSX is therefore often described as **syntactic sugar** for creating React Elements.

---

# JSX Compilation

One of the most important things to understand is that browsers do **not** understand JSX.

When you run a React application:

```text
JSX Source Code

↓

Compiler

↓

JavaScript

↓

Browser
```

The compiler transforms JSX into JavaScript that the browser can execute.

This compilation step happens automatically when using modern tools such as Vite.

---

# JSX vs HTML

Although JSX looks similar to HTML, several important differences exist.

| HTML | JSX |
|------|------|
| `class` | `className` |
| `for` | `htmlFor` |
| Inline styles use CSS strings | Inline styles use JavaScript objects |
| Comments use `<!-- -->` | Comments use `{/* */}` |
| Attribute values are strings | Attribute values can be JavaScript expressions |

These differences exist because JSX follows JavaScript syntax rather than HTML parsing rules.

---

# JSX Expressions

One of JSX's greatest strengths is that it allows you to seamlessly combine JavaScript logic with your user interface.

Unlike HTML, JSX is not limited to static content.

Anything that can be evaluated as a valid JavaScript expression can be embedded directly inside JSX.

This enables React applications to render dynamic user interfaces based on variables, calculations, function calls, and application state.

---

## What is a JavaScript Expression?

A JavaScript expression is any piece of code that produces a value.

Examples include:

```javascript
"Engineering Playbook"

10 + 20

true

user.name

price * quantity

isLoggedIn ? "Logout" : "Login"
```

Each of these evaluates to a single value.

JSX allows these expressions to be inserted directly into the UI.

---

## Using Expressions in JSX

JavaScript expressions are enclosed inside curly braces.

```jsx
const title = "Engineering Playbook";

function App() {
    return (
        <h1>{title}</h1>
    );
}
```

Output:

```text
Engineering Playbook
```

Notice that React replaces the expression with its evaluated value.

---

## Why Curly Braces?

Curly braces tell React:

> "Everything inside this block is JavaScript."

Outside the braces:

```jsx
<h1>Hello</h1>
```

React treats the content as plain text.

Inside the braces:

```jsx
<h1>{message}</h1>
```

React evaluates the JavaScript expression before rendering.

Conceptually:

```text
JSX

↓

Encounter {

↓

Switch to JavaScript

↓

Evaluate Expression

↓

Insert Result

↓

Continue JSX
```

---

# What Can Be Written Inside Curly Braces?

Almost any JavaScript expression can be used.

## Variables

```jsx
const name = "Alex";

<h1>Hello {name}</h1>
```

---

## Numbers

```jsx
const age = 25;

<p>{age}</p>
```

---

## Mathematical Expressions

```jsx
<p>{15 + 25}</p>
```

Output:

```text
40
```

---

## String Concatenation

```jsx
const first = "Engineering";
const second = "Playbook";

<h1>{first + " " + second}</h1>
```

---

## Template Literals

```jsx
const version = 19;

<p>{`React ${version}`}</p>
```

---

## Boolean Expressions

```jsx
const loggedIn = true;

<p>{loggedIn ? "Welcome" : "Please Login"}</p>
```

---

## Function Calls

```jsx
function greet(name) {
    return `Hello ${name}`;
}

<h1>{greet("Alex")}</h1>
```

---

## Object Properties

```jsx
const user = {
    name: "Alex",
    role: "Developer"
};

<p>{user.name}</p>
```

---

## Array Elements

```jsx
const colors = ["Red", "Blue", "Green"];

<p>{colors[1]}</p>
```

Output:

```text
Blue
```

---

# What Cannot Be Written?

JSX only accepts **expressions**, not **statements**.

This is a common source of confusion.

### Invalid

```jsx
{
    if (isLoggedIn) {
        return "Welcome";
    }
}
```

Why?

Because `if` is a statement.

Statements perform actions but do not produce a value.

---

### Valid

```jsx
{
    isLoggedIn
        ? "Welcome"
        : "Login"
}
```

The ternary operator is an expression because it evaluates to a value.

---

# Expressions vs Statements

| Expression | Statement |
|------------|-----------|
| Produces a value | Performs an action |
| Allowed inside JSX | Not allowed inside JSX |
| `user.name` | `if` |
| `price * qty` | `for` |
| `"Hello"` | `while` |
| `condition ? a : b` | `switch` |

Understanding this difference is essential when writing React components.

---

# JSX is Still JavaScript

A useful mental model is:

```text
JSX

=

HTML-like Syntax

+

JavaScript Expressions
```

React does not create a new programming language.

It extends JavaScript with a more expressive way to describe user interfaces.

Whenever you encounter curly braces, remember:

```text
React

↓

Exit JSX

↓

Execute JavaScript

↓

Return Result

↓

Continue Rendering
```

---

# Engineering Perspective

Many developers initially think of JSX as "HTML inside JavaScript."

A more accurate way to think about it is:

> **JSX is JavaScript that describes a user interface.**

The HTML-like syntax exists only to improve readability.

Behind the scenes, every JSX element becomes a JavaScript object representing part of your application's UI.

This distinction becomes increasingly important when learning React Elements, Rendering, and Reconciliation in the following chapters.

# JSX Attributes

Just as HTML elements have attributes, JSX elements can also receive attributes.

Attributes provide additional information about an element and define how it should behave or appear.

Examples include:

- CSS classes
- IDs
- Images
- Links
- Accessibility properties
- Event handlers
- Component properties

Although JSX attributes look similar to HTML attributes, they follow **JavaScript rules**, not HTML rules.

---

## HTML Attributes

In HTML, attributes provide metadata for an element.

Example:

```html
<img src="logo.png" alt="Logo">

<a href="https://engineeringplaybook.dev">
    Visit Website
</a>
```

The browser reads these attributes directly.

---

## JSX Attributes

JSX follows a similar syntax.

```jsx
<img src="logo.png" alt="Engineering Playbook Logo" />
```

At first glance this looks identical to HTML.

However, JSX attributes are far more powerful because they can contain JavaScript expressions.

---

# String Attributes

Simple string values can be written exactly like HTML.

```jsx
<button title="Save">
    Save
</button>
```

```jsx
<input
    placeholder="Enter your email"
/>
```

These are static values.

---

# JavaScript Attributes

Whenever an attribute value needs to be dynamic, use curly braces.

Example:

```jsx
const image = "/images/react.png";

<img src={image} />
```

React evaluates the expression before rendering.

Conceptually:

```text
Attribute

↓

Expression

↓

Evaluate

↓

Assign Value

↓

Render
```

---

## Using Variables

```jsx
const name = "Engineering Playbook";

<h1 title={name}>
    {name}
</h1>
```

---

## Using Numbers

```jsx
const width = 300;

<img
    src="/logo.png"
    width={width}
/>
```

---

## Using Boolean Values

```jsx
const disabled = true;

<button disabled={disabled}>
    Save
</button>
```

---

## Using Expressions

```jsx
const price = 100;
const quantity = 5;

<p>Total: {price * quantity}</p>
```

Likewise,

```jsx
<input
    maxLength={20 + 10}
/>
```

Expressions are evaluated before rendering.

---

# Boolean Attributes

Some HTML attributes are boolean.

Examples:

- disabled
- checked
- required
- hidden
- readOnly

Instead of writing:

```jsx
<button disabled={true}>
```

React allows the shorter form:

```jsx
<button disabled>
```

Both are equivalent.

---

# Special JSX Attributes

Because JSX is JavaScript, some HTML attribute names cannot be used directly.

---

## class → className

HTML

```html
<div class="container">
```

JSX

```jsx
<div className="container">
```

Why?

`class` is a reserved keyword in JavaScript.

React therefore uses `className`.

---

## for → htmlFor

HTML

```html
<label for="email">
```

JSX

```jsx
<label htmlFor="email">
```

Again, this avoids conflicts with JavaScript syntax.

---

# Inline Styles

HTML

```html
<div style="color:red;">
```

JSX

```jsx
<div
    style={{
        color: "red"
    }}
>
```

Notice two important differences:

- The style attribute receives a JavaScript object.
- CSS property names use camelCase.

Example:

```jsx
style={{
    backgroundColor: "black",
    fontSize: "20px",
    marginTop: "10px"
}}
```

---

# Spread Attributes

React supports spreading object properties into JSX.

Example:

```jsx
const buttonProps = {
    disabled: true,
    className: "primary",
    title: "Save"
};

<button {...buttonProps}>
    Save
</button>
```

Conceptually:

```text
Object

↓

Spread (...)

↓

Individual Attributes

↓

React Element
```

Spread attributes improve reusability and reduce repetitive code.

---

# Default HTML vs JSX Attribute Comparison

| HTML | JSX |
|------|------|
| class | className |
| for | htmlFor |
| style="..." | style={{ }} |
| onclick | onClick |
| tabindex | tabIndex |
| readonly | readOnly |

Notice that many DOM property names use **camelCase** in JSX.

---

# Attribute Naming Rules

React follows JavaScript naming conventions.

Examples:

```text
className

tabIndex

readOnly

maxLength

autoComplete

onClick

onMouseEnter
```

CamelCase keeps attribute names consistent with JavaScript object properties.

---

# Engineering Perspective

Think of JSX attributes as **object properties**, not HTML attributes.

A helpful mental model is:

```text
HTML

↓

Browser Attributes

----------------------

JSX

↓

JavaScript Properties

↓

React Elements
```

This explains why JSX uses names like `className`, `htmlFor`, and `onClick`.

React is building JavaScript objects first, not HTML markup.

Understanding this distinction makes JSX feel much more logical and prepares you for working with React components, where attributes become **Props**, the primary mechanism for passing data between components.

---

# JSX Children

Every JSX element can contain other JSX elements.

These nested elements are called **children**.

For example:

```jsx
<div>
    <h1>Engineering Playbook</h1>
    <p>Learn Engineering. Build Better Software.</p>
</div>
```

In this example:

- `<div>` is the parent element.
- `<h1>` and `<p>` are its children.

Conceptually:

```text
div

├── h1

└── p
```

React uses this hierarchy to build the React Element Tree.

---

# Nested JSX

JSX supports deeply nested structures.

```jsx
<main>
    <section>
        <article>
            <h1>React</h1>
            <p>Learn React step by step.</p>
        </article>
    </section>
</main>
```

Conceptually:

```text
main

└── section

    └── article

        ├── h1

        └── p
```

The nesting represents the UI hierarchy.

---

# Self-Closing Tags

HTML allows some tags to omit their closing slash.

For example:

```html
<img>
```

In JSX, every element must be properly closed.

Correct:

```jsx
<img />

<input />

<br />

<hr />
```

Incorrect:

```jsx
<img>

<input>
```

Why?

Because JSX follows XML-like syntax, where every element must have a matching closing tag or be self-closing.

---

# Multiple Root Elements

One of the first errors beginners encounter is returning multiple sibling elements.

Incorrect:

```jsx
function App() {
    return (
        <h1>Hello</h1>
        <p>Welcome</p>
    );
}
```

React will display an error because the component is returning multiple root elements.

Instead, wrap them inside a single parent.

```jsx
function App() {
    return (
        <div>
            <h1>Hello</h1>
            <p>Welcome</p>
        </div>
    );
}
```

Conceptually:

```text
Component

↓

One Root Element

↓

Children

↓

Render
```

---

# Why One Root Element?

Remember from the previous chapter:

A component returns **one React Element**.

That root element may contain many children, but the component itself returns a single root.

```text
Component

↓

Root Element

├── Header

├── Main

└── Footer
```

This makes the component tree predictable and easier for React to process.

---

# React Fragments

Sometimes adding an extra `<div>` is unnecessary.

React provides **Fragments** to group multiple children without adding an extra DOM element.

Example:

```jsx
<>
    <h1>Hello</h1>
    <p>Welcome</p>
</>
```

Equivalent long form:

```jsx
<React.Fragment>
    <h1>Hello</h1>
    <p>Welcome</p>
</React.Fragment>
```

Fragments improve the DOM structure by avoiding unnecessary wrapper elements.

---

# When Should You Use Fragments?

Use fragments when:

- You need multiple sibling elements.
- You don't want an extra `<div>` in the DOM.
- A parent element would negatively affect layout or styling.

Example:

Instead of:

```jsx
<div>
    <li>React</li>
    <li>Angular</li>
</div>
```

Use:

```jsx
<>
    <li>React</li>
    <li>Angular</li>
</>
```

---

# JSX Comments

HTML comments do not work inside JSX.

Incorrect:

```jsx
<!-- Header -->
```

Correct:

```jsx
{/* Header */}
```

React treats everything inside `{}` as JavaScript.

The comment itself is simply a JavaScript block comment.

---

# Rendering Different Values

JSX can render many JavaScript values directly.

```jsx
<h1>{"Engineering Playbook"}</h1>

<p>{100}</p>

<p>{true}</p>

<p>{null}</p>
```

However, React treats some values differently.

| Value | Rendered? |
|--------|-----------|
| String | ✅ Yes |
| Number | ✅ Yes |
| React Element | ✅ Yes |
| Array | ✅ Yes (if valid JSX) |
| null | ❌ No |
| undefined | ❌ No |
| false | ❌ No |
| true | ❌ No |

This behavior is commonly used for conditional rendering.

For example:

```jsx
{isLoggedIn && <Dashboard />}
```

If `isLoggedIn` is `false`, React renders nothing.

---

# JSX Rules

Every JSX file follows a few important rules.

## Rule 1

Return a single root element.

---

## Rule 2

Close every tag.

```jsx
<img />

<input />

<hr />
```

---

## Rule 3

Use `className` instead of `class`.

---

## Rule 4

Use `htmlFor` instead of `for`.

---

## Rule 5

Embed JavaScript using curly braces.

```jsx
<h1>{title}</h1>
```

---

## Rule 6

Use camelCase for DOM properties.

Examples:

```text
onClick

tabIndex

readOnly

maxLength

autoFocus
```

---

## Rule 7

Comments must use JavaScript syntax.

```jsx
{/* Comment */}
```

---

# Common JSX Syntax Errors

## Forgetting to Close Tags

Incorrect:

```jsx
<img>
```

Correct:

```jsx
<img />
```

---

## Returning Multiple Root Elements

Incorrect:

```jsx
<>
<h1>Hello</h1>
<p>World</p>
```

Missing closing fragment.

Correct:

```jsx
<>
    <h1>Hello</h1>
    <p>World</p>
</>
```

---

## Using HTML Attribute Names

Incorrect:

```jsx
<div class="container">
```

Correct:

```jsx
<div className="container">
```

---

## Forgetting Curly Braces

Incorrect:

```jsx
<h1>title</h1>
```

If `title` is a variable.

Correct:

```jsx
<h1>{title}</h1>
```

---

# Engineering Perspective

JSX is intentionally strict.

These rules may seem restrictive at first, but they help React build a predictable component tree and reduce ambiguity during compilation.

Think of JSX as a structured language for describing user interfaces.

Every JSX component should produce a clear, valid hierarchy that React can transform into React Elements and eventually render efficiently.

By following these rules consistently, your components become easier to read, maintain, and reason about—especially as applications grow in size and complexity.

---

# How JSX Works Behind the Scenes

Everything you've written so far has looked like HTML.

However, the browser has no idea what JSX is.

Consider this JSX:

```jsx
function App() {
    return (
        <h1>Hello React</h1>
    );
}
```

If you save this code into a plain JavaScript file and open it directly in a browser, it will fail.

Why?

Because browsers understand JavaScript—not JSX.

JSX must first be transformed into standard JavaScript before it can be executed.

---

# JSX Compilation Pipeline

The complete lifecycle looks like this:

```text
Developer

↓

Writes JSX

↓

Compiler (Babel / SWC)

↓

JavaScript

↓

Browser

↓

React

↓

UI
```

Let's understand each step.

---

# Step 1 — You Write JSX

The developer writes readable JSX.

```jsx
function App() {
    return (
        <h1>Hello React</h1>
    );
}
```

This is optimized for humans.

Not for browsers.

---

# Step 2 — The Compiler

During development or production build, tools such as:

- Babel
- SWC
- esbuild

transform JSX into JavaScript.

React itself does **not** compile JSX.

The compiler does.

Modern React projects using Vite typically use **esbuild** during development and **Rollup** for production builds, while other toolchains may use Babel or SWC.

---

# Step 3 — JSX Becomes JavaScript

Conceptually, the previous JSX becomes:

```javascript
React.createElement(
    "h1",
    null,
    "Hello React"
);
```

Notice something important.

The HTML-like syntax completely disappears.

Only JavaScript remains.

---

# Step 4 — React Creates a React Element

`React.createElement()` returns a JavaScript object.

Conceptually:

```javascript
{
    type: "h1",
    props: {
        children: "Hello React"
    }
}
```

This object is called a **React Element**.

It is **not** a DOM element.

It is simply a description of the UI.

---

# Step 5 — React Builds the UI

React receives the React Element.

```text
React Element

↓

Virtual DOM

↓

Reconciliation

↓

Browser DOM

↓

Visible UI
```

Eventually, React updates the real DOM and the browser paints the interface.

---

# The Complete Flow

Everything you've learned so far connects together.

```text
Developer

↓

JSX

↓

Compiler

↓

JavaScript

↓

React.createElement()

↓

React Element

↓

Virtual DOM

↓

Reconciliation

↓

Browser DOM

↓

Screen
```

This is the complete lifecycle of a JSX element.

---

# Classic JSX Runtime

Before React 17, every JSX file required importing React.

Example:

```jsx
import React from "react";

function App() {
    return <h1>Hello</h1>;
}
```

Why?

Because JSX was compiled into:

```javascript
React.createElement(...)
```

Without importing React, the compiler would generate code that referenced `React`, resulting in an error.

---

# Automatic JSX Runtime

React 17 introduced the **Automatic JSX Runtime**.

Now you can write:

```jsx
function App() {
    return <h1>Hello</h1>;
}
```

No explicit React import is required just to use JSX.

The compiler automatically imports the required JSX runtime functions during compilation.

This reduces boilerplate while keeping the runtime behavior the same.

---

# Does JSX Affect Performance?

Many beginners wonder whether JSX is slower than writing plain JavaScript.

The answer is **no**.

JSX is removed during compilation.

By the time your application runs in the browser, there is no JSX left—only JavaScript.

The browser never executes JSX directly.

Therefore, writing JSX does not introduce runtime overhead by itself.

---

# JSX Is Not a Template Engine

Another common misconception is that JSX works like template languages such as Handlebars or EJS.

It doesn't.

Template engines generate HTML strings.

JSX generates **React Elements**.

Conceptually:

```text
Template Engine

↓

HTML String

↓

Browser
```

React:

```text
JSX

↓

React Elements

↓

React

↓

DOM
```

This distinction is fundamental to understanding how React works.

---

# Common Misconceptions

## "JSX is HTML"

❌ Incorrect

JSX only resembles HTML.

It is JavaScript syntax that is compiled before execution.

---

## "The Browser Understands JSX"

❌ Incorrect

Browsers execute JavaScript.

A compiler transforms JSX into JavaScript before the browser ever sees it.

---

## "React Reads JSX"

Not directly.

The compiler transforms JSX first.

React works with the generated JavaScript and React Elements.

---

# Engineering Perspective

JSX is a **developer-friendly syntax**, not a browser technology.

Its purpose is to improve readability and maintainability while preserving the full power of JavaScript.

By separating authoring syntax (JSX) from runtime execution (JavaScript), React allows developers to write expressive UI code without changing how browsers execute applications.

Understanding this compilation process helps explain many React concepts, including React Elements, rendering, reconciliation, and why tools like Vite, Babel, and SWC are part of the React ecosystem.

---

# Best Practices

- Treat JSX as JavaScript, not HTML.
- Use JSX to describe UI, not to write complex business logic.
- Keep expressions simple and readable.
- Move complex logic outside of the returned JSX.
- Prefer meaningful component composition over deeply nested markup.

---

# Common Mistakes

❌ Assuming JSX is sent directly to the browser.

❌ Mixing large amounts of business logic inside JSX.

❌ Thinking `React.createElement()` is called manually in modern React projects.

❌ Believing JSX is required to use React (it isn't—it's a convenience syntax).

---

# Summary

JSX is a syntax extension that makes React components easier to write and understand.

Although it looks like HTML, JSX is transformed into JavaScript during compilation.

The compiler converts JSX into React Element creation code, React builds an internal representation of the UI, and finally updates the browser DOM.

Understanding this pipeline is essential because every React application relies on it.

---

# Knowledge Check

1. What does JSX stand for?
2. Is JSX HTML? Explain your answer.
3. Why can't browsers execute JSX directly?
4. Which tools compile JSX into JavaScript?
5. What does `React.createElement()` return?
6. What is the difference between the Classic and Automatic JSX Runtime?
7. Why doesn't JSX affect runtime performance?
8. How does JSX differ from a template engine?

---

# Further Reading

- 📖 React Elements
- 📖 Components
- 📖 Rendering

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← React Core Concepts | ↑ Core Concepts | 🗺 React Learning Path | React Elements → |

---

# Continue Your Journey

You now understand how JSX is written, how it is compiled, and how it becomes React Elements.

In the next article, you'll explore **React Elements**—the immutable JavaScript objects that represent every piece of your user interface and form the foundation of React's rendering system.

- ⬅ **Previous:** [React Core Concepts](README.md)
- ➡ **Next:** [02 - React Elements](02-react-elements.md)