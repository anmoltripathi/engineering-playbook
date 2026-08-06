# Component Composition

> Module: React Core Concepts
>
> Reading Time: 90–120 Minutes
>
> Difficulty: 🟡 Intermediate

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
> → Component Composition

---

# Overview

So far, you've learned how individual React components work.

You've learned:

- JSX
- Components
- Props
- State
- Events
- Conditional Rendering
- Rendering Lists
- Keys

Using these concepts, you can already build small applications.

However, real-world software isn't built from isolated components.

Instead, applications are built by combining many small components into larger, reusable features.

This design approach is called **Component Composition**.

Composition is one of React's core architectural principles.

Instead of creating one massive component that does everything,

React encourages developers to build many small, focused components that work together.

Think of components as building blocks.

Small blocks combine into larger blocks.

Larger blocks combine into complete applications.

---

# How It Connects

```text
Components

↓

Reusable Components

↓

Composition

↓

Features

↓

Pages

↓

Application
```

Everything you've learned so far becomes useful through composition.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Component Composition |
| Level | Intermediate |
| Reading Time | 90–120 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 2 Hours |
| Prerequisites | Keys |
| Next Topic | Thinking in React |

---

# Why This Matters

Every modern React application relies on composition.

Examples include:

- Dashboards
- E-commerce websites
- Banking portals
- Hospital Management Systems
- Payroll Systems
- CRM Software
- Social Media Platforms

None of these applications are one large component.

Instead, they are composed from hundreds or thousands of small reusable components.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain Component Composition.
- Design reusable component hierarchies.
- Break large interfaces into smaller components.
- Use composition instead of inheritance.
- Build layout components.
- Build reusable page structures.
- Understand parent-child relationships.
- Prepare for application architecture.

---

# The Problem Composition Solves

Imagine building a dashboard.

One approach is writing everything inside one component.

```jsx
function Dashboard() {

    // Header

    // Sidebar

    // Statistics

    // Employee Table

    // Payroll

    // Footer

}
```

Eventually:

- 1000 lines
- 2000 lines
- 5000 lines

The component becomes impossible to understand.

Instead,

divide responsibilities.

```text
Dashboard

├── Header

├── Sidebar

├── Statistics

├── EmployeeTable

├── PayrollSummary

└── Footer
```

Each component has one responsibility.

---

# What is Component Composition?

Component Composition means building larger user interfaces by combining smaller reusable components.

Conceptually:

```text
Button

↓

Card

↓

Dashboard Card

↓

Dashboard

↓

Application
```

Every larger component is composed from smaller ones.

---

# Components are Building Blocks

Imagine LEGO bricks.

Small bricks.

↓

Medium structures.

↓

Large structures.

↓

Entire city.

React components work exactly the same way.

```text
Button

↓

Toolbar

↓

Header

↓

Dashboard

↓

Application
```

Each level builds upon the previous one.

---

# Component Hierarchy

React applications naturally form trees.

Example:

```text
App

├── Layout

│   ├── Header

│   ├── Sidebar

│   └── Main

│       ├── Dashboard

│       ├── EmployeeTable

│       └── PayrollSummary

└── Footer
```

Notice that every component owns smaller components.

This hierarchy is one of React's biggest strengths.

---

# Parent and Child Components

Composition creates parent-child relationships.

Example:

```text
Dashboard

↓

EmployeeTable

↓

EmployeeRow

↓

ActionButton
```

Each child focuses on a smaller responsibility.

The parent coordinates everything.

---

# Composition Over Inheritance

React strongly encourages:

> Composition over inheritance.

Instead of creating huge inheritance hierarchies,

React combines components.

Bad mental model:

```text
Button

↓

PrimaryButton

↓

LargePrimaryButton

↓

LargeBluePrimaryButton
```

Good mental model:

```text
<Button

    variant="primary"

    size="large"

/>
```

Composition produces simpler and more flexible designs.

---

# Reusing Components

Imagine displaying employee information.

Without composition:

```text
Employee Card

Employee Table

Employee Popup

Employee Profile
```

Each duplicates employee rendering.

Instead:

```text
EmployeeInfo

↓

EmployeeCard

↓

EmployeeModal

↓

EmployeeRow
```

One reusable component serves many different interfaces.

---

# Composition Flow

Everything you've learned now connects together.

```text
Small Components

↓

Reusable Components

↓

Feature Components

↓

Page Components

↓

Application
```

Composition scales React applications from dozens to thousands of components.

---

> 🏗️ Engineering Note
>
> React applications are not built by creating large components.
>
> They are built by composing many small, focused, reusable components into increasingly larger structures.
>
> Good composition improves readability, maintainability, testing, and reuse.

# Component Trees

Every React application can be represented as a tree of components.

For example:

```text
App

├── Layout

│   ├── Header

│   ├── Sidebar

│   └── Main

│       ├── Dashboard

│       ├── EmployeeTable

│       └── PayrollSummary

└── Footer
```

This hierarchy is called the **Component Tree**.

Each node represents a React component.

Each parent composes one or more child components.

Thinking in trees helps developers understand application structure and data flow.

---

# Why Component Trees Matter

Imagine trying to understand a payroll application containing 500 components.

Instead of reading thousands of lines of code,

you can understand the application by looking at its component tree.

```text
Payroll App

├── Authentication

├── Layout

├── Employees

├── Payroll

├── Reports

└── Settings
```

Every feature can then be explored independently.

Good component trees improve:

- Navigation
- Team collaboration
- Testing
- Maintainability

---

# Building UI from Small Components

React encourages building from the smallest reusable pieces.

Example:

```text
Icon

↓

Button

↓

Toolbar

↓

Header

↓

Dashboard

↓

Application
```

Notice that every larger component depends on smaller ones.

Instead of creating one huge component,

React builds applications layer by layer.

---

# Layout Components

Some components exist only to organize the page.

They don't contain business logic.

Example:

```text
Layout

├── Header

├── Sidebar

├── Content

└── Footer
```

Example:

```jsx
function Layout({

    children

}) {

    return (

        <div>

            <Header />

            <Sidebar />

            <main>

                {children}

            </main>

            <Footer />

        </div>

    );

}
```

The layout doesn't know what page is being displayed.

It simply provides the application structure.

---

# The children Prop Revisited

Earlier, you learned about the special `children` prop.

Component Composition is where it becomes extremely useful.

Example:

```jsx
<Layout>

    <Dashboard />

</Layout>
```

React transforms this into:

```jsx
function Layout({

    children

}) {

    return (

        <main>

            {children}

        </main>

    );

}
```

Conceptually:

```text
Parent Component

↓

children

↓

Layout

↓

Rendered Page
```

This allows layout components to remain reusable.

---

# Wrapper Components

A wrapper component surrounds other components while adding shared behavior or styling.

Example:

```jsx
<Card>

    <EmployeeTable />

</Card>
```

The Card component doesn't know anything about employees.

It simply wraps content.

Another example:

```jsx
<Modal>

    <EmployeeForm />

</Modal>
```

The Modal component manages:

- Overlay
- Close button
- Animation
- Positioning

The EmployeeForm focuses only on employee data.

Each component has one responsibility.

---

# Container Components

Some components coordinate data and behavior.

Example:

```text
EmployeePage

↓

Fetch Employees

↓

Manage State

↓

Pass Props

↓

EmployeeTable
```

Container components usually:

- Fetch data
- Manage State
- Handle Events
- Pass Props

They orchestrate the application flow.

---

# Presentational Components

Presentational components focus on rendering UI.

Example:

```text
EmployeeCard

↓

Name

↓

Department

↓

Salary
```

These components usually:

- Receive Props
- Render UI
- Contain little or no business logic

They are highly reusable because they don't depend on application-specific behavior.

---

# Container vs Presentational

Consider an employee page.

```text
EmployeePage

↓

EmployeeTable

↓

EmployeeCard
```

Responsibilities:

```text
EmployeePage

↓

API

State

Filtering

Sorting

---------------------

EmployeeTable

↓

Display Table

---------------------

EmployeeCard

↓

Display Employee
```

Separating responsibilities makes components easier to test and reuse.

> **Note:** Modern React often uses Hooks inside components instead of strict "container" and "presentational" separation, but the underlying idea—separating data management from UI rendering—remains valuable.

---

# Composing Features

React applications are usually organized around features rather than pages.

Example:

```text
HRMS

├── Employees

├── Payroll

├── Attendance

├── Leave

└── Reports
```

Each feature contains its own components.

Example:

```text
Employees

├── EmployeeTable

├── EmployeeCard

├── EmployeeForm

├── EmployeeFilter

└── EmployeeDetails
```

Feature-based composition keeps large applications modular.

---

# Reusing Layouts

Imagine several pages.

```text
Dashboard

Employees

Payroll

Reports
```

Every page shares:

```text
Header

Sidebar

Footer
```

Instead of duplicating them,

reuse a Layout component.

```text
Layout

↓

Dashboard

Layout

↓

Employees

Layout

↓

Payroll
```

One layout serves the entire application.

---

# Designing Component APIs

Every reusable component exposes an API through Props.

Example:

```jsx
<Button

    variant="primary"

    size="large"

    disabled={false}

>

    Save

</Button>
```

The component doesn't expose its internal implementation.

It exposes a simple interface.

Think of a component like any other software API.

Consumers should understand **how to use it**, not **how it's implemented**.

---

# Component Composition Flow

Everything you've learned now connects together.

```text
Small Components

↓

Reusable Components

↓

Layout Components

↓

Feature Components

↓

Pages

↓

Application
```

Every React application follows this composition model regardless of its size.

---

> 🏗️ Engineering Note
>
> Good React architecture isn't measured by how many components you create.
>
> It's measured by **how clearly responsibilities are separated**.
>
> A well-composed application allows each component to focus on one concern while collaborating with other components through Props and Composition.

# Compound Components

As applications become more sophisticated, multiple components often work together to provide a single feature.

This pattern is called **Compound Components**.

Instead of exposing one large component with dozens of Props, React allows several related components to collaborate.

Example:

```jsx
<Tabs>

    <Tabs.List>

        <Tabs.Tab>Overview</Tabs.Tab>

        <Tabs.Tab>Payroll</Tabs.Tab>

        <Tabs.Tab>Reports</Tabs.Tab>

    </Tabs.List>

    <Tabs.Panels>

        <Tabs.Panel>

            <Overview />

        </Tabs.Panel>

        <Tabs.Panel>

            <Payroll />

        </Tabs.Panel>

        <Tabs.Panel>

            <Reports />

        </Tabs.Panel>

    </Tabs.Panels>

</Tabs>
```

Conceptually:

```text
Tabs

├── List

├── Tab

├── Panels

└── Panel
```

Each component has one responsibility while working together as one feature.

You'll implement this pattern later when learning advanced React.

---

# Composition vs Configuration

There are two common ways to make components flexible.

## Configuration

Use Props to change behavior.

Example:

```jsx
<Button

    variant="primary"

    size="large"

    disabled={false}

/>
```

The component changes based on configuration.

---

## Composition

Pass components instead of configuration.

Example:

```jsx
<Card>

    <EmployeeTable />

</Card>
```

Instead of asking the Card how it should behave,

we compose it with another component.

Conceptually:

```text
Configuration

↓

Props

--------------------

Composition

↓

Children
```

React strongly favors composition whenever possible.

---

# Prop Drilling (Introduction)

Consider this hierarchy.

```text
App

↓

Dashboard

↓

EmployeeSection

↓

EmployeeTable

↓

EmployeeRow
```

Suppose only `EmployeeRow` needs the current user.

Without another solution,

every intermediate component passes the same Prop.

```text
App

↓

currentUser

↓

Dashboard

↓

currentUser

↓

EmployeeSection

↓

currentUser

↓

EmployeeTable

↓

currentUser

↓

EmployeeRow
```

This is called **Prop Drilling**.

It's acceptable for small component trees but becomes difficult to manage in larger applications.

Later modules introduce alternatives such as:

- Context API
- Zustand
- Redux
- Server State libraries

For now, understand the problem—not the solution.

---

# Feature-Based Composition

Professional React applications are rarely organized by pages alone.

Instead, they are organized around business features.

Example:

```text
src

├── features

│   ├── employees

│   ├── payroll

│   ├── attendance

│   ├── leave

│   └── reports

├── shared

├── layouts

└── app
```

Each feature contains:

```text
Employees

├── Components

├── Hooks

├── API

├── Types

├── Utilities

└── Tests
```

This keeps applications modular and easier to scale as teams grow.

---

# Composition Patterns

Professional React applications use several composition patterns.

```text
Component Composition

│

├── Layout Components

├── Wrapper Components

├── Feature Components

├── Compound Components

├── Slot-based Composition (children)

├── Custom Hooks

└── Context Providers
```

Each pattern solves a different architectural problem.

You'll explore these patterns in later modules.

---

# Engineering Perspective

Component Composition is the reason React applications remain maintainable as they grow.

Instead of creating one enormous component,

React applications are assembled from many small, reusable building blocks.

Think of a construction project.

```text
Bricks

↓

Walls

↓

Rooms

↓

Floors

↓

Building
```

React follows the same principle.

```text
Buttons

↓

Cards

↓

Features

↓

Pages

↓

Application
```

Composition allows independent development, testing, and maintenance of each building block.

---

# Under the Hood

React doesn't know anything about "pages" or "features."

It simply executes components recursively.

Example:

```text
<App />

↓

<Layout />

↓

<Dashboard />

↓

<EmployeeTable />

↓

<EmployeeRow />

↓

<Button />
```

Each component returns more React Elements until the complete UI tree is built.

Conceptually:

```text
Component

↓

Returns JSX

↓

More Components

↓

More JSX

↓

Complete React Tree

↓

Virtual DOM

↓

Reconciliation

↓

Browser DOM
```

Composition naturally creates the tree React uses during rendering.

---

# Best Practices

## One Responsibility Per Component

Good:

```text
EmployeeTable

↓

Displays Employees
```

Avoid:

```text
EmployeeTable

↓

Displays Employees

↓

Calls APIs

↓

Handles Authentication

↓

Processes Payroll

↓

Downloads Reports
```

Each component should solve one primary problem.

---

## Build from Small to Large

Create reusable building blocks first.

```text
Button

↓

Card

↓

EmployeeCard

↓

EmployeeDashboard
```

This encourages reuse across the application.

---

## Prefer Composition Over Inheritance

React components should be combined rather than extended through inheritance.

Favor:

```jsx
<Card>

    <EmployeeTable />

</Card>
```

over deep inheritance hierarchies.

---

## Design Clear Component APIs

Expose only the Props consumers need.

Example:

```jsx
<Button

    variant="primary"

    loading={true}

>

    Save

</Button>
```

Avoid exposing unnecessary implementation details.

---

## Reuse Layouts

Shared page structure belongs in reusable Layout components.

Avoid duplicating:

- Header
- Sidebar
- Footer
- Navigation

across every page.

---

# Common Mistakes

## Mistake 1

Creating "God Components."

```text
Dashboard.jsx

↓

3000 Lines
```

Break large components into focused, reusable pieces.

---

## Mistake 2

Duplicating UI.

If the same UI appears multiple times,

extract it into a reusable component.

---

## Mistake 3

Passing too many Props.

When a component requires dozens of Props,

its API is likely too complex.

Consider grouping related data or introducing additional components.

---

## Mistake 4

Confusing Layout and Business Logic.

Layout components should organize structure.

Business logic belongs in feature components or custom hooks.

---

## Mistake 5

Creating Components Too Early

Not every repeated line of JSX needs its own component.

Extract components when they represent a meaningful, reusable concept.

---

# Real-World Architecture Example

Consider an HR Management System.

```text
App

├── Layout

│   ├── Header

│   ├── Sidebar

│   └── Main

├── Employees

│   ├── EmployeeTable

│   ├── EmployeeCard

│   ├── EmployeeFilter

│   └── EmployeeDetails

├── Payroll

│   ├── PayrollTable

│   ├── SalarySlip

│   └── PayrollSummary

├── Reports

└── Settings
```

Every feature is composed from smaller reusable components.

No single component owns the entire application.

---

# Quick Reference

| Goal | Recommended Pattern |
|------|----------------------|
| Shared page structure | Layout Component |
| Reusable UI | Composition |
| Pass arbitrary content | `children` |
| Organize business features | Feature-based folders |
| Coordinate related components | Compound Components |
| Separate concerns | Small focused components |

---

# Key Takeaways

✅ Component Composition builds complex UIs from simple components.

✅ React favors composition over inheritance.

✅ Layout components provide shared page structure.

✅ The `children` prop enables flexible composition.

✅ Small, focused components are easier to test and maintain.

✅ Feature-based composition scales better for large applications.

---

# Interview Questions

## Beginner

1. What is Component Composition?

2. Why does React prefer composition over inheritance?

3. What is the purpose of the `children` prop?

4. What is a Layout component?

---

## Intermediate

5. Explain Container vs Presentational components.

6. What is Prop Drilling?

7. How do Wrapper components improve reuse?

8. What are Compound Components?

---

## Advanced

9. How would you organize a React application with hundreds of components?

10. What makes a good component API?

11. When should a component be extracted?

12. How does Component Composition improve maintainability?

---

# Hands-on Exercises

## Exercise 1

Break a large Dashboard component into:

- Header
- Sidebar
- DashboardContent
- Footer

---

## Exercise 2

Create a reusable Layout component using the `children` prop.

Use it for:

- Dashboard
- Employees
- Payroll

---

## Exercise 3

Build an Employee feature.

Create:

- EmployeeTable
- EmployeeRow
- EmployeeActions
- EmployeeFilter

Compose them into one page.

---

## Exercise 4

Design a simple Tabs component using the Compound Component pattern.

Focus on the component structure rather than implementation details.

---

# Summary

Component Composition is React's primary architectural pattern.

Rather than building large monolithic components, React applications are assembled from many small, focused components that collaborate through Props and the `children` prop.

This approach promotes reuse, separation of concerns, maintainability, and scalability, making it suitable for applications ranging from small websites to enterprise platforms.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What is Component Composition?
- Why does React favor composition over inheritance?
- What role does the `children` prop play?
- What is the difference between a Layout component and a Feature component?
- What is Prop Drilling?
- What are Compound Components?
- How does good composition improve maintainability?

If you can confidently answer these questions, you're ready for **Thinking in React**.

---

# Further Reading

- 📖 Thinking in React
- 📖 Context API
- 📖 Custom Hooks
- 📖 React Router

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Keys | ↑ React Core Concepts | 🗺 Module Home | Thinking in React → |

---

# Continue Your Journey

You've learned how to design applications using **Component Composition**.

```text
Small Components

↓

Reusable Components

↓

Features

↓

Pages

↓

Application
```

The final chapter in this module, **Thinking in React**, brings everything together. You'll learn a systematic process for taking a product requirement and transforming it into a well-structured React application, from identifying components and state to defining data flow and building scalable architectures.

- ⬅ **Previous:** [12 - Keys](12-keys.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [14 - Thinking in React](14-thinking-in-react.md)