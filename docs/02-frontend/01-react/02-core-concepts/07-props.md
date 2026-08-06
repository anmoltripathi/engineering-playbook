# Props

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
> → Props

---

# Overview

So far in this module, you've learned how React renders and updates user interfaces.

However, all of the components you've created have one limitation.

They always display the same content.

Consider this component.

```jsx
function Button() {
    return (
        <button>Save</button>
    );
}
```

No matter how many times you use this component, it always displays **Save**.

```jsx
<Button />

<Button />

<Button />
```

Output

```
Save

Save

Save
```

This isn't very useful.

Real applications need reusable components that can display different data.

For example:

```
Save

Cancel

Delete

Update
```

Instead of creating four separate components, React allows us to pass data into a component.

This data is called **Props**.

Props make components dynamic, configurable, and reusable.

---

# How It Connects

```
Components

↓

Reusable Components

↓

Need Different Data

↓

Props

↓

Dynamic UI

↓

State (Next Chapter)
```

Components define structure.

Props customize that structure.

State will later allow that data to change over time.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Props |
| Level | Beginner → Intermediate |
| Reading Time | 60–75 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | Components, Reconciliation |
| Next Topic | State |

---

# Why This Matters

Nearly every React application relies on Props.

You'll use them when building:

- Buttons
- Cards
- Navigation menus
- User profiles
- Tables
- Charts
- Dashboards
- Forms

Without Props, components would not be reusable.

Every variation would require creating another component.

Props solve this problem elegantly.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain what Props are.
- Pass data from parent to child.
- Read Props inside components.
- Use multiple Props.
- Understand one-way data flow.
- Explain why Props are immutable.
- Distinguish Props from State.
- Build configurable, reusable components.

---

# The Problem Props Solve

Imagine you're building a dashboard.

It contains three statistics.

```
Employees

Departments

Projects
```

One approach is to build three components.

```jsx
<EmployeeCard />

<DepartmentCard />

<ProjectCard />
```

Although the displayed data is different, the layout is nearly identical.

This results in duplicated code.

A better solution is to create one reusable component.

```jsx
<StatCard />

<StatCard />

<StatCard />
```

Now another question appears.

> **How does each StatCard know what to display?**

The answer is **Props**.

---

# What Are Props?

Props (short for **Properties**) are values passed from a parent component to a child component.

They allow the same component to display different information depending on the data it receives.

Think of Props as inputs.

```
Parent Component

↓

Props

↓

Child Component

↓

Rendered UI
```

Every time the parent renders, it can provide different values.

This makes components reusable.

---

# Props Are Like Function Parameters

React components are JavaScript functions.

JavaScript functions receive parameters.

```javascript
function greet(name) {
    return `Hello ${name}`;
}

greet("Alex");
greet("Sarah");
```

The function doesn't change.

Only the input changes.

React components behave the same way.

```jsx
<Greeting name="Alex" />

<Greeting name="Sarah" />
```

The component remains the same.

Only the Props change.

---

# Passing Props

A parent passes Props using JSX attributes.

```jsx
<Greeting
    name="Alex"
/>
```

React creates a Props object and passes it to the child.

```jsx
function Greeting(props) {
    return (
        <h1>Hello {props.name}</h1>
    );
}
```

Conceptually:

```
Parent

↓

name="Alex"

↓

Props Object

↓

Child Component

↓

Hello Alex
```

Props are simply a JavaScript object.

---

# The Props Object

Consider the following component.

```jsx
<Greeting
    name="Alex"
    role="Developer"
    age={28}
/>
```

React conceptually creates:

```javascript
{
    name: "Alex",
    role: "Developer",
    age: 28
}
```

This object is passed as the first argument to the component.

```jsx
function Greeting(props) {

}
```

You can access individual values.

```jsx
props.name

props.role

props.age
```

Everything passed from the parent becomes part of the Props object.

---

# Parent Owns the Data

One of React's most important principles is:

> **The parent owns the data.**

The child simply receives it.

Conceptually:

```
Parent

↓

Creates Data

↓

Passes Props

↓

Child Reads Data
```

The child should never assume ownership of Props.

This principle keeps React applications predictable and easier to maintain.

# Reading Props

There are two common ways to read Props inside a React component.

The first is using the `props` object directly.

Example:

```jsx
function UserCard(props) {
    return (
        <div>
            <h2>{props.name}</h2>
            <p>{props.role}</p>
        </div>
    );
}
```

React passes the entire Props object into the component.

You can access any value using dot notation.

```jsx
props.name

props.role

props.department
```

This approach is simple and explicit.

---

# Props Destructuring

As components grow, repeatedly writing `props.` becomes verbose.

Instead, JavaScript destructuring allows you to extract only the values you need.

Instead of:

```jsx
function UserCard(props) {

    return (
        <h2>{props.name}</h2>
    );

}
```

Write:

```jsx
function UserCard({ name }) {

    return (
        <h2>{name}</h2>
    );

}
```

For multiple Props:

```jsx
function UserCard({

    name,

    role,

    department

}) {

    return (

        <div>

            <h2>{name}</h2>

            <p>{role}</p>

            <p>{department}</p>

        </div>

    );

}
```

This is the preferred style in modern React applications.

---

# Multiple Props

A component can receive as many Props as necessary.

Example:

```jsx
<ProductCard

    name="MacBook Pro"

    price={199999}

    category="Laptop"

    inStock={true}

/>
```

React creates a Props object conceptually like this:

```javascript
{
    name: "MacBook Pro",
    price: 199999,
    category: "Laptop",
    inStock: true
}
```

Each property becomes available inside the component.

---

# Different Types of Props

Props are simply JavaScript values.

You can pass almost any value.

---

## String

```jsx
<Button

    label="Save"

/>
```

---

## Number

```jsx
<Product

    price={499}

/>
```

---

## Boolean

```jsx
<Button

    disabled={true}

/>
```

---

## Object

```jsx
<UserCard

    user={{

        id: 1,

        name: "Alex"

    }}

/>
```

---

## Array

```jsx
<UserList

    users={users}

/>
```

---

## Function

```jsx
<Button

    onClick={handleSave}

/>
```

You'll learn callback functions in the Events chapter.

---

# Default Values

Sometimes a parent doesn't pass a Prop.

Instead of displaying undefined,

provide a default value.

Example:

```jsx
function Button({

    label = "Submit"

}) {

    return (

        <button>

            {label}

        </button>

    );

}
```

Usage:

```jsx
<Button />
```

Output:

```
Submit
```

Now with a Prop:

```jsx
<Button

    label="Save"

/>
```

Output:

```
Save
```

Default values make components more robust.

---

# The Special `children` Prop

One of React's most powerful features is the special `children` Prop.

Consider this component.

```jsx
<Card>

    <h2>Engineering Playbook</h2>

    <p>Learn React from fundamentals to architecture.</p>

</Card>
```

The content placed between the opening and closing tags is automatically passed as `children`.

```jsx
function Card({

    children

}) {

    return (

        <div className="card">

            {children}

        </div>

    );

}
```

Conceptually:

```text
<Card>

↓

Everything Inside

↓

children Prop

↓

Rendered by Card
```

This allows components to act as reusable containers.

---

# Passing Objects as Props

Passing objects is very common.

Example:

```jsx
const user = {

    id: 1,

    name: "Alex",

    role: "Developer"

};
```

Pass the object.

```jsx
<UserCard

    user={user}

/>
```

Read the object.

```jsx
function UserCard({

    user

}) {

    return (

        <div>

            <h2>{user.name}</h2>

            <p>{user.role}</p>

        </div>

    );

}
```

Passing objects keeps related data grouped together.

---

# Passing Arrays as Props

Lists are usually passed as arrays.

```jsx
const courses = [

    "React",

    "TypeScript",

    "FastAPI"

];
```

Pass the array.

```jsx
<CourseList

    courses={courses}

/>
```

Later you'll learn how to render arrays using `map()`.

---

# Passing Functions as Props

Functions can also be passed as Props.

Example:

```jsx
<Button

    onClick={handleSave}

/>
```

The child receives the function.

```jsx
function Button({

    onClick

}) {

    return (

        <button onClick={onClick}>

            Save

        </button>

    );

}
```

This enables child components to notify parent components about user interactions.

This concept becomes extremely important in the Events chapter.

---

# One-Way Data Flow

React follows a one-way (unidirectional) data flow.

Data always moves from parent to child.

```text
App

↓

Dashboard

↓

Statistics

↓

StatCard
```

Every component receives data from its parent.

Children cannot directly change the Props they receive.

If data changes,

the parent passes new Props during the next render.

This predictable flow makes React applications easier to debug and maintain.

---

# Props Are Immutable

Props are **read-only**.

A child component should never modify them.

Incorrect:

```jsx
props.name = "John";
```

Correct:

The parent provides new Props.

```text
Parent Updates Data

↓

Render Again

↓

Child Receives New Props
```

React relies on immutable Props to keep rendering predictable and support efficient reconciliation.

---

> 🏗️ Engineering Note
>
> Treat Props like **function arguments**.
>
> Your component should read them, use them to calculate the UI, and never modify them.
>
> If data needs to change, the parent component should supply a new value during the next render.

# Props vs State

One of the first questions every React developer asks is:

> **When should I use Props and when should I use State?**

Although both store data, they solve different problems.

---

## Props

Props are data passed **from a parent component to a child component**.

Characteristics:

- Read-only
- Controlled by the parent
- Used to configure components
- Cannot be modified by the child

Example:

```jsx
<Button

    label="Save"

/>
```

---

## State

State is data owned by the component itself.

Characteristics:

- Local to the component
- Can change over time
- Managed using React Hooks
- Causes re-rendering when updated

Example:

```jsx
const [count, setCount] = useState(0);
```

---

## Comparison

| Props | State |
|--------|-------|
| Passed by Parent | Owned by Component |
| Read-only | Mutable (through setState/useState) |
| Configure Component | Store Dynamic Data |
| External Data | Internal Data |
| Parent Controls | Component Controls |

---

## Mental Model

Think of a car.

Props are like the options selected by the buyer.

```text
Color

↓

Engine

↓

Transmission
```

These values are provided when the car is ordered.

---

State is like the information that changes while driving.

```text
Fuel Level

↓

Speed

↓

Current Gear

↓

Engine Temperature
```

Those values continuously change during the lifetime of the car.

React works the same way.

---

# Data Flow in React

Everything you've learned now connects together.

```text
App

↓

Props

↓

Dashboard

↓

Props

↓

Statistics

↓

State

↓

UI
```

Props move downward.

State lives inside a component.

Events (next chapter) will request State updates.

---

# Real Example

Imagine a reusable Product Card.

Parent:

```jsx
<ProductCard

    name="MacBook Pro"

    price={199999}

    inStock={true}

/>
```

Child:

```jsx
function ProductCard({

    name,

    price,

    inStock

}) {

    return (

        <div>

            <h2>{name}</h2>

            <p>{price}</p>

            <p>

                {inStock ? "Available" : "Out of Stock"}

            </p>

        </div>

    );

}
```

The same component can now display hundreds of different products simply by receiving different Props.

---

# Engineering Perspective

Props are the mechanism that makes React's component architecture reusable.

Instead of creating many nearly identical components, developers create one generic component and configure it using Props.

This separation of **structure** (Component) and **configuration** (Props) makes React applications easier to scale, test, and maintain.

Combined with React's one-way data flow, Props also make applications more predictable because every component receives its inputs explicitly from its parent.

---

# Best Practices

## Keep Props Small

Pass only the data a component actually needs.

Good:

```jsx
<UserCard

    name={user.name}

    role={user.role}

/>
```

Avoid passing huge objects if only one or two values are required.

---

## Use Destructuring

Instead of:

```jsx
props.name

props.role
```

Prefer:

```jsx
function UserCard({

    name,

    role

}) {

}
```

It improves readability.

---

## Use Meaningful Prop Names

Good:

```jsx
<UserCard

    user={user}

/>

<Button

    disabled={true}

/>

<ProductCard

    price={499}

/>
```

Avoid unclear names like:

```jsx
data

item

value

obj
```

Choose names that describe the data's purpose.

---

## Never Modify Props

Incorrect:

```jsx
props.price = 100;
```

Correct:

Update the value in the parent component and pass new Props during the next render.

---

## Keep Components Generic

Design components to work with many different Prop values.

Instead of:

```jsx
<SaveButton />
```

Prefer:

```jsx
<Button

    label="Save"

/>
```

Generic components are easier to reuse across applications.

---

# Common Mistakes

## Mistake 1

Trying to modify Props.

Props are immutable.

---

## Mistake 2

Confusing Props with State.

Props come from the parent.

State belongs to the component.

---

## Mistake 3

Passing too many unrelated Props.

Instead of:

```jsx
<UserCard

    id={...}

    name={...}

    role={...}

    department={...}

    manager={...}

    salary={...}

    address={...}

/>
```

Consider passing a single object when the data naturally belongs together.

```jsx
<UserCard

    user={user}

/>
```

---

## Mistake 4

Using Props when State is needed.

Props configure a component.

State stores values that change over time.

---

# Real-World Example

Consider an employee management system.

Parent:

```jsx
<EmployeeCard

    employee={employee}

/>
```

Employee 1

```text
Name

Department

Designation

Salary
```

Employee 2

```text
Name

Department

Designation

Salary
```

Employee 3

```text
Name

Department

Designation

Salary
```

The layout remains identical.

Only the Props change.

This is the essence of reusable component design.

---

# Quick Reference

| Scenario | Use Props? |
|----------|------------|
| Pass data from parent to child | ✅ Yes |
| Configure a reusable component | ✅ Yes |
| Pass callback functions | ✅ Yes |
| Display API data | ✅ Yes |
| Store changing local values | ❌ Use State |
| Update user input | ❌ Use State |

---

# Key Takeaways

✅ Props are inputs to a React component.

✅ Props are passed from parent to child.

✅ Props are immutable.

✅ Components should never modify their Props.

✅ Props make components reusable and configurable.

✅ React follows one-way data flow.

---

# Interview Questions

## Beginner

1. What are Props in React?

2. Why do we use Props?

3. How are Props passed to a component?

4. Are Props mutable?

---

## Intermediate

5. Explain one-way data flow.

6. What is Props destructuring?

7. What is the `children` Prop?

8. How are objects and arrays passed as Props?

---

## Advanced

9. Explain the relationship between Props and Reconciliation.

10. Why are immutable Props important for React?

11. When would you pass an object instead of multiple individual Props?

12. How do callback Props enable parent-child communication?

---

# Hands-on Exercises

## Exercise 1

Create a reusable Button component.

Use Props for:

- Label
- Color
- Disabled state

---

## Exercise 2

Create a reusable EmployeeCard component.

Pass:

- Name
- Department
- Designation
- Salary

using Props.

---

## Exercise 3

Pass an array of products to a ProductList component.

Display the products using the received Props.

---

## Exercise 4

Pass a callback function from a parent component to a child button.

Log a message when the button is clicked.

---

# Summary

Props are React's mechanism for passing data from parent components to child components.

They allow components to remain reusable by separating a component's structure from the data it displays.

Props are immutable, flow in one direction, and should be treated like function parameters.

By understanding Props, you've taken the first step toward building dynamic React applications.

The next chapter introduces **State**, which allows components to manage data that changes over time.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What are Props?
- Why are Props immutable?
- What is one-way data flow?
- How are Props different from State?
- What is the `children` Prop?
- Why do reusable components rely on Props?
- When should you pass an object instead of multiple Props?

If you can confidently answer these questions, you're ready to learn **State**.

---

# Further Reading

- 📖 State
- 📖 Events
- 📖 Component Composition

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Reconciliation | ↑ React Core Concepts | 🗺 Module Home | State → |

---

# Continue Your Journey

You've learned how React components receive data through **Props**.

```text
Parent Component

↓

Props

↓

Child Component

↓

Rendered UI
```

In the next chapter, you'll learn **State**—React's mechanism for storing and updating data that changes over time.

Together, **Props** and **State** form the foundation of every interactive React application.

- ⬅ **Previous:** [06 - Reconciliation](06-reconciliation.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [08 - State](08-state.md)