# How React Works

> Module: React Fundamentals
>
> Reading Time: 25–30 Minutes
>
> Difficulty: 🟡 Beginner

---

> **📍 Location**
>
> Frontend Engineering Playbook
>
> → Docs
>
> → Frontend
>
> → React
>
> → React Fundamentals
>
> → How React Works

---

# Overview

React makes building user interfaces simple by allowing developers to describe **what the interface should look like**, rather than manually updating HTML elements whenever data changes.

Although writing React code often feels straightforward, a considerable amount of work happens behind the scenes before the browser displays anything.

Every time you write a component, click a button, update state, or fetch data, React follows a predictable rendering process.

Understanding this process is one of the most important milestones in becoming a React developer because nearly every advanced React topic—including Components, State, Hooks, Performance, and Architecture—builds upon it.

Rather than treating React as a "black box," this article explains the complete journey from writing a React component to seeing the final user interface in the browser.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Fundamentals |
| Topic | How React Works |
| Level | Beginner |
| Reading Time | 25–30 Minutes |
| Hands-on Required | No |
| Code Examples | Minimal |
| Prerequisites | What is React, Why React, History of React |
| Next Topic | React Ecosystem |

---

# Why This Matters

Many beginners can build React applications without understanding what React is actually doing behind the scenes.

As a result, topics such as:

- Rendering
- Re-rendering
- State Updates
- Hooks
- Performance
- Memoization

often seem confusing.

Once you understand React's rendering pipeline, these concepts become much easier to learn because you'll understand **why** React behaves the way it does rather than simply memorizing APIs.

Think of this article as learning how the engine of a car works before learning how to drive it efficiently.

---

# Learning Objectives

After completing this article, you'll be able to:

- Explain how React renders a user interface.
- Understand React's rendering pipeline.
- Describe what happens when application data changes.
- Explain the difference between the Virtual DOM and the Browser DOM.
- Understand React's high-level rendering lifecycle.
- Build a mental model for how React updates the screen.

---

# Mental Model

Before learning React's internal workflow, it's important to understand the difference between traditional web development and React's approach.

## Traditional Web Development

In traditional JavaScript development, developers manually update the browser.

```text
User Clicks Button

        │

        ▼

Find HTML Element

        │

        ▼

Modify HTML

        │

        ▼

Modify CSS

        │

        ▼

Update Browser
```

The developer is responsible for deciding **what should change** and **how it should change**.

As applications grow, this quickly becomes difficult to maintain.

---

## React's Approach

React follows a different philosophy.

Instead of manipulating the browser directly, developers update the application's data.

React determines how the interface should change.

```text
User Clicks Button

        │

        ▼

Application State Changes

        │

        ▼

React Calculates Changes

        │

        ▼

Browser Updates Automatically
```

Notice the difference.

With React, developers focus on **application state**.

React focuses on **updating the user interface**.

This is one of the biggest mindset shifts when learning React.

---

# The Big Picture

Let's look at the complete lifecycle of a React application before diving into each step.

```text
Developer Writes Components

            │

            ▼

React Creates React Elements

            │

            ▼

Builds Component Tree

            │

            ▼

Creates Virtual DOM

            │

            ▼

Renders Browser DOM

            │

            ▼

User Sees Interface

            │

            ▼

User Interacts

            │

            ▼

Application State Changes

            │

            ▼

React Re-renders

            │

            ▼

Updates Only Necessary DOM Nodes

            │

            ▼

Browser Paints Updated UI
```

Although this diagram may look complex today, by the end of this article every step will make sense.

---

# React's High-Level Workflow

At a high level, React repeats the same process throughout the life of an application.

```text
Write Components

↓

Render UI

↓

User Interaction

↓

State Changes

↓

React Re-renders

↓

Browser Updates

↓

Repeat
```

Everything you'll learn later—including Hooks, State Management, Performance Optimization, and Component Lifecycle—is built on top of this workflow.

Understanding this cycle is one of the most important concepts in React.

---

# Engineering Perspective

One of the reasons React became successful is that it changed how developers think.

Traditional development asks:

> "Which HTML element should I update?"

React asks:

> "What should the user interface look like right now?"

This small change in thinking has a huge impact.

Instead of writing code that updates dozens of DOM elements manually, developers describe the current state of the application.

React then determines the most efficient way to synchronize the browser with that state.

This declarative programming model makes applications easier to understand, easier to test, and easier to maintain as they grow.

---

> 💡 **Key Insight**
>
> React's primary job is **not creating HTML**.
>
> React's primary responsibility is **keeping the user interface synchronized with application state**.

---

# React Rendering Pipeline

Now that you understand the high-level workflow, let's look at what actually happens when a React application starts.

Although React performs many operations internally, the overall rendering pipeline can be understood as a sequence of predictable steps.

```text
Developer Writes React Code

        │

        ▼

JSX is Converted into React Elements

        │

        ▼

React Builds the Component Tree

        │

        ▼

React Creates the Virtual DOM

        │

        ▼

React Renders the Real DOM

        │

        ▼

Browser Paints the Screen

        │

        ▼

User Interacts

        │

        ▼

State Changes

        │

        ▼

React Starts the Process Again
```

Think of this as React's rendering pipeline.

Every React application follows this process repeatedly throughout its lifetime.

---

# Step 1 — You Write Components

Every React application begins with components.

A component is a reusable piece of the user interface that describes **what should appear on the screen**.

For example:

```jsx
function App() {
    return <h1>Hello React</h1>;
}
```

Although this code looks simple, several things happen behind the scenes before the browser displays **Hello React**.

At this stage:

- Nothing has been rendered.
- The browser has not been updated.
- React is simply reading your component.

Think of a component as a blueprint rather than the finished building.

```text
Blueprint

↓

Construction

↓

Finished Building
```

Similarly,

```text
React Component

↓

React Processing

↓

Visible User Interface
```

The component itself is only a description.

React is responsible for turning that description into a real interface.

---

## Components Describe the UI

One of the most important ideas in React is that components describe the user interface instead of creating it directly.

Imagine describing a room to an architect.

You might say:

- One window
- One door
- Two lights
- Wooden floor

This description is not the room itself.

It is simply a specification.

React components work the same way.

They describe:

- What should appear
- How elements are organized
- Which components are nested inside others

React later converts this description into actual browser elements.

---

# Step 2 — JSX Becomes React Elements

The code we write in React often looks like HTML.

```jsx
function App() {
    return (
        <h1>Hello React</h1>
    );
}
```

However, this is **not HTML**.

It is **JSX**.

JSX is a syntax that allows developers to write UI in a familiar way while still using JavaScript.

Before the browser can understand it, JSX is transformed into regular JavaScript.

Conceptually, the transformation looks like this:

```text
JSX

↓

JavaScript

↓

React Element
```

A React Element is a plain JavaScript object that describes what should appear on the screen.

For example, the previous JSX eventually becomes something conceptually similar to:

```javascript
{
    type: "h1",
    props: {
        children: "Hello React"
    }
}
```

Don't worry about the exact syntax.

The important idea is this:

> **JSX is only a developer-friendly way to describe React Elements.**

We'll explore JSX in detail in the next module.

---

## React Elements Are Descriptions

A common beginner misconception is thinking that React immediately creates HTML.

It doesn't.

Instead, React first creates **React Elements**.

Think of them as instructions.

```text
Component

↓

React Element

↓

Browser Element
```

The React Element simply answers questions such as:

- What type of element is this?
- What properties does it have?
- What children does it contain?

React uses this information later during rendering.

---

# Step 3 — React Builds the Component Tree

Once React has converted your JSX into React Elements, it organizes them into a tree.

Consider this example.

```jsx
<App>

    <Header />

    <Main>

        <ProductList />

    </Main>

    <Footer />

</App>
```

Internally, React thinks about this structure as a hierarchy.

```text
App

├── Header

├── Main

│     └── ProductList

└── Footer
```

This hierarchy is called the **Component Tree**.

Every React application has one.

As applications become larger, the tree becomes deeper.

```text
App

├── Header

│      ├── Logo

│      ├── Search

│      └── Navigation

├── Dashboard

│      ├── Sidebar

│      ├── Statistics

│      ├── Charts

│      └── Activity Feed

└── Footer
```

Understanding the component tree is important because:

- React renders components from this hierarchy.
- Parent components contain child components.
- Updates often flow through this tree.
- Many performance optimizations depend on it.

You'll revisit the Component Tree many times throughout this playbook.

---

# Why the Component Tree Matters

Imagine trying to manage a large application without structure.

Everything would exist in one enormous file.

```text
Application

↓

5000 Lines

↓

Everything Mixed Together
```

React replaces that with a hierarchy.

```text
Application

↓

Component Tree

↓

Small Independent Components
```

Benefits include:

- Better organization
- Easier maintenance
- Reusability
- Team collaboration
- Predictable rendering

This is one of React's greatest strengths.

---

# Engineering Perspective

Notice what React has **not** done yet.

Even after:

- Reading components
- Converting JSX
- Creating React Elements
- Building the Component Tree

React still hasn't updated the browser.

Everything so far has happened **inside React**.

Only after React understands the complete interface does it begin interacting with the Browser DOM.

This separation allows React to make intelligent decisions before performing expensive DOM operations.

That's one of the reasons React applications remain efficient as they grow.

---

# Step 4 — React Creates the Virtual DOM

At this point, React has:

- Read your components
- Converted JSX into React Elements
- Built the Component Tree

Now React creates an in-memory representation of the user interface known as the **Virtual DOM**.

The Virtual DOM is **not** the browser's DOM.

Instead, it is a lightweight JavaScript representation of what the user interface should look like.

```text
Developer Components

        │

        ▼

React Elements

        │

        ▼

Component Tree

        │

        ▼

Virtual DOM
```

Think of the Virtual DOM as React's working copy of the interface.

Instead of modifying the browser immediately, React first updates this internal representation.

This allows React to understand exactly what has changed before touching the real browser.

> 💡 **Key Insight**
>
> The Virtual DOM exists so React can make intelligent update decisions before performing expensive browser operations.

---

# What is the Browser DOM?

Before continuing, let's understand what the browser's DOM actually is.

Whenever the browser loads an HTML page, it converts that HTML into a tree structure called the **Document Object Model (DOM).**

For example,

```html
<body>
    <h1>Hello</h1>
    <button>Click Me</button>
</body>
```

becomes something conceptually like this:

```text
Document

└── html

    └── body

        ├── h1

        └── button
```

Every visible element on the page exists inside this DOM tree.

Changing the DOM causes the browser to perform additional work such as:

- Layout
- Styling
- Painting
- Compositing

These operations can become expensive for large applications.

That's why React tries to minimize unnecessary DOM updates.

---

# Virtual DOM vs Browser DOM

Although their names are similar, they have different responsibilities.

| Virtual DOM | Browser DOM |
|--------------|-------------|
| JavaScript Object | Browser Structure |
| Lightweight | Heavyweight |
| Managed by React | Managed by Browser |
| Fast to Compare | Expensive to Modify |
| Exists in Memory | Displays UI |

Think of it like this.

```text
Virtual DOM

↓

Planning

↓

Browser DOM

↓

Rendering
```

React first plans.

The browser then renders.

---

# Step 5 — Initial Render

When a React application loads for the first time, React performs an **Initial Render**.

During this process, React builds the complete interface from scratch.

The high-level workflow looks like this:

```text
React Component

↓

React Element

↓

Component Tree

↓

Virtual DOM

↓

Browser DOM

↓

Visible UI
```

This process only happens once when the application starts.

After the initial render, React tries to reuse as much of the existing interface as possible.

This makes future updates much more efficient.

---

# What Happens During Initial Render?

Let's follow the process step by step.

Imagine the following component.

```jsx
function App() {
    return (
        <div>
            <h1>Hello React</h1>
            <button>Click Me</button>
        </div>
    );
}
```

React performs the following operations.

### 1. Read the Component

```text
App()
```

↓

React executes the component function.

---

### 2. Create React Elements

```text
div

↓

h1

↓

button
```

React now understands the interface.

---

### 3. Build Component Tree

```text
App

└── div

     ├── h1

     └── button
```

---

### 4. Create Virtual DOM

React creates its internal representation.

Nothing has appeared in the browser yet.

---

### 5. Create Browser DOM

React now creates the corresponding browser nodes.

```text
DOM

div

├── h1

└── button
```

---

### 6. Browser Paints

Finally, the browser displays the interface.

```text
User

↓

Sees

Hello React

[ Click Me ]
```

The first render is complete.

---

# Step 6 — Browser Paint

Creating DOM nodes is not the final step.

The browser must still display them.

After React updates the DOM, the browser performs rendering work.

This typically involves:

```text
DOM Updated

↓

Calculate Layout

↓

Apply CSS

↓

Paint Pixels

↓

Display Screen
```

These browser operations are outside React's control.

React's responsibility ends after updating the DOM.

The browser is responsible for displaying the final result.

---

# Why React Doesn't Update the Browser Immediately

A common beginner question is:

> Why doesn't React update the DOM as soon as something changes?

Imagine an application where five different values change almost simultaneously.

Without React's approach:

```text
Change 1

↓

DOM Update

↓

Change 2

↓

DOM Update

↓

Change 3

↓

DOM Update

↓

Change 4

↓

DOM Update

↓

Change 5

↓

DOM Update
```

This results in multiple expensive browser updates.

Instead, React first understands all changes before updating the browser.

Conceptually:

```text
Multiple State Changes

↓

React Collects Changes

↓

Virtual DOM Updated

↓

Compare Changes

↓

Single Efficient DOM Update
```

This batching strategy helps reduce unnecessary work and improves overall application performance.

> 🚀 **Engineering Tip**
>
> Updating JavaScript objects in memory is generally much cheaper than repeatedly modifying the browser's DOM.
>
> React takes advantage of this by performing as much work as possible before interacting with the browser.

---

# What Happens When State Changes?

So far, we've learned how React performs the **Initial Render** and displays the application for the first time.

However, modern web applications are interactive.

Users constantly perform actions such as:

- Clicking buttons
- Typing into forms
- Searching for products
- Adding items to a shopping cart
- Opening dialogs
- Switching tabs

Every interaction changes the application's data.

In React, these data changes are called **State Updates**.

Whenever state changes, React begins another rendering cycle to ensure the user interface reflects the latest application state.

---

# A Simple Example

Imagine a counter application.

Initially:

```text
Count = 0

↓

Screen

Count: 0
```

The user clicks the **Increment** button.

```text
User Click

↓

Count = 1
```

At this point, React notices that the application's state has changed.

Instead of manually updating the `<h1>` element displaying the count, React automatically starts a new rendering process.

---

# React's Update Cycle

Whenever state changes, React follows a predictable workflow.

```text
User Interaction

        │

        ▼

State Changes

        │

        ▼

React Re-renders Components

        │

        ▼

Creates New Virtual DOM

        │

        ▼

Compares with Previous Virtual DOM

        │

        ▼

Updates Browser DOM

        │

        ▼

Browser Paints Updated UI
```

This process happens so quickly that users usually don't notice it.

---

# Initial Render vs Re-render

One of the most important concepts in React is understanding the difference between these two terms.

## Initial Render

Occurs only once.

```text
Application Starts

↓

React Builds Entire UI

↓

Browser Displays Page
```

---

## Re-render

Occurs whenever React needs to update the interface.

Examples include:

- State changes
- Props changes
- Context updates
- Parent component updates

```text
State Changes

↓

React Re-renders

↓

UI Updates
```

A React application typically performs **one Initial Render** and **many Re-renders** throughout its lifetime.

---

# Does React Rebuild the Entire Page?

This is one of the biggest misconceptions among beginners.

The answer is:

> **No.**

React may execute component functions again, but it does **not** recreate the entire browser page every time.

Instead, React compares the previous UI with the new UI and updates only the parts that have changed.

For example:

```text
Dashboard

├── Header

├── Sidebar

├── Statistics

├── Orders

└── Footer
```

Suppose only the statistics section changes.

React does **not** rebuild the entire dashboard.

Instead:

```text
Dashboard

├── Header

├── Sidebar

├── Statistics   ← Updated

├── Orders

└── Footer
```

Only the affected part of the interface is updated.

This selective updating is one of React's biggest advantages.

---

# Why React Re-renders Components

Many beginners think:

> "Re-render" means React updates the browser immediately.

That's not entirely accurate.

A **Re-render** simply means React executes component functions again to determine what the user interface should look like now.

For example:

```jsx
function Counter() {
    return <h1>Count</h1>;
}
```

Whenever the component's state changes, React executes the `Counter()` function again.

It generates a new description of the UI.

Only after comparing the old and new descriptions does React decide whether the browser actually needs updating.

This distinction is important:

```text
Re-render

≠

DOM Update
```

React can re-render a component without changing the browser if the rendered output remains the same.

---

# The Comparison Process

After a component re-renders, React now has two versions of the interface.

```text
Previous Virtual DOM

        │

        ▼

Current Virtual DOM
```

React compares both versions.

```text
Old UI

↓

Compare

↓

New UI
```

If nothing has changed:

```text
No DOM Update
```

If differences exist:

```text
Update Only Changed Nodes
```

This comparison process is called **Reconciliation**, which we'll explore in the next section.

---

# Real-World Example

Imagine an online shopping application.

The user adds one product to the cart.

Should React rebuild:

- Navigation?
- Footer?
- Product List?
- User Profile?
- Search Bar?

Of course not.

Only the cart-related interface needs updating.

```text
User Adds Product

↓

Cart State Changes

↓

Cart Component Re-renders

↓

React Detects Difference

↓

Cart Count Updates

↓

Total Price Updates
```

Everything else remains unchanged.

This selective updating is what makes React efficient.

---

# Engineering Perspective

One of React's greatest innovations is separating **rendering** from **updating the browser**.

Instead of immediately modifying the DOM whenever data changes, React first asks:

> "What should the interface look like now?"

Only after answering that question does React determine whether the browser actually needs updating.

This separation allows React to avoid unnecessary DOM operations and provides a consistent, predictable programming model.

Understanding this idea is essential because many future topics—such as memoization, performance optimization, Hooks, and lifecycle behavior—depend on it.

---

> 💡 **Key Insight**
>
> A component re-render does **not** automatically mean the browser DOM changes.
>
> React first compares the new UI with the previous UI and updates the browser only if necessary.

---

# Reconciliation (High-Level)

In the previous section, we learned that whenever state changes, React creates a **new Virtual DOM**.

At this point, React has two versions of the user interface.

```text
Old Virtual DOM

        │

        ▼

Compare

        ▲

        │

New Virtual DOM
```

React now needs to answer one important question:

> **"What actually changed?"**

The process of comparing the previous Virtual DOM with the new Virtual DOM is called **Reconciliation**.

React uses this comparison to determine the smallest set of changes required to update the browser.

Instead of rebuilding the entire page, React updates only the elements that have changed.

For example, consider a shopping cart.

### Before

```text
Cart Items : 2

Total : $150
```

### After

```text
Cart Items : 3

Total : $220
```

React doesn't recreate the entire application.

Instead, it identifies only the changed values.

```text
Navigation

Header

Cart Count        ✅ Changed

Total Price       ✅ Changed

Product List

Footer
```

Only the affected DOM nodes are updated.

This process happens automatically and is one of React's most powerful optimizations.

> 💡 **We'll explore Reconciliation in detail later.**
>
> For now, it's enough to understand that React compares two versions of the UI before updating the browser.

---

# Complete React Rendering Flow

Let's combine everything we've learned into one complete workflow.

```text
Developer Writes Component

        │

        ▼

JSX

        │

        ▼

React Elements

        │

        ▼

Component Tree

        │

        ▼

Virtual DOM

        │

        ▼

Browser DOM

        │

        ▼

Browser Paint

        │

        ▼

User Interaction

        │

        ▼

State Changes

        │

        ▼

Component Re-renders

        │

        ▼

New Virtual DOM

        │

        ▼

Reconciliation

        │

        ▼

DOM Updates

        │

        ▼

Browser Paint

        │

        ▼

Updated User Interface
```

Although this appears to be a long process, modern browsers and React perform these operations extremely quickly.

Most updates happen in just a few milliseconds.

---

# How React Thinks

One of the biggest mindset changes when learning React is understanding how React approaches user interface development.

Traditional JavaScript asks:

> Which HTML element should I update?

React asks:

> Given the current application data, what should the user interface look like?

This difference is fundamental.

Traditional development often looks like this:

```text
Find Element

↓

Update HTML

↓

Update CSS

↓

Update DOM
```

React follows a different model.

```text
Current State

↓

Render Components

↓

Compare UI

↓

Update Browser
```

This declarative approach allows developers to focus on business logic while React manages UI synchronization.

---

# Engineering Perspective

React's rendering model provides several important advantages.

## Predictability

The interface always reflects the current application state.

Developers don't need to manually synchronize multiple HTML elements.

---

## Maintainability

Applications are divided into reusable components.

Each component manages its own portion of the user interface.

---

## Performance

React minimizes unnecessary DOM updates by comparing the previous and current Virtual DOM before updating the browser.

---

## Scalability

The same rendering model works for both small applications and large enterprise systems.

Whether an application contains 10 components or 10,000 components, React follows the same predictable workflow.

This consistency makes large applications easier to develop and maintain.

---

# Best Practices

As you continue learning React, keep these recommendations in mind.

- Think in components rather than pages.
- Focus on application state instead of DOM manipulation.
- Don't manually update the DOM inside React components.
- Understand rendering before learning performance optimizations.
- Learn concepts before memorizing APIs.

A strong understanding of React's rendering process will make advanced topics much easier to learn.

---

# Common Mistakes

### ❌ Assuming React Updates the Entire Page

React updates only the parts of the interface that have changed.

---

### ❌ Confusing Re-render with DOM Updates

A component may re-render even when no browser DOM changes are required.

---

### ❌ Thinking the Virtual DOM Replaces the Browser DOM

The Virtual DOM is React's internal representation.

The Browser DOM is what users actually see.

---

### ❌ Trying to Manually Manipulate the DOM

React is designed to manage the user interface.

Direct DOM manipulation should generally be avoided unless working with specific browser APIs or third-party libraries.

---

# Summary

React follows a predictable rendering pipeline.

When developers write components, React converts them into React Elements, builds a Component Tree, creates a Virtual DOM, and renders the Browser DOM.

After the application is running, every user interaction that changes state starts another rendering cycle.

React compares the previous and current Virtual DOM through a process called Reconciliation and updates only the parts of the Browser DOM that have changed.

Understanding this rendering model provides the foundation for learning Components, JSX, State, Hooks, Lifecycle, Performance Optimization, and React Architecture.

Almost every advanced React concept builds upon the workflow introduced in this article.

---

# Knowledge Check

Before moving to the next article, make sure you can answer the following questions.

## Understanding

1. What happens after you write a React component?
2. What is a React Element?
3. What is the Component Tree?
4. What is the Virtual DOM?
5. What is the Browser DOM?

## Rendering

6. What is the Initial Render?
7. What causes a Re-render?
8. Does React rebuild the entire page after every state update?

## Engineering

9. What is Reconciliation?
10. Why does React compare two Virtual DOM trees?
11. Why doesn't React update the Browser DOM immediately?
12. Why is declarative programming easier to maintain?

If you can confidently answer these questions, you've built a strong mental model of React's rendering process.

---

# Further Reading

Continue strengthening your understanding with these related topics.

- 📖 What is React?
- 📖 Why React?
- 📖 History of React

The next article builds directly on the concepts introduced here.

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← History of React | ↑ React Fundamentals | 🗺 React Learning Path | React Ecosystem → |

---

# Continue Your Journey

Congratulations!

You now understand one of the most important concepts in React:

**How React transforms your code into a user interface and keeps that interface synchronized with application state.**

This mental model will help you understand every React concept that follows.

In the next article, you'll explore the broader **React Ecosystem** and learn about the tools and libraries that work alongside React in real-world applications.

- ⬅ **Previous:** [03 - History of React](03-history-of-react.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [05 - React Ecosystem](05-react-ecosystem.md)