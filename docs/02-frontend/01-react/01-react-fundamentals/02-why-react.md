---

# Why Facebook Built React

React was originally created by engineers at Facebook to solve a practical engineering problem rather than to create a new JavaScript trend.

As Facebook grew, its applications became increasingly interactive.

Features such as:

- News Feed
- Comments
- Likes
- Notifications
- Chat
- User Profiles

were constantly updating while users interacted with the application.

Keeping all of these interface elements synchronized using traditional DOM manipulation became increasingly difficult.

Every new feature introduced additional complexity, and maintaining consistency across the user interface required significant engineering effort.

Facebook needed a better approach.

The engineering team introduced React with a simple but powerful idea:

> **The user interface should be a function of the application's data.**

Instead of manually updating every HTML element, developers would update the application's state, and React would determine how the interface should change.

This shift dramatically simplified UI development and laid the foundation for modern frontend engineering.

---

# Problems React Solves

React addresses several challenges that arise when building modern web applications.

## 1. Managing Complex User Interfaces

Modern applications consist of many independent sections that update at different times.

For example, an e-commerce application may contain:

```text
Application

├── Header
├── Navigation
├── Search
├── Filters
├── Product Grid
├── Shopping Cart
├── Wishlist
├── User Profile
└── Notifications
```

Without a structured architecture, keeping these sections synchronized quickly becomes difficult.

React solves this by organizing the interface into reusable components.

---

## 2. Reducing Manual DOM Updates

Traditional JavaScript requires developers to locate and modify DOM elements directly.

```text
Change Data

↓

Find DOM Element

↓

Update HTML

↓

Update CSS

↓

Repeat
```

React replaces this with a declarative approach.

```text
Change State

↓

React Calculates Changes

↓

UI Updates Automatically
```

Developers focus on the application's data rather than DOM operations.

---

## 3. Improving Code Reusability

Imagine creating a button for an application.

Without reusable components, the same HTML, CSS, and JavaScript might be duplicated across dozens of pages.

With React, the button becomes a reusable component.

```text
<Button />
```

The same component can be used throughout the application while maintaining a consistent appearance and behavior.

This reduces duplication and simplifies maintenance.

---

## 4. Making Applications Easier to Scale

As applications grow, organizing code becomes increasingly important.

React encourages developers to divide large applications into small, focused components.

Instead of managing one large file, teams work with independent modules that are easier to develop, test, and maintain.

---

## 5. Predictable User Interfaces

One of React's greatest strengths is predictability.

The interface always reflects the current application state.

When the underlying data changes, React updates the interface accordingly.

This reduces many common bugs caused by inconsistent UI updates.

---

# Core Benefits of React

React became popular because it introduced several engineering practices that improve the developer experience.

## Component-Based Architecture

Applications are divided into reusable building blocks.

This improves:

- Maintainability
- Reusability
- Collaboration
- Scalability

---

## Declarative Programming

Developers describe the desired interface.

React determines how to update the browser efficiently.

This makes code easier to understand compared to manually manipulating DOM elements.

---

## Reusability

Components can be reused throughout an application.

Examples include:

- Buttons
- Navigation Bars
- Product Cards
- Forms
- Tables
- Dialogs

Writing a component once and using it many times improves consistency and reduces duplicate code.

---

## Strong Ecosystem

React has one of the largest frontend ecosystems.

Popular tools include:

- React Router
- Vite
- Next.js
- Zustand
- Redux Toolkit
- TanStack Query
- React Hook Form
- Testing Library

Developers can choose the tools that best fit their project's requirements.

---

## Excellent Developer Experience

React offers features that improve productivity, such as:

- Fast Refresh
- Component-based development
- Rich DevTools
- Large community
- Extensive documentation

These capabilities make development faster and debugging easier.

---

# Real-World Comparison

Imagine you're building a dashboard.

### Traditional Approach

```text
Dashboard.html

↓

Locate Sidebar

↓

Update Sidebar

↓

Locate Header

↓

Update Header

↓

Locate Statistics

↓

Update Statistics

↓

Locate Notifications

↓

Update Notifications
```

Every update requires manual coordination.

---

### React Approach

```text
Dashboard

│

├── Sidebar

├── Header

├── Statistics

├── Notifications

└── Footer
```

When the application's data changes:

```text
Update State

↓

React Determines What Changed

↓

Only Affected Components Re-render

↓

UI Remains Consistent
```

Developers spend less time managing the interface and more time implementing business features.

---

# React Isn't a Silver Bullet

Although React is an excellent choice for many applications, it is not the perfect solution for every project.

For example:

- A static marketing page may not require React.
- A small documentation website can often be built with static HTML or a static site generator.
- Very small projects may benefit from simpler solutions.

Choosing React should be based on project requirements rather than popularity.

Good engineers select the right tool for the problem.

---

# Engineering Perspective

One reason React has been widely adopted is that it aligns well with how software teams build large applications.

Instead of organizing code around pages, React encourages organizing code around reusable features.

For example, a shopping cart component can be reused in:

- Product Details
- Checkout
- Mobile View
- Order Summary

This reduces duplication and makes applications easier to maintain over time.

For engineering teams working on large products, this modular approach improves collaboration because different developers can work on different components without affecting unrelated parts of the application.
---

# Best Practices

As you begin your React journey, keep these best practices in mind.

## Learn JavaScript Before React

React is built on top of JavaScript.

A strong understanding of JavaScript fundamentals—including functions, objects, arrays, modules, promises, and asynchronous programming—will make learning React significantly easier.

Avoid treating React as a replacement for JavaScript.

---

## Understand the "Why" Before the "How"

Many beginners jump directly into learning Hooks, state management libraries, or UI frameworks.

Instead, first understand:

- Why React exists
- What problems it solves
- How React thinks
- Why React uses components
- Why React encourages declarative programming

A strong conceptual foundation makes advanced topics much easier to understand.

---

## Think in Components

Don't think about building pages.

Think about building reusable pieces.

Instead of asking:

> "How do I build this page?"

Ask:

> "What reusable components make up this page?"

For example:

```text
Dashboard

├── Header

├── Sidebar

├── Search Bar

├── Statistics Card

├── Chart

├── Recent Orders

└── Footer
```

This mindset is fundamental to React development.

---

## Build Small Projects Frequently

Reading documentation alone is not enough.

After learning each concept, build something practical.

Examples:

- Counter App
- Todo App
- Notes App
- Calculator
- Weather App
- Expense Tracker

Small projects reinforce concepts far more effectively than passive reading.

---

## Avoid Learning Too Many Libraries Too Early

React's ecosystem is enormous.

However, don't rush into learning:

- Redux
- Zustand
- Next.js
- TanStack Query
- React Hook Form

Before you understand:

- Components
- Props
- State
- Rendering
- Hooks

Master the fundamentals first.

---

# Common Mistakes

Many beginners encounter similar challenges when learning React.

Understanding these mistakes early will help you avoid frustration.

---

## ❌ Skipping JavaScript Fundamentals

React uses JavaScript extensively.

Trying to learn React without understanding JavaScript often leads to confusion.

Always strengthen your JavaScript knowledge alongside React.

---

## ❌ Memorizing Instead of Understanding

Avoid memorizing code snippets.

Instead, understand:

- Why React behaves the way it does.
- Why components exist.
- Why state changes trigger updates.

Conceptual understanding lasts much longer than memorized syntax.

---

## ❌ Copying Tutorials Without Practice

Following tutorials is useful, but real learning happens when you build something yourself.

After every topic, create a small application without looking at the tutorial.

---

## ❌ Building Large Projects Too Early

Start with small applications.

As your understanding grows, gradually increase project complexity.

Trying to build a complex dashboard on your first day usually leads to frustration.

---

## ❌ Thinking React Solves Every Problem

React is an excellent UI library, but not every project requires React.

Good engineers choose technology based on project requirements rather than trends.

---

# Summary

React was created to solve the growing complexity of building interactive user interfaces.

Instead of manually manipulating the DOM, React introduced a declarative, component-based approach that keeps the user interface synchronized with application data.

By organizing applications into reusable components, React makes code easier to understand, maintain, and scale.

Its flexibility, strong ecosystem, and focus on developer productivity have made it one of the most widely adopted frontend technologies.

Understanding *why* React exists is essential because it explains the reasoning behind many of the concepts you'll encounter throughout the rest of this playbook.

---

# Knowledge Check

Before continuing, make sure you can confidently answer the following questions.

### Understanding

1. Why was React created?
2. What challenges existed before React?
3. What is manual DOM manipulation?
4. How does React simplify UI development?

### Concepts

5. What does declarative programming mean?
6. Why are components important?
7. Why is code reusability valuable?
8. Why do large applications benefit from React?

### Engineering

9. Why do companies choose React?
10. Is React the right choice for every project? Why or why not?

If you can answer these questions without referring back to the article, you're ready to move on.

---

# Further Reading

Before continuing, you may also revisit:

- 📖 What is React?
- 📖 React Fundamentals
- 🗺 React Learning Path

These articles reinforce the concepts discussed here.

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← What is React | ↑ React Fundamentals | 🗺 React Learning Path | History of React → |

---

# Continue Your Journey

Congratulations! You now understand:

- Why React was created
- The problems it solves
- Why it became popular
- When React is a good choice
- The engineering principles behind React

You're now ready to learn how React evolved over time.

➡ **Next Article:** **03 - History of React**

Or revisit the previous article if you'd like to strengthen your understanding before moving forward.

- ⬅ **Previous:** [01 - What is React](01-what-is-react.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [03 - History of React](03-history-of-react.md)