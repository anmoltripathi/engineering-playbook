# Components

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
> → Components

---

# Overview

In the previous chapter, you learned that every JSX expression becomes a **React Element**.

However, React applications are not built by manually creating thousands of React Elements.

Instead, developers create **Components**.

Components are the primary building blocks of every React application.

They allow developers to organize user interfaces into small, reusable, and independent pieces.

Rather than thinking about an application as one large page, React encourages you to think in terms of components.

This component-based architecture is one of React's greatest strengths and is the foundation of modern frontend development.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Components |
| Level | Beginner → Intermediate |
| Reading Time | 60–75 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | JSX, React Elements |
| Next Topic | Rendering |

---

# Why This Matters

Every React application is ultimately composed of components.

Whether you're building:

- A button
- A navigation bar
- A login page
- A dashboard
- An e-commerce application

everything begins with components.

Without components, React would simply be a library for creating React Elements.

Components make React scalable.

They allow applications to grow from a few lines of code to millions of lines while remaining maintainable.

---

# Learning Objectives

After completing this article, you'll be able to:

- Explain what a React Component is.
- Understand why components exist.
- Distinguish Components from React Elements.
- Create function components.
- Compose components together.
- Follow React component naming conventions.
- Build reusable UI structures.
- Understand the component hierarchy.

---

# Before Components

Imagine building a webpage without components.

You might write:

```jsx
<header>
    ...
</header>

<main>
    ...
</main>

<footer>
    ...
</footer>
```

Now imagine repeating this structure across dozens of pages.

Problems quickly appear:

- Duplicate code
- Difficult maintenance
- Inconsistent UI
- Poor scalability

As applications grow, manually repeating UI becomes impractical.

---

# The Idea Behind Components

A component allows you to package UI into a reusable unit.

Instead of rewriting the same markup, you define it once and reuse it wherever needed.

Conceptually:

```text
Create Once

↓

Reuse Anywhere

↓

Maintain Once
```

This approach reduces duplication and keeps applications organized.

---

# What is a React Component?

A React Component is a JavaScript function that returns React Elements.

This is one of the most important definitions in React.

Notice what it does **not** return:

- HTML
- DOM Nodes
- Browser Elements

It returns **React Elements**.

Example:

```jsx
function Welcome() {
    return <h1>Welcome</h1>;
}
```

Flow:

```text
Component

↓

Execute Function

↓

Return React Elements

↓

React Renders UI
```

---

# Components Build Applications

Applications are simply collections of components.

Example:

```text
App

├── Header

├── Sidebar

├── Dashboard

│   ├── Statistics

│   ├── Chart

│   └── Activity

└── Footer
```

Every box in this diagram is another React component.

Together they form the complete application.

---

# Components vs React Elements

This is one of the most misunderstood concepts.

| Component | React Element |
|-----------|---------------|
| JavaScript Function | JavaScript Object |
| Can contain logic | Contains UI description |
| Reusable | Immutable |
| Returns React Elements | Rendered by React |

Relationship:

```text
Component

↓

Returns

↓

React Element

↓

React

↓

Browser DOM
```

A component creates React Elements.

A React Element describes the UI.

React renders the UI.

---

# Function Components

Modern React applications primarily use **Function Components**.

Example:

```jsx
function Greeting() {
    return (
        <h1>Hello React</h1>
    );
}
```

Arrow function syntax is also common:

```jsx
const Greeting = () => {
    return (
        <h1>Hello React</h1>
    );
};
```

Both produce the same result.

Function Components are now the recommended approach for building React applications.

---

# Naming Components

React distinguishes components from HTML elements based on naming.

Native HTML:

```jsx
<div>
```

React Component:

```jsx
<Dashboard />
```

Rule:

- HTML elements start with lowercase letters.
- React Components start with uppercase letters.

Incorrect:

```jsx
function dashboard() {}
```

Correct:

```jsx
function Dashboard() {}
```

This naming convention allows React to determine whether a JSX tag represents a browser element or a custom component.

---

# Component Composition

One of React's most powerful ideas is **composition**.

Instead of building one large component that contains everything, React encourages developers to build many small components and combine them together.

Think of components like LEGO® bricks.

Each brick has a single purpose.

When combined, they can build something much larger.

Conceptually:

```text
Button

+

Input

+

Card

+

Modal

↓

User Profile
```

Every large application is simply a collection of smaller components working together.

---

# Why Composition Matters

Imagine building an e-commerce application.

Without components:

```text
Product Page

↓

2000 Lines of Code
```

Finding bugs becomes difficult.

Reusing code becomes nearly impossible.

Now imagine the same page built using components.

```text
Product Page

├── Header

├── Product Gallery

├── Product Information

├── Reviews

├── Similar Products

└── Footer
```

Each component has one responsibility.

This makes the application easier to:

- Read
- Test
- Maintain
- Reuse
- Scale

---

# Parent and Child Components

Components often contain other components.

Example:

```jsx
function App() {
    return (
        <>
            <Header />
            <Dashboard />
            <Footer />
        </>
    );
}
```

Conceptually:

```text
App

├── Header

├── Dashboard

└── Footer
```

Here:

- `App` is the parent component.
- `Header`, `Dashboard`, and `Footer` are child components.

This hierarchy forms the application's **Component Tree**.

---

# Nested Components

Components can be nested many levels deep.

Example:

```text
App

├── Header

│   ├── Logo

│   └── Navigation

│

├── Dashboard

│   ├── Sidebar

│   ├── Statistics

│   └── Activity Feed

│

└── Footer
```

Every component can contain additional components.

This hierarchical structure makes complex interfaces manageable.

---

# Reusable Components

A good component is designed to be reused.

Example:

Instead of writing three buttons manually:

```jsx
<button>Save</button>

<button>Cancel</button>

<button>Delete</button>
```

Create one reusable component.

```jsx
<Button />

<Button />

<Button />
```

Later you'll learn how **Props** make each button unique.

Reusability reduces duplication and improves consistency.

---

# Component Hierarchy

A React application is not a collection of pages.

It is a hierarchy of components.

Example:

```text
Application

↓

App

↓

Dashboard

↓

Sidebar

↓

Navigation Item
```

Every level of the hierarchy has a specific responsibility.

Thinking in hierarchies helps organize large applications.

---

# Breaking Down a UI

One of the first skills every React engineer develops is learning how to break a design into components.

Imagine this dashboard.

```text
--------------------------------

Header

--------------------------------

Sidebar | Main Content

        | Statistics

        | Chart

        | Recent Activity

--------------------------------

Footer

--------------------------------
```

Rather than building it as one component:

```text
Dashboard
```

Break it into smaller pieces.

```text
Dashboard

├── Header

├── Sidebar

├── Main

│   ├── Statistics

│   ├── Chart

│   └── Activity

└── Footer
```

This approach makes every part easier to maintain independently.

---

# Single Responsibility Principle

A useful engineering principle is:

> A component should have one clear responsibility.

Examples:

Good:

```text
UserAvatar
```

Displays only the user's avatar.

Good:

```text
NavigationMenu
```

Displays navigation links.

Poor:

```text
DashboardEverythingManagerComponent
```

Handles navigation, API calls, forms, charts, authentication, and settings.

Large components become difficult to understand and maintain.

---

> 🏗️ Engineering Note
>
> If a component becomes difficult to explain in one sentence, it may have more than one responsibility.
>
> Splitting large components into smaller ones often improves readability, testability, and reusability.

---

# Components Are Independent

Each component should manage only the logic it needs.

For example:

```text
Header

↓

Logo

Navigation

User Menu
```

The `Header` component shouldn't know how the `Chart` component works.

Keeping components independent reduces coupling between different parts of the application.

---

# Components Can Be Combined Infinitely

Small components can be combined to create increasingly complex interfaces.

Example:

```text
Button

↓

Form

↓

Login Page

↓

Authentication Module

↓

Entire Application
```

This composability is one of the reasons React scales well for both small and enterprise applications.

---

# Real-World Example

Consider a social media feed.

Instead of building one enormous component:

```text
Feed
```

Build a hierarchy.

```text
Feed

├── Post

│   ├── UserInfo

│   ├── Content

│   ├── Image

│   ├── Like Button

│   └── Comments

├── Post

├── Post

└── Post
```

Each part can evolve independently without affecting the others.

---

# Engineering Perspective

React is fundamentally a **component-based architecture**.

The goal is not simply to split code into smaller files.

The goal is to create independent, reusable building blocks that can be combined to build complex user interfaces.

When developers think in components instead of pages, applications become easier to understand, extend, and maintain.

This mindset becomes increasingly important as projects grow from a few components to hundreds or even thousands.

---

# Best Practices

Following a few simple principles can make your components easier to understand, maintain, and scale.

---

## Keep Components Small

Avoid creating components that handle multiple responsibilities.

Instead of:

```text
Dashboard

↓

Everything
```

Prefer:

```text
Dashboard

├── Header

├── Sidebar

├── Statistics

├── Chart

└── Footer
```

Smaller components are easier to:

- Read
- Test
- Reuse
- Maintain

---

## Give Components Meaningful Names

Component names should describe **what they represent**, not how they are implemented.

Good Examples

```text
UserCard

Navigation

ProductGrid

CheckoutForm

ProfileAvatar
```

Avoid names like:

```text
Data

Component1

Test

MyComponent

Temp
```

Meaningful names improve code readability.

---

## Keep Components Focused

Each component should solve one problem.

For example:

```text
SearchBox

↓

Input

Button

Search Logic
```

Avoid mixing unrelated responsibilities such as:

- Authentication
- API Calls
- Dashboard Charts
- User Settings

inside one component.

---

## Prefer Composition Over Duplication

If the same UI appears multiple times:

❌ Copy it.

✅ Convert it into a reusable component.

Example:

```text
User Card

↓

Profile Page

Dashboard

Team Page

Search Results
```

One reusable component can serve many pages.

---

## Organize Components Logically

Large applications benefit from clear organization.

Example:

```text
Dashboard

├── Header

├── Sidebar

├── Widgets

├── Charts

└── Footer
```

Avoid storing unrelated components together.

---

## Keep Rendering Logic Simple

A component's primary responsibility is to describe the UI.

If rendering becomes difficult to read, consider extracting parts into smaller components.

Example:

Instead of:

```text
800-line Component
```

Prefer:

```text
Dashboard

↓

Statistics

↓

StatisticsCard

↓

Value
```

---

# Common Mistakes

## Creating Huge Components

Large components quickly become difficult to understand.

Bad:

```text
Dashboard

↓

2000 Lines
```

Good:

```text
Dashboard

↓

10 Small Components
```

---

## Deeply Nested JSX

Too much nesting reduces readability.

Example:

```text
div

↓

div

↓

section

↓

article

↓

div

↓

...
```

Break deeply nested structures into smaller components.

---

## Duplicating UI

If you copy and paste the same JSX multiple times,

it's usually a signal that a reusable component should exist.

---

## Confusing Components with Pages

Pages are typically composed of many components.

Example:

```text
Home Page

↓

Header

↓

Hero

↓

Features

↓

Testimonials

↓

Footer
```

Pages organize components.

Components build pages.

---

## Ignoring Reusability

Before creating a new component, ask:

> Can an existing component solve this problem?

Reusing components improves consistency and reduces maintenance.

---

# Real-World Architecture Example

Imagine building an online learning platform.

Instead of:

```text
LearningPage.jsx
```

with thousands of lines,

design a component hierarchy.

```text
LearningPage

├── Header

├── Sidebar

│   ├── Navigation

│   └── Progress

├── LessonArea

│   ├── VideoPlayer

│   ├── Notes

│   ├── Attachments

│   └── Discussion

└── Footer
```

Every component has a clearly defined responsibility.

This architecture is significantly easier to evolve over time.

---

> 🏛️ Architecture Insight
>
> Modern React applications are built by composing many small components into larger features.
>
> Feature-level composition improves maintainability, enables independent development, and reduces the impact of changes across the application.
>
> Throughout this playbook, you'll repeatedly see this principle applied in production-ready architectures.

---

# Interview Questions

## Beginner

### 1. What is a React Component?

---

### 2. Why do we use components?

---

### 3. What does a React Component return?

---

### 4. What is the difference between a Component and a React Element?

---

### 5. Why should component names start with an uppercase letter?

---

## Intermediate

### 6. Explain component composition.

---

### 7. What is the relationship between parent and child components?

---

### 8. What is the Single Responsibility Principle in React?

---

### 9. How do components improve maintainability?

---

### 10. How do reusable components reduce technical debt?

---

## Advanced

### 11. How would you break down a complex dashboard into reusable components?

---

### 12. When should a component be split into multiple smaller components?

---

### 13. Why is composition preferred over inheritance in React?

---

### 14. What characteristics define a well-designed React component?

---

# Hands-on Exercises

## Exercise 1

Take a simple webpage and identify all possible components.

Draw the component hierarchy.

---

## Exercise 2

Break a login page into reusable components.

Example:

```text
LoginPage

├── Logo

├── LoginForm

│   ├── EmailInput

│   ├── PasswordInput

│   └── SubmitButton

└── Footer
```

---

## Exercise 3

Take an existing React component with more than 200 lines.

Refactor it into smaller reusable components.

Explain why each new component exists.

---

## Exercise 4

Design the component hierarchy for one of the following:

- E-commerce Product Page
- Social Media Feed
- Admin Dashboard
- Banking Application

---

# Summary

Components are the foundation of every React application.

In this chapter, you learned that:

- Components are JavaScript functions.
- Components return React Elements.
- Components enable reusable UI.
- Components can be composed into larger interfaces.
- Applications are built as hierarchies of components.
- Small, focused components are easier to maintain than large monolithic ones.

By thinking in components instead of pages, you can build applications that scale from simple interfaces to enterprise systems.

---

# Knowledge Check

Before moving to the next chapter, make sure you can answer the following:

- What is a React Component?
- What does a component return?
- How is a Component different from a React Element?
- Why are components reusable?
- What is component composition?
- Why is the Single Responsibility Principle important?
- How would you divide a complex page into reusable components?

If you can confidently explain these concepts, you're ready to learn how React transforms component trees into a visible user interface.

---

# Further Reading

- 📖 Rendering
- 📖 Virtual DOM
- 📖 Reconciliation

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← React Elements | ↑ React Core Concepts | 🗺 Module Home | Rendering → |

---

# Continue Your Journey

You now understand how React applications are built using reusable components.

In the next chapter, you'll learn **Rendering**—the process through which React executes components, creates React Elements, and updates the user interface efficiently.

This chapter connects everything you've learned so far:

```
JSX

↓

React Elements

↓

Components

↓

Rendering
```

Once you understand rendering, concepts like the Virtual DOM, Reconciliation, and React Fiber will become much easier to grasp.

- ⬅ **Previous:** [02 - React Elements](02-react-elements.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [04 - Rendering](04-rendering.md)