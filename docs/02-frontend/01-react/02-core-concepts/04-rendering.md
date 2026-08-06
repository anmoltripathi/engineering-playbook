# Rendering

> Module: React Core Concepts
>
> Reading Time: 60–75 Minutes
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
> → Rendering

---

# Overview

So far in this module you've learned:

```
JSX

↓

React Elements

↓

Components
```

A question naturally follows:

> **How does a React component actually appear on the screen?**

The answer is **Rendering**.

Rendering is the process through which React executes components, creates React Elements, compares UI changes, and eventually updates the browser.

Although developers often think rendering simply means "displaying the UI," React's rendering process is much more sophisticated.

Understanding rendering is essential because it forms the foundation for:

- Virtual DOM
- Reconciliation
- State Updates
- Props
- Performance Optimization
- React Fiber

Every React application relies on this process.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Rendering |
| Level | Beginner → Intermediate |
| Reading Time | 60–75 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | JSX, React Elements, Components |
| Next Topic | Virtual DOM |

---

# Why This Matters

Every time:

- a component mounts,
- state changes,
- props change,
- context changes,

React performs another render.

If you don't understand rendering, it becomes difficult to reason about:

- why components update,
- why unnecessary renders occur,
- why performance problems appear,
- why Hooks behave the way they do.

Rendering is one of the most important concepts in React.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain what rendering means in React.
- Understand how React renders components.
- Distinguish rendering from DOM updates.
- Explain initial rendering.
- Explain re-rendering.
- Understand render triggers.
- Understand Render Phase and Commit Phase.
- Prepare for Virtual DOM and Reconciliation.

---

# What is Rendering?

Rendering is the process of converting React Components into React Elements so React can determine what should appear on the screen.

Rendering does **not** immediately mean updating the browser DOM.

Instead, rendering is React calculating what the UI should look like.

Think of rendering as React preparing a blueprint before construction begins.

Conceptually:

```
Component

↓

Execute Function

↓

React Elements

↓

Virtual UI

↓

DOM Update (later)
```

---

# A Simple Example

Consider the following component.

```jsx
function Welcome() {
    return (
        <h1>Hello Engineering Playbook</h1>
    );
}
```

When React renders this component:

Step 1

React calls the function.

```
Welcome()
```

Step 2

The function returns JSX.

```
<h1>Hello Engineering Playbook</h1>
```

Step 3

JSX becomes React Elements.

```
React Element

↓

type

↓

props

↓

children
```

Step 4

React compares the result with the previous UI.

Step 5

React updates the browser only if something changed.

This entire workflow is called rendering.

---

# Rendering Is Not Painting

Many beginners think:

```
Rendering

=

Showing UI
```

This is not entirely correct.

React rendering and browser painting are two different processes.

React is responsible for calculating the next UI.

The browser is responsible for drawing pixels on the screen.

Conceptually:

```
React

↓

Calculate UI

↓

Browser

↓

Paint Pixels
```

React never draws pixels itself.

---

# The Rendering Pipeline

Every render follows the same high-level process.

```
Component

↓

Execute Function

↓

Return React Elements

↓

Build UI Tree

↓

Compare Previous Tree

↓

Update Browser DOM

↓

Browser Paint
```

Notice that DOM updates happen near the end of the pipeline.

Most of React's work occurs before touching the browser.

---

# Initial Render

The first time an application appears on the screen is called the **Initial Render**.

Example:

```
React App Starts

↓

<App />

↓

React Executes Components

↓

Builds React Elements

↓

Creates DOM

↓

Screen Appears
```

This happens only once for a component's initial mount.

---

# Re-render

After the initial render, React may render the component again.

This is called a **Re-render**.

Example:

```
Button Click

↓

State Changes

↓

React Executes Component Again

↓

New React Elements

↓

Compare

↓

Update DOM
```

A re-render does **not** necessarily mean the DOM changes.

React first determines whether any visual changes are required.

---

# Initial Render vs Re-render

| Initial Render | Re-render |
|---------------|-----------|
| First execution | Executes again |
| Creates UI | Updates UI |
| Happens once | Happens many times |
| Creates DOM | Updates DOM only if needed |

Understanding this distinction is essential before learning Reconciliation.

---

# Engineering Perspective

Rendering is one of the most misunderstood terms in React.

Rendering does not mean "changing the DOM."

Rendering means **executing components to calculate the next version of the user interface**.

Only after React finishes rendering does it decide whether the browser actually needs to be updated.

This separation allows React to optimize updates and avoid unnecessary DOM operations, which are significantly more expensive than creating lightweight JavaScript objects.

---

# What Triggers Rendering?

React does not continuously render components.

Instead, rendering occurs only when React detects that something may have changed in the application's user interface.

Think of rendering as React's response to change.

Conceptually:

```text
Something Changes

↓

React Detects Change

↓

Render Scheduled

↓

Component Executes

↓

New UI Calculated
```

Understanding what causes rendering is essential for building efficient React applications.

---

# Trigger 1 — Initial Application Load

The very first render occurs when React mounts your application.

Example:

```jsx
createRoot(document.getElementById("root")).render(
    <App />
);
```

Flow:

```text
Application Starts

↓

<App />

↓

React Executes Components

↓

Initial Render

↓

Browser Displays UI
```

This happens only once for the initial mount of a component.

---

# Trigger 2 — State Changes

The most common render trigger is a state update.

Example:

```jsx
const [count, setCount] = useState(0);
```

When:

```jsx
setCount(count + 1);
```

is executed,

React schedules another render.

Conceptually:

```text
State Updated

↓

Component Executes Again

↓

New React Elements

↓

Compare

↓

Update DOM (if needed)
```

Notice something important.

Changing state does **not** directly update the DOM.

It first triggers another render.

---

# Trigger 3 — Props Changes

Components receive data through Props.

When a parent component passes new props to a child, React renders the child again.

Example:

```jsx
<Profile
    user={currentUser}
/>
```

If `currentUser` changes,

React executes the `Profile` component again.

Flow:

```text
Parent Updates

↓

New Props

↓

Child Renders

↓

React Compares UI

↓

Update DOM
```

---

# Trigger 4 — Context Changes

React Context allows data to be shared across multiple components.

Whenever a Context value changes,

every component consuming that Context is scheduled to render again.

Conceptually:

```text
Context Updated

↓

Consumers Notified

↓

Components Render

↓

React Compares

↓

DOM Update
```

You'll explore Context in a later module.

---

# Trigger 5 — Parent Re-render

One of the biggest surprises for beginners is that a child component may render even if its own data has not changed.

Example:

```text
App

├── Header

├── Dashboard

└── Footer
```

If `App` renders again,

its child components are also executed by default.

This does **not** automatically mean the browser DOM changes.

React still compares the resulting UI before updating the DOM.

---

# Trigger 6 — Force Updates

Although uncommon, React also provides ways to force rendering.

Examples include:

- Force updates (legacy APIs)
- Certain development tools
- Development features such as Strict Mode

In modern React, developers generally rely on state and props rather than forcing renders manually.

---

# What Does NOT Trigger Rendering?

Understanding what **doesn't** cause rendering is just as important.

---

## Local Variables

Changing a normal JavaScript variable has no effect on React.

Example:

```jsx
let count = 0;

count++;
```

React doesn't know this variable changed.

Therefore, no render occurs.

---

## Updating Objects Without State

Example:

```jsx
const user = {
    name: "Alex"
};

user.name = "John";
```

The object changed,

but React was never notified.

Without a state update,

no render occurs.

---

## DOM Manipulation

Changing the DOM manually using browser APIs does not trigger React rendering.

Example:

```javascript
document.getElementById("title").textContent = "Hello";
```

React is unaware of this change.

Direct DOM manipulation should generally be avoided in React applications.

---

# Summary of Render Triggers

| Trigger | Causes Render? |
|----------|----------------|
| Initial Mount | ✅ Yes |
| State Update | ✅ Yes |
| Props Change | ✅ Yes |
| Context Change | ✅ Yes |
| Parent Render | ✅ Usually |
| Local Variable Change | ❌ No |
| Manual Object Mutation | ❌ No |
| Direct DOM Manipulation | ❌ No |

---

# Rendering Is Scheduled

An important detail often overlooked is that React does not always render immediately.

Instead, React schedules rendering.

Conceptually:

```text
State Update

↓

React Scheduler

↓

Render

↓

Commit

↓

Browser Paint
```

Modern versions of React intelligently schedule work to keep applications responsive.

You'll learn more about scheduling and React Fiber in the Advanced module.

---

> 🏗️ Engineering Note
>
> A render is **not** a failure or a performance problem.
>
> Rendering is React's normal mechanism for recalculating the UI.
>
> Performance issues arise from **expensive rendering**, **unnecessary rendering**, or **inefficient DOM updates**—not from rendering itself.

---

# The Two Phases of Rendering

React does not update the browser immediately after a render is triggered.

Instead, React divides rendering into two distinct phases.

```text
Render Trigger

↓

Render Phase

↓

Commit Phase

↓

Browser Paint
```

Understanding these phases is essential because many advanced React features—including Hooks, Virtual DOM, Reconciliation, Concurrent Rendering, and React Fiber—are built around them.

---

# Phase 1 — Render Phase

The Render Phase is where React calculates what the next version of the user interface should look like.

During this phase, React:

- Executes components
- Creates new React Elements
- Builds the next UI tree
- Compares it with the previous tree

Notice something important.

**React does not modify the browser DOM during this phase.**

Instead, React is simply performing calculations.

Conceptually:

```text
Component

↓

Execute Function

↓

React Elements

↓

Next UI Tree

↓

Ready for Comparison
```

Think of this phase as planning before construction begins.

---

# What Happens During the Render Phase?

Suppose the following code executes.

```jsx
setCount(count + 1);
```

React begins the Render Phase.

```text
State Updated

↓

Component Executes Again

↓

New JSX Returned

↓

New React Elements Created

↓

Next UI Calculated
```

At this point,

the browser has **not changed yet**.

React is still working internally.

---

# Characteristics of the Render Phase

The Render Phase is:

✅ Pure

✅ Predictable

✅ Side-effect free

✅ Focused on calculation

Its only responsibility is determining what the UI should look like.

---

# Phase 2 — Commit Phase

Once React finishes calculating the next UI,

it enters the Commit Phase.

This is where React applies changes to the browser.

Conceptually:

```text
Previous DOM

↓

React Knows Changes

↓

Update DOM

↓

Browser Paint
```

Unlike the Render Phase,

this phase actually interacts with the browser.

---

# What Happens During the Commit Phase?

React performs operations such as:

- Creating DOM nodes
- Removing DOM nodes
- Updating attributes
- Updating text
- Attaching event listeners
- Updating references (refs)

Only the necessary changes are applied.

---

# Example

Imagine the counter changes from:

```text
Count: 5
```

to

```text
Count: 6
```

During Render:

```text
Old Tree

↓

New Tree

↓

Difference Found
```

During Commit:

```text
Update Text Node

↓

Browser DOM Updated

↓

User Sees "6"
```

React updates only what actually changed.

---

# Render Phase vs Commit Phase

| Render Phase | Commit Phase |
|--------------|--------------|
| Executes Components | Updates Browser DOM |
| Creates React Elements | Applies DOM Changes |
| Calculates Next UI | Makes UI Visible |
| No DOM Changes | DOM Changes Occur |
| Pure Computation | Browser Interaction |

Understanding this distinction is one of the biggest milestones in learning React.

---

# Why Separate These Phases?

Imagine updating the browser after every line of code.

```text
Update DOM

↓

Calculate

↓

Update DOM

↓

Calculate

↓

Update DOM
```

This would be slow and inefficient.

Instead,

React first calculates everything.

Only then does it perform the minimum required DOM updates.

```text
Calculate Everything

↓

Know Exactly What Changed

↓

One Efficient DOM Update
```

This separation is one reason React performs well.

---

# Rendering Does Not Mean DOM Updates

This is one of the most common misconceptions.

Many developers believe:

```text
Render

=

DOM Update
```

This is incorrect.

A render may occur without any DOM changes.

Example:

```jsx
function App() {

    console.log("Rendering...");

    return <h1>Hello</h1>;

}
```

The component can execute multiple times.

If the resulting UI is identical,

React may skip updating the DOM.

Conceptually:

```text
Component Executes

↓

Same UI

↓

No DOM Changes
```

Rendering and committing are related,

but they are not the same thing.

---

# Render Purity

React expects components to behave like pure functions during rendering.

A render should:

- Receive inputs (Props, State, Context)
- Calculate JSX
- Return React Elements

Nothing more.

Avoid performing side effects while rendering.

For example:

❌ Fetching data

❌ Modifying the DOM

❌ Starting timers

❌ Calling browser APIs

Those belong in Effects, which you'll learn in the Hooks module.

---

> 🏗️ Engineering Note
>
> A good mental model is:
>
> **Render = "What should the UI look like?"**
>
> **Commit = "Apply those changes to the browser."**
>
> Keeping these responsibilities separate allows React to optimize rendering, defer work, and support advanced features such as Concurrent Rendering.

---

# Visualizing the Complete Process

Everything you've learned so far connects together.

```text
State Changes

↓

Render Trigger

↓

Render Phase

• Execute Components

• Create React Elements

• Build Next UI Tree

↓

Commit Phase

• Update Browser DOM

↓

Browser Paint

↓

User Sees Updated UI
```

This lifecycle occurs repeatedly throughout the lifetime of a React application.

# Rendering vs Reconciliation

By now, you've learned that rendering calculates the next version of the user interface.

However, another important question remains:

> **How does React determine what actually changed?**

The answer is **Reconciliation**.

Rendering and Reconciliation are closely related, but they are not the same process.

Understanding the distinction is essential for mastering React's rendering architecture.

---

## Rendering

Rendering is the process of executing components and producing a new UI description.

During rendering, React answers one question:

> **"What should the UI look like now?"**

Conceptually:

```text
Props

State

Context

↓

Execute Components

↓

Create React Elements

↓

Build New UI Tree
```

Rendering only calculates the next UI.

Nothing has changed in the browser yet.

---

## Reconciliation

Once React has the new UI tree,

it compares it with the previous UI tree.

This comparison process is called **Reconciliation**.

Its purpose is simple:

> **Find the minimum number of changes required to update the UI.**

Conceptually:

```text
Previous Tree

↓

Compare

↓

Next Tree

↓

Identify Changes
```

React does not rebuild the entire page.

Instead,

it identifies only what actually changed.

---

## Relationship Between Rendering and Reconciliation

Think of them as consecutive steps.

```text
Rendering

↓

Creates Next UI

↓

Reconciliation

↓

Compares UI Trees

↓

Commit Phase

↓

Update Browser DOM
```

Rendering calculates.

Reconciliation compares.

Commit applies.

---

## Example

Suppose your application displays:

```text
Count: 5
```

After clicking a button:

```jsx
setCount(6);
```

React performs the following steps:

```text
State Changes

↓

Render

↓

New React Elements

↓

Reconciliation

↓

Text Changed

↓

Commit

↓

DOM Updated

↓

Browser Paint
```

Notice that only the text node changes.

Everything else remains untouched.

---

## Why Separate Rendering and Reconciliation?

Imagine React skipped reconciliation.

Every state change would rebuild the entire page.

```text
Button Click

↓

Destroy DOM

↓

Recreate DOM

↓

Paint Again
```

That would be slow and inefficient.

Instead,

React performs this optimized workflow.

```text
Render

↓

Compare

↓

Update Only Differences
```

This approach minimizes expensive DOM operations.

---

# Rendering vs Browser Paint

Another misconception is that React controls everything displayed on the screen.

It doesn't.

React prepares updates.

The browser performs the actual drawing.

Conceptually:

```text
React

↓

Render

↓

Reconciliation

↓

Commit

↓

Browser

↓

Layout

↓

Paint

↓

Composite

↓

Visible Screen
```

React stops after updating the DOM.

The browser is responsible for rendering pixels.

---

# Why React Can Skip DOM Updates

One of React's biggest optimizations is that a render does **not** always produce a DOM update.

Imagine this component.

```jsx
function Greeting() {
    return <h1>Hello</h1>;
}
```

Suppose React renders it twice.

Both renders produce exactly the same React Elements.

Conceptually:

```text
Previous UI

↓

<h1>Hello</h1>

↓

New UI

↓

<h1>Hello</h1>
```

Reconciliation finds no differences.

Result:

```text
Render

↓

Compare

↓

No Differences

↓

Skip Commit

↓

No DOM Updates
```

The component rendered,

but the browser DOM remained unchanged.

---

# Why This Is Important

Many developers believe:

```text
Render

↓

Always Updates DOM
```

This is incorrect.

The actual workflow is:

```text
Render

↓

Compare

↓

Only Update If Necessary
```

Understanding this distinction helps explain:

- Why React is efficient
- Why unnecessary renders aren't always expensive
- Why React focuses on minimizing DOM operations

---

> 🏗️ Engineering Note
>
> Rendering itself is relatively inexpensive because it mainly creates lightweight JavaScript objects.
>
> Browser DOM operations—creating elements, updating layouts, recalculating styles, and repainting pixels—are significantly more expensive.
>
> React's architecture is designed to reduce these costly operations as much as possible.

---

# Function Components and Rendering

One of the most important concepts to understand is that **every render executes the component function again**.

This often surprises developers who are new to React.

Consider the following component:

```jsx
function Counter() {
    console.log("Rendering...");

    return (
        <h1>Counter</h1>
    );
}
```

Every time React renders this component,

the function executes from top to bottom.

Conceptually:

```text
Render

↓

Call Counter()

↓

Execute Function

↓

Return React Elements
```

React does **not** reuse the previous function execution.

Instead, it executes the function again to calculate the next UI.

---

# Every Render Creates New React Elements

Suppose your component returns:

```jsx
<h1>Hello</h1>
```

Every render creates a **new React Element object**.

Conceptually:

First Render

```text
<h1>Hello</h1>

↓

React Element A
```

Second Render

```text
<h1>Hello</h1>

↓

React Element B
```

Even though both describe the same UI,

they are newly created JavaScript objects.

React later determines whether the resulting UI has actually changed.

---

# Why Doesn't This Hurt Performance?

At first this sounds inefficient.

> "React creates new objects every render?"

Yes.

But React Elements are extremely lightweight.

Creating JavaScript objects is much cheaper than updating the browser DOM.

Conceptually:

```text
Create React Element

≈ Cheap

----------------

Modify Browser DOM

≈ Expensive
```

React intentionally favors creating new objects over manipulating the DOM unnecessarily.

---

# Render Does Not Mean Rebuild

Imagine a dashboard.

```text
Dashboard

├── Header

├── Sidebar

├── Statistics

├── Chart

└── Footer
```

Suppose only the statistics value changes.

React may execute several components again,

but after comparison,

only the changed DOM node is updated.

```text
Render

↓

Compare

↓

One Small DOM Update
```

This is one of React's biggest performance advantages.

---

# Pure Rendering

React expects rendering to behave like a **pure function**.

A pure function:

- Receives inputs.
- Produces the same output for the same inputs.
- Does not produce side effects.

Conceptually:

```text
Props

+

State

↓

Component

↓

Same JSX
```

If the inputs haven't changed,

the rendered output should also remain the same.

---

# What Should NOT Happen During Rendering?

Rendering should only calculate the UI.

Avoid performing work such as:

❌ Fetching API data

❌ Writing to localStorage

❌ Updating the DOM

❌ Starting timers

❌ Playing audio

❌ Opening dialogs

These operations are called **side effects**.

You'll learn how React handles them safely in the Hooks module using `useEffect`.

---

# React Strict Mode (Development)

When running a React application in development,

you may notice components rendering twice.

Example:

```jsx
console.log("Render");
```

Console Output:

```text
Render

Render
```

This is usually caused by **React Strict Mode**.

Strict Mode intentionally performs extra renders during development to help detect:

- Side effects during rendering
- Unsafe lifecycle behavior
- Unexpected mutations

This behavior does **not** occur in production builds.

---

# Rendering Is Predictable

One of React's greatest strengths is that rendering is deterministic.

Given the same:

- Props
- State
- Context

a component should always return the same React Elements.

Conceptually:

```text
Same Inputs

↓

Same Output

↓

Predictable UI
```

This predictability makes React applications easier to debug, test, and optimize.

---

# Engineering Perspective

Rendering is the heart of React's declarative programming model.

Instead of manually telling the browser what to change,

developers describe the desired UI by returning React Elements from components.

React repeatedly executes components, calculates the next interface, compares it with the previous one, and updates only the parts of the browser that actually changed.

This separation between **calculation** and **DOM manipulation** is one of the key architectural decisions that makes React scalable and performant.

---

# Best Practices

- Keep render functions pure.
- Avoid side effects during rendering.
- Keep rendering logic simple and readable.
- Split large components into smaller ones.
- Remember that rendering calculates UI—it doesn't directly update the DOM.

---

# Common Mistakes

❌ Assuming every render updates the DOM.

❌ Treating rendering as a performance problem.

❌ Performing API calls inside the render body.

❌ Modifying the DOM manually during rendering.

❌ Confusing rendering with browser painting.

---

# Interview Questions

## Beginner

1. What is rendering in React?
2. What triggers a render?
3. Does every render update the DOM?
4. What is the difference between an initial render and a re-render?

## Intermediate

5. Explain the Render Phase and Commit Phase.
6. Why are React renders considered pure?
7. What happens when state changes?
8. Why does React execute function components multiple times?

## Advanced

9. Why can React skip DOM updates after rendering?
10. How does rendering relate to the Virtual DOM?
11. Why is creating new React Elements inexpensive?
12. What is the purpose of React Strict Mode?

---

# Hands-on Exercises

## Exercise 1

Create a component with a `console.log()` statement.

Observe when the component renders.

---

## Exercise 2

Update state using a button.

Track:

- Render
- DOM Update

Determine whether every render changes the DOM.

---

## Exercise 3

Build a component hierarchy.

Identify which components render after a parent state update.

---

## Exercise 4

Enable React Strict Mode.

Observe how rendering differs between development and production.

Document your findings.

---

# Summary

Rendering is the process of calculating the next version of the user interface.

During rendering, React executes components, creates new React Elements, and prepares the next UI tree.

Only after rendering does React compare the new tree with the previous one and decide whether the browser DOM needs to be updated.

Understanding rendering is fundamental because it serves as the foundation for the next two topics:

- Virtual DOM
- Reconciliation

---

# Knowledge Check

Before moving on, make sure you can answer the following:

- What is rendering?
- What triggers rendering?
- What happens during the Render Phase?
- What happens during the Commit Phase?
- Why doesn't every render update the DOM?
- Why does React execute component functions again?
- What makes rendering "pure"?

---

# Further Reading

- 📖 Virtual DOM
- 📖 Reconciliation
- 📖 React Fiber (Advanced)

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Components | ↑ React Core Concepts | 🗺 Module Home | Virtual DOM → |

---

# Continue Your Journey

You've learned how React executes components and calculates the next version of the UI.

In the next chapter, you'll explore the **Virtual DOM**—React's lightweight in-memory representation of the user interface that enables efficient updates and forms the foundation for React's reconciliation process.

- ⬅ **Previous:** [03 - Components](03-components.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [05 - Virtual DOM](05-virtual-dom.md)