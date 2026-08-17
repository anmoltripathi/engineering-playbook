# Thinking in React

> Module: React Core Concepts
>
> Reading Time: 90–120 Minutes
>
> Difficulty: 🟡 Intermediate → 🔴 Advanced
>
> ⭐ One of the Most Important Chapters in React

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
> → Thinking in React

---

# Overview

Congratulations.

You've reached the final chapter of React Core Concepts.

Until now, you've learned individual React concepts.

- JSX
- Components
- Props
- State
- Events
- Conditional Rendering
- Rendering Lists
- Keys
- Component Composition

Each chapter taught an individual tool.

However...

Professional frontend engineers don't start by writing components.

They start by solving problems.

Given a product requirement or a UI design, they ask questions such as:

- What are the reusable components?
- What data changes?
- Where should State live?
- Which components own that State?
- How does data flow?
- Which components are reusable?
- Which parts are static?
- Which parts are dynamic?

This systematic design process is called **Thinking in React**.

Thinking in React is less about React APIs and more about engineering methodology.

---

# How It Connects

```text
Requirements

↓

UI Design

↓

Thinking in React

↓

Component Tree

↓

State Design

↓

Data Flow

↓

Implementation

↓

Scalable Application
```

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Thinking in React |
| Level | Intermediate → Advanced |
| Reading Time | 90–120 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 3 Hours |
| Prerequisites | Entire React Core Concepts Module |
| Next Module | React Hooks |

---

# Why This Matters

Every React engineer performs this process daily.

Examples include:

- Building a Dashboard
- Designing an HRMS
- Creating an E-commerce Site
- Building a Banking Portal
- Creating a CRM
- Designing SaaS Applications

Thinking in React is not specific to React.

It is a problem-solving methodology that scales to large frontend applications.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Break complex UIs into components.
- Design reusable component trees.
- Identify application State.
- Decide State ownership.
- Design data flow.
- Separate static and dynamic UI.
- Translate designs into React architecture.

---

# The Problem Thinking in React Solves

Imagine someone gives you this screen.

```text
Employee Dashboard

──────────────────────────────

Search Employees

Department Filter

Employee Table

Pagination

Summary Cards

──────────────────────────────
```

Where do you begin?

Many beginners immediately start writing JSX.

Senior engineers don't.

Instead they analyze the problem first.

---

# The Engineering Workflow

Professional React development follows a repeatable process.

```text
Requirements

↓

UI Breakdown

↓

Component Tree

↓

Static Version

↓

Identify State

↓

State Ownership

↓

Data Flow

↓

Implementation

↓

Refactoring

↓

Optimization
```

Every feature follows this workflow.

---

# Step 1 — Understand the Requirements

Before writing code,

understand the business problem.

Example:

Employee Dashboard

Requirements:

- Search employees
- Filter department
- Sort table
- Pagination
- Edit employee
- Delete employee

Notice that none of these are React concepts.

They are business requirements.

React is simply a tool for implementing them.

---

# Step 2 — Break the UI into Components

Now inspect the interface.

```text
Employee Dashboard

↓

Header

↓

Search Bar

↓

Department Filter

↓

Summary Cards

↓

Employee Table

↓

Pagination

↓

Footer
```

Every distinct responsibility becomes a component.

Avoid thinking about code.

Think about responsibilities.

---

# Step 3 — Build the Component Tree

Now organize the hierarchy.

```text
App

↓

Dashboard

├── Header

├── SearchBar

├── DepartmentFilter

├── SummaryCards

├── EmployeeTable

│   └── EmployeeRow

├── Pagination

└── Footer
```

Congratulations.

You already have an application architecture.

Before writing a single line of JSX.

---

# Step 4 — Build a Static Version

Now create the UI.

No State.

No API.

No Events.

Only Props.

Example:

```text
Header

↓

SearchBar

↓

EmployeeTable

↓

Footer
```

The page doesn't work yet.

That's okay.

You're validating the structure.

This approach makes layout problems much easier to solve before introducing interactivity.

---

# Step 5 — Identify Dynamic Data

Now ask:

> What changes?

Example:

```text
Search Text

↓

Selected Department

↓

Current Page

↓

Employees

↓

Loading

↓

Error
```

These values are candidates for State.

Static values do not belong in State.

# Step 6 — Determine State Ownership

Now that you've identified the dynamic data, the next question is:

> **Which component should own each piece of State?**

This is one of the most important architectural decisions in React.

Incorrect State ownership leads to:

- Prop Drilling
- Duplicate State
- Difficult debugging
- Tight coupling
- Complex component trees

Good State ownership makes applications predictable and maintainable.

---

# The Single Source of Truth

Every piece of State should have **one owner**.

This principle is called the **Single Source of Truth**.

Instead of storing the same information in multiple components,

React encourages one component to own the data and pass it downward through Props.

Conceptually:

```text
Search Text

↓

Dashboard

↓

SearchBar

↓

EmployeeTable
```

Dashboard owns the State.

Children receive it through Props.

---

# Finding the Correct Owner

Ask two questions.

## Question 1

Who changes this data?

## Question 2

Who needs this data?

The answers determine where State belongs.

---

# Example 1

Search Text

```text
SearchBar

↓

EmployeeTable
```

SearchBar changes it.

EmployeeTable uses it.

The closest common parent is:

```text
Dashboard
```

Therefore:

```text
Dashboard

↓

searchText

├── SearchBar

└── EmployeeTable
```

Dashboard owns the State.

---

# Example 2

Modal Visibility

```text
EmployeeDetailsModal
```

Only one component uses it.

State belongs there.

```text
EmployeeDetailsModal

↓

isOpen
```

No need to move it upward.

---

# Example 3

Theme

Many components use it.

```text
Header

Sidebar

Dashboard

Settings

Footer
```

The owner becomes:

```text
App
```

Later you'll learn Context API to share this State efficiently.

---

# Rule of Thumb

Choose the **lowest common ancestor**.

Conceptually:

```text
Component A

Component B

↓

Lowest Common Parent

↓

Owns State
```

This minimizes unnecessary State sharing.

---

# Step 7 — Define Data Flow

Once State ownership is decided,

define how data moves.

React follows one-way data flow.

```text
State Owner

↓

Props

↓

Child

↓

Child

↓

UI
```

Events travel upward.

```text
Button Click

↓

Callback

↓

Parent

↓

setState()

↓

Render
```

Complete flow:

```text
Parent State

↓

Props

↓

Child

↓

User Event

↓

Callback

↓

Parent Updates State

↓

Render
```

Every React application follows this model.

---

# Example Data Flow

Employee Dashboard.

```text
Dashboard

↓

Employees

↓

EmployeeTable

↓

EmployeeRow

↓

Edit Button

↓

Click

↓

Callback

↓

Dashboard

↓

Update Employee

↓

Render
```

Notice:

Data flows down.

Events flow up.

---

# Step 8 — Build Features Incrementally

Don't build everything at once.

Instead:

```text
Layout

↓

Display Data

↓

Add State

↓

Add Events

↓

Add API

↓

Refactor

↓

Optimize
```

Each step should leave the application in a working state.

---

# Example Development Order

Employee Dashboard

```text
Header

↓

Search Bar

↓

Employee Table

↓

Pagination

↓

Loading State

↓

Error State

↓

API Integration

↓

Editing

↓

Delete

↓

Optimization
```

Avoid implementing everything simultaneously.

---

# Step 9 — Refactor

After features work,

improve the architecture.

Examples:

```text
Large Component

↓

Split Components

↓

Custom Hook

↓

Reusable Component

↓

Cleaner Structure
```

Refactoring is part of development,

not something done only at the end.

---

# Step 10 — Optimize

Optimization comes last.

Never optimize code before measuring performance.

Typical optimization order:

```text
Working Code

↓

Correct Code

↓

Readable Code

↓

Reusable Code

↓

Optimized Code
```

Premature optimization often increases complexity without improving the user experience.

---

# Complete Thinking in React Workflow

Every feature should pass through the same pipeline.

```text
Requirements

↓

Break UI

↓

Component Tree

↓

Static Version

↓

Identify State

↓

State Owner

↓

Data Flow

↓

Implementation

↓

Refactoring

↓

Optimization
```

Professional React development is a repeatable engineering process—not trial and error.

---

# Case Study 1 — Employee Dashboard

Requirements:

```text
Search

Department Filter

Employee Table

Pagination

Employee Details
```

Step 1

Component Tree

```text
Dashboard

├── SearchBar

├── DepartmentFilter

├── EmployeeTable

├── Pagination

└── EmployeeDetails
```

Step 2

Identify State

```text
searchText

department

currentPage

employees

loading

error
```

Step 3

Determine Ownership

```text
Dashboard

↓

searchText

department

currentPage

employees
```

Step 4

Data Flow

```text
Dashboard

↓

Props

↓

SearchBar

↓

EmployeeTable

↓

Pagination
```

Implementation becomes straightforward because the architecture is already defined.

---

# Case Study 2 — E-commerce Product Page

Requirements

```text
Gallery

Product Info

Quantity

Reviews

Related Products

Add to Cart
```

Component Tree

```text
ProductPage

├── Gallery

├── ProductInfo

├── QuantitySelector

├── AddToCartButton

├── Reviews

└── RelatedProducts
```

State

```text
quantity

selectedImage

loading

reviews
```

Notice that each feature owns only the State it actually needs.

---

# Case Study 3 — Chat Application

Requirements

```text
Conversation List

Messages

Message Input

Online Users
```

Component Tree

```text
Chat

├── Sidebar

├── ConversationList

├── MessageList

├── MessageInput

└── UserStatus
```

State

```text
messages

selectedConversation

typingMessage

onlineUsers
```

Again,

architecture comes before implementation.

---

> 🏗️ Engineering Note
>
> Senior React engineers rarely begin by writing JSX.
>
> They first identify components, define responsibilities, determine State ownership, and establish data flow.
>
> Once the architecture is clear, writing React code becomes a straightforward implementation task rather than a design exercise.


# Engineering Perspective

Thinking in React is not another React feature.

It is an engineering methodology.

Junior developers often think:

> "How do I write this component?"

Experienced engineers think:

> "How should this application be designed?"

This difference changes everything.

Instead of focusing on JSX first, engineers focus on:

- Requirements
- Responsibilities
- Component boundaries
- State ownership
- Data flow
- Reusability
- Maintainability

React code becomes the implementation of a well-designed architecture.

---

# Under the Hood

Imagine a product manager asks for a new feature.

```text
Feature Request

↓

Requirements

↓

UI Design

↓

Thinking in React

↓

Component Tree

↓

State Design

↓

Data Flow

↓

React Components

↓

Virtual DOM

↓

Reconciliation

↓

Browser UI
```

Notice something important.

React itself only starts near the end.

Most engineering work happens **before** writing JSX.

---

# Architecture Checklist

Before implementing any feature, walk through this checklist.

## 1. Understand the Requirement

Ask:

- What problem are we solving?
- Who uses this feature?
- What should happen?
- What are the edge cases?

Never begin with code.

---

## 2. Break the UI into Components

Every component should have one clear responsibility.

Example:

```text
Employee Dashboard

├── Header

├── SearchBar

├── Filters

├── EmployeeTable

├── Pagination

└── Footer
```

---

## 3. Draw the Component Tree

Organize the hierarchy.

```text
App

↓

Dashboard

↓

EmployeeTable

↓

EmployeeRow

↓

EmployeeActions
```

The tree often reveals reusable components before coding begins.

---

## 4. Build the Static Version

Ignore:

- State
- API
- Events

Focus only on:

- Layout
- Components
- Props

If the static UI is difficult to build, revisit the component structure.

---

## 5. Identify State

Ask:

> What changes over time?

Examples:

```text
Search Text

Loading

Error

Current Page

Selected Employee
```

Only these values should become State candidates.

---

## 6. Choose the State Owner

Ask:

```text
Who changes it?

Who reads it?
```

Find the lowest common ancestor.

Avoid duplicate State.

---

## 7. Define Data Flow

Remember React's rule.

```text
State

↓

Props

↓

Child

↓

User Event

↓

Callback

↓

Parent Updates State
```

Data flows down.

Events flow up.

---

## 8. Implement

Now write React code.

Notice how implementation becomes much easier because the architecture already exists.

---

## 9. Refactor

Once everything works,

improve the design.

Examples:

- Extract reusable components.
- Create custom hooks.
- Simplify Props.
- Remove duplicate logic.

---

## 10. Optimize

Optimization comes last.

Only optimize after measuring real bottlenecks.

---

# React Design Checklist

Use this checklist for every new feature.

```text
□ Understand Requirements

↓

□ Break UI into Components

↓

□ Draw Component Tree

↓

□ Build Static UI

↓

□ Identify State

↓

□ Choose State Owner

↓

□ Define Data Flow

↓

□ Implement

↓

□ Refactor

↓

□ Optimize

↓

□ Write Tests
```

Over time, this process becomes second nature.

---

# Best Practices

## Design Before Coding

Spend time understanding the problem before opening your editor.

Good architecture reduces future maintenance costs.

---

## Build Incrementally

Develop one working feature at a time.

Example:

```text
Layout

↓

Display Data

↓

Interactivity

↓

API

↓

Error Handling

↓

Optimization
```

Small, incremental progress makes debugging easier.

---

## Keep Components Focused

Each component should have one primary responsibility.

If a component is difficult to describe in one sentence, it may be doing too much.

---

## Minimize State

Store only what truly changes.

Compute derived values instead of storing them.

---

## Reuse Before Rewriting

If the same UI appears in multiple places,

extract it into a reusable component.

---

## Optimize Last

A working, readable solution is more valuable than a prematurely optimized one.

---

# Common Mistakes

## Mistake 1

Starting with JSX.

Beginners often code immediately.

Professionals analyze first.

---

## Mistake 2

Creating Components Too Early

Not every repeated `<div>` deserves its own component.

Extract meaningful concepts, not arbitrary code.

---

## Mistake 3

Too Much State

Avoid storing:

- Derived values
- Static configuration
- Duplicate data

Keep State minimal.

---

## Mistake 4

Wrong State Ownership

State should live in the lowest common ancestor that needs to coordinate it.

Incorrect ownership leads to unnecessary Prop Drilling or duplicated State.

---

## Mistake 5

Ignoring Reusability

When designing a component, ask:

> Could this be useful elsewhere?

Design reusable APIs where appropriate.

---

# Real-World Example

Let's revisit the Employee Dashboard.

```text
Requirements

↓

Employee Dashboard

↓

Break UI

↓

Header

Search

Filters

Table

Pagination

↓

Component Tree

↓

Identify State

↓

searchText

department

page

employees

↓

Choose State Owner

↓

Dashboard

↓

Implement

↓

Refactor

↓

Optimize
```

This workflow scales whether the application has 5 components or 5,000.

---

# Quick Reference

| Question | Ask Yourself |
|----------|--------------|
| What am I building? | Understand the requirement |
| What should become a component? | Look for reusable responsibilities |
| What changes? | Candidate for State |
| Who owns the State? | Lowest common ancestor |
| How does data move? | Props down, Events up |
| Is this reusable? | Consider composition |
| Should I optimize now? | Usually no |

---

# Key Takeaways

✅ Think about the problem before writing code.

✅ Break interfaces into small, focused components.

✅ Build a component tree before implementation.

✅ Keep State minimal and owned by the appropriate component.

✅ Follow one-way data flow.

✅ Build incrementally.

✅ Refactor continuously.

✅ Optimize only after measuring.

---

# Interview Questions

## Beginner

1. What is "Thinking in React"?

2. Why should you build a static version first?

3. How do you identify State?

4. What is the purpose of a component tree?

---

## Intermediate

5. How do you determine State ownership?

6. What is the Single Source of Truth?

7. Why is one-way data flow important?

8. Why should optimization come last?

---

## Advanced

9. Walk through the complete Thinking in React workflow.

10. How would you architect an Employee Management System?

11. How do you balance component reuse with simplicity?

12. How would you approach a brand-new feature from a Figma design?

---

# Hands-on Exercises

## Exercise 1

Take a login page design.

Without writing code:

- Break it into components.
- Draw the component tree.
- Identify State.
- Define data flow.

---

## Exercise 2

Choose an e-commerce product page.

Design:

- Component hierarchy
- State ownership
- Event flow

before implementing anything.

---

## Exercise 3

Analyze your HRMS project.

Draw its complete component tree.

Identify:

- Shared layouts
- Feature components
- State owners

Refactor anything that seems too large.

---

## Exercise 4

Pick a screen from your design system.

Write a one-page architecture document before writing React code.

---

# Summary

Thinking in React is the process of transforming product requirements into a scalable React architecture.

Instead of beginning with JSX, you begin by understanding the problem, decomposing the interface into reusable components, identifying State, determining ownership, and defining data flow.

By following this workflow consistently, React development becomes a structured engineering process rather than trial and error.

---

# Final Knowledge Check

You should now be able to answer:

- How do you approach a brand-new feature?
- How do you identify reusable components?
- How do you decide where State belongs?
- How do Props and Events move through the application?
- How do you organize a scalable component tree?
- Why is React considered declarative?
- How does the entire rendering pipeline work?

If you can confidently answer these questions, you've completed the **React Core Concepts** module.

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Component Composition | ↑ React Core Concepts | 🏠 React Home | React Hooks → |

---

# 🎓 Congratulations!

You've completed **React Core Concepts**.

You now understand both **how React works internally** and **how to design React applications**.

Your knowledge now includes:

```text
JSX
        ↓
React Elements
        ↓
Components
        ↓
Rendering
        ↓
Virtual DOM
        ↓
Reconciliation
        ↓
Props
        ↓
State
        ↓
Events
        ↓
Conditional Rendering
        ↓
Rendering Lists
        ↓
Keys
        ↓
Component Composition
        ↓
Thinking in React
```

This is the complete mental model required before learning Hooks.

---

# What's Next?

You're now ready for the next major module:

```text
React Hooks

↓

useState

↓

useEffect

↓

useRef

↓

useMemo

↓

useCallback

↓

Custom Hooks

↓

Advanced Hooks

↓

Hook Patterns

↓

Hook Architecture
```

Unlike many tutorials that teach Hooks immediately, you've first built a strong understanding of React's rendering model, component architecture, and data flow. That foundation will make Hooks easier to understand and apply correctly in real-world applications.

- ⬅ **Previous:** [13 - Component Composition](13-component-composition.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next Module:** [React Hooks](../03-hooks/README.md) *(Planned)*