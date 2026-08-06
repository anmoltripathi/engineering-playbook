# State

> Module: React Core Concepts
>
> Reading Time: 75–90 Minutes
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
> → State

---

# Overview

In the previous chapter, you learned that **Props** allow a parent component to pass data to a child component.

However, Props have one important limitation.

They are controlled by the parent component.

Now imagine building a counter.

```
Count: 0
```

The user clicks:

```
Increment
```

Now the UI should display:

```
Count: 1
```

Who changes that value?

Not the parent.

The component itself.

This introduces a new concept:

**State**.

State allows a component to remember information and update that information over time.

Without State, React applications would be static.

Buttons couldn't count.

Forms couldn't accept input.

Shopping carts couldn't update.

Dashboards couldn't display live information.

State is what makes React applications interactive.

---

# How It Connects

```
Components

↓

Props

↓

Static UI

↓

State

↓

Interactive UI

↓

Events (Next Chapter)
```

Props provide external data.

State stores internal data.

Events will later change that State.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | State |
| Level | Beginner → Intermediate |
| Reading Time | 75–90 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 120 Minutes |
| Prerequisites | Props |
| Next Topic | Events |

---

# Why This Matters

Every modern React application uses State.

Examples include:

- Login forms
- Search boxes
- Shopping carts
- Counters
- Dashboards
- Notifications
- Theme switching
- Chat applications
- Data fetching
- Games

Without State, these features would not work.

State is one of the most fundamental concepts in React.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain what State is.
- Understand why State exists.
- Create State using `useState`.
- Read and update State.
- Explain why State updates trigger rendering.
- Understand State immutability.
- Distinguish Props from State.
- Understand React's State lifecycle.

---

# The Problem State Solves

Imagine building a Like button.

```
❤️ 0 Likes
```

The user clicks.

The interface should become:

```
❤️ 1 Like
```

Click again.

```
❤️ 2 Likes
```

Where should React remember this value?

Using a normal JavaScript variable seems reasonable.

```javascript
let likes = 0;
```

Increase it.

```javascript
likes++;
```

Now ask yourself:

> **Will the UI automatically update?**

The answer is **No**.

React doesn't know that the variable changed.

Changing a normal JavaScript variable does not trigger rendering.

React needs a special mechanism that both:

- Stores data
- Notifies React when the data changes

That mechanism is **State**.

---

# What is State?

State is data owned and managed by a React component.

Unlike Props, which come from a parent,

State belongs to the component itself.

Conceptually:

```
Component

↓

Owns State

↓

Reads State

↓

Updates State

↓

React Re-renders
```

State allows components to remember information between renders.

---

# State is Component Memory

A useful mental model is:

Imagine a calculator.

It remembers:

- Current number
- Previous number
- Selected operator

Without memory,

every button press would start from zero.

React components work the same way.

State is their memory.

It stores values across renders.

---

# Props vs State

Before learning how to create State,

it's important to understand the difference.

| Props | State |
|--------|-------|
| Passed by Parent | Owned by Component |
| Read-only | Updated by Component |
| External Data | Internal Data |
| Configure UI | Drive UI Changes |
| Parent Controls | Component Controls |

Props and State work together,

but they solve different problems.

---

# Creating State

React provides the `useState` Hook.

Example:

```jsx
const [count, setCount] = useState(0);
```

This single line creates component State.

Let's understand each part.

```
count

↓

Current State Value
```

```
setCount

↓

Function That Updates State
```

```
0

↓

Initial State
```

Conceptually:

```
Current Value

+

Update Function

↓

Component State
```

---

# Anatomy of useState

```jsx
const [

    count,

    setCount

] = useState(0);
```

React returns two values.

First:

```text
count
```

The current value.

Second:

```text
setCount
```

A function that tells React to update the value.

Every time `setCount()` is called,

React schedules another render.

---

# Reading State

Once State exists,

it can be displayed inside JSX.

```jsx
function Counter() {

    const [

        count,

        setCount

    ] = useState(0);

    return (

        <h1>

            {count}

        </h1>

    );

}
```

React automatically displays the current value.

Whenever State changes,

the displayed value changes too.

---

# Updating State

State should never be changed directly.

Incorrect:

```jsx
count++;
```

or

```jsx
count = 10;
```

React will not know about these changes.

Instead,

always use the updater function.

Correct:

```jsx
setCount(

    count + 1

);
```

Flow:

```
setCount()

↓

State Changes

↓

Render Scheduled

↓

Component Executes

↓

Updated UI
```

---

> 🏗️ Engineering Note
>
> Think of `setState` (or `setCount`) as sending a request to React.
>
> You're not directly changing the value.
>
> You're asking React to update the component's state and perform another render if necessary.

# The State Lifecycle

React State follows a predictable lifecycle.

Every state update moves through several stages before the user sees the updated interface.

Understanding this lifecycle helps explain why React behaves the way it does.

Conceptually:

```text
Create State

↓

Read State

↓

Update State

↓

Render

↓

Virtual DOM

↓

Reconciliation

↓

Commit

↓

Browser Paint
```

Every state update follows this same pipeline.

---

# Initial State

When a component renders for the first time,

React creates the initial state.

Example:

```jsx
const [count, setCount] = useState(0);
```

At this moment:

```text
count = 0
```

React stores this value internally.

The component now has its own local memory.

---

# Reading State

During every render,

the component receives the latest state value.

Example:

```jsx
<h1>{count}</h1>
```

React substitutes the current value.

If:

```text
count = 5
```

React renders:

```html
<h1>5</h1>
```

Every render always uses the most recent state.

---

# Updating State

Suppose the user clicks a button.

```jsx
<button

    onClick={() => setCount(count + 1)}

>
    Increment
</button>
```

React performs the following steps.

```text
Button Click

↓

setCount()

↓

State Update Requested

↓

Render Scheduled
```

Notice something important.

At this point,

the value has **not yet changed on the screen**.

React first schedules another render.

---

# React Executes the Component Again

After scheduling the update,

React executes the component from the beginning.

Conceptually:

```text
Counter()

↓

Read Updated State

↓

Return New JSX

↓

Render Complete
```

This is why function components execute many times throughout an application's lifetime.

Every render starts from the top of the component function.

---

# State Survives Between Renders

Although the component function executes again,

the state is **not recreated**.

Example:

```jsx
const [count, setCount] = useState(0);
```

React does **not** create a new state variable every render.

Instead:

```text
First Render

↓

count = 0

↓

setCount(1)

↓

Second Render

↓

count = 1
```

The state value is preserved internally by React.

This is why state behaves like component memory.

---

# State Triggers Rendering

One of the most important React concepts is:

> **Changing State triggers a render.**

Example:

```jsx
setCount(10);
```

Flow:

```text
setCount()

↓

React Schedules Render

↓

Component Executes Again

↓

New React Elements

↓

Virtual DOM

↓

Reconciliation

↓

Commit

↓

Browser Paint
```

This entire process happens automatically.

---

# Why Doesn't React Update Immediately?

Many beginners expect this:

```jsx
setCount(10);

console.log(count);
```

Output:

```text
10
```

Instead, they often see:

```text
0
```

Why?

Because `setCount()` schedules an update.

React hasn't rendered the component yet.

Only after React completes another render does `count` become `10`.

Conceptually:

```text
Current Render

↓

setCount()

↓

Schedule Next Render

↓

Next Render

↓

Updated State
```

State updates become visible in the **next render**, not immediately.

---

# Multiple State Variables

A component can have multiple independent pieces of state.

Example:

```jsx
const [name, setName] = useState("");

const [email, setEmail] = useState("");

const [age, setAge] = useState(18);
```

Conceptually:

```text
Component

├── name

├── email

└── age
```

Each state variable is managed independently.

Updating one does not automatically change the others.

---

# Updating Multiple States

Consider:

```jsx
setName("Alex");

setAge(30);
```

Both updates are scheduled.

React may process them together to avoid unnecessary renders.

You'll learn about batching later in this chapter.

---

# State Belongs to One Component

Each component owns its own state.

Example:

```text
Dashboard

├── Sidebar

├── Header

└── Profile
```

Each component can have completely separate state.

```text
Sidebar

↓

isOpen

------------------

Header

↓

theme

------------------

Profile

↓

user
```

One component cannot directly modify another component's state.

State ownership is local unless it's intentionally shared.

---

# Local State

This is why State is often called **Local State**.

It belongs only to the component that created it.

Example:

```jsx
function Counter() {

    const [

        count,

        setCount

    ] = useState(0);

}
```

Only `Counter` owns this state.

Other components cannot access it unless it is passed through Props.

---

> 🏗️ Engineering Note
>
> Think of State as **private memory** owned by a component.
>
> Props are like **function arguments** provided by a parent.
>
> State is like **private variables** that the component manages itself.
>
> Understanding this ownership model is essential before learning how components communicate with one another.

# State is Immutable

One of React's fundamental principles is:

> **Never modify State directly.**

Instead of changing existing State,

React expects you to create a **new value**.

This principle is called **immutability**.

Understanding immutability is essential because React relies on it to determine whether the UI should update.

---

# What Does Immutable Mean?

Immutable means:

> **Once a value is created, don't modify it. Create a new value instead.**

Example:

Instead of:

```text
Old Object

↓

Modify Same Object
```

React prefers:

```text
Old Object

↓

Create New Object

↓

Replace Old Value
```

This makes updates predictable and easier to detect.

---

# Primitive Values

Primitive values are easy to update.

Example:

```jsx
const [

    count,

    setCount

] = useState(0);
```

Correct:

```jsx
setCount(count + 1);
```

React receives a completely new value.

```
0

↓

1
```

---

# Objects Are Different

Suppose State stores an object.

```jsx
const [

    user,

    setUser

] = useState({

    name: "Alex",

    age: 28

});
```

A beginner might write:

```jsx
user.age = 29;
```

This changes the existing object.

React cannot reliably detect that change.

This is incorrect.

---

# Correct Object Update

Instead,

create a new object.

```jsx
setUser({

    ...user,

    age: 29

});
```

Conceptually:

```text
Old Object

↓

Copy Everything

↓

Replace age

↓

New Object
```

React now receives a brand-new object.

---

# Updating Arrays

Arrays follow the same rule.

Incorrect:

```jsx
items.push(newItem);
```

This mutates the existing array.

Correct:

```jsx
setItems([

    ...items,

    newItem

]);
```

Conceptually:

```text
Old Array

↓

Copy Items

↓

Add New Item

↓

New Array
```

The original array remains unchanged.

---

# Why Doesn't React Want Mutation?

Imagine React stores the previous State.

```text
Previous User

↓

Current User
```

If both variables reference the same object,

React cannot easily determine what changed.

```text
Previous

↓

Same Object

↓

Current
```

Now imagine creating a new object.

```text
Previous Object

↓

New Object
```

React immediately knows something changed.

Immutability makes comparison simple and efficient.

---

# Object References

Consider these variables.

```javascript
const user1 = {

    name: "Alex"

};

const user2 = user1;
```

Both variables point to the same object.

```
user1

↓

Object

↑

user2
```

Changing one affects the other.

```javascript
user2.name = "John";
```

Now:

```javascript
user1.name
```

also becomes:

```
John
```

This shared reference is why mutation can lead to unexpected behavior.

---

# Creating a New Object

Instead:

```javascript
const user2 = {

    ...user1,

    name: "John"

};
```

Now:

```text
user1

↓

Object A

------------------

user2

↓

Object B
```

Each object is independent.

This is the approach React encourages.

---

# Functional State Updates

Sometimes the next State depends on the previous State.

Instead of:

```jsx
setCount(

    count + 1

);
```

React recommends:

```jsx
setCount(previousCount =>

    previousCount + 1

);
```

Conceptually:

```text
Previous State

↓

Updater Function

↓

Next State
```

This approach is safer because React always provides the latest state value.

---

# Why Functional Updates Matter

Imagine two updates happen almost simultaneously.

```jsx
setCount(count + 1);

setCount(count + 1);
```

You might expect:

```
2
```

But both updates use the same value of `count` from the current render.

Instead, write:

```jsx
setCount(previous =>

    previous + 1

);

setCount(previous =>

    previous + 1

);
```

Now React processes them correctly.

```text
0

↓

1

↓

2
```

Functional updates avoid stale state values.

---

# State Update Queue

React doesn't immediately process every `setState()` call.

Instead, updates are placed into a queue.

Conceptually:

```text
setCount()

↓

Queue

↓

React Processes Updates

↓

Render

↓

Updated UI
```

This allows React to efficiently handle multiple updates together.

---

# Automatic Batching

Modern React automatically groups multiple state updates into a single render whenever possible.

Example:

```jsx
setName("Alex");

setAge(30);

setCity("Delhi");
```

Instead of rendering three times:

```text
Render

Render

Render
```

React batches them.

```text
Three Updates

↓

One Render

↓

One Browser Update
```

Batching improves performance by reducing unnecessary renders.

---

# State Updates Are Scheduled

Calling:

```jsx
setCount(5);
```

does not immediately change `count`.

Instead:

```text
setCount()

↓

Schedule Update

↓

React Queue

↓

Render

↓

Updated State
```

This explains why reading State immediately after calling `setState()` often returns the previous value.

---

> 🏗️ Engineering Note
>
> React doesn't update State immediately because it needs the flexibility to batch multiple updates, prioritize rendering work, and keep the user interface responsive.
>
> By treating State updates as scheduled work rather than immediate mutations, React can optimize rendering while preserving predictable application behavior.

# Lifting State Up

As applications grow, multiple components often need access to the same data.

Consider this component tree.

```text
App

├── SearchBox

└── ProductList
```

Suppose:

- `SearchBox` stores the search text.
- `ProductList` needs that same text to filter products.

If the state stays inside `SearchBox`, `ProductList` cannot access it.

The solution is to move the state to their nearest common parent.

This pattern is called **Lifting State Up**.

---

## Before

```text
App

├── SearchBox
│       ↓
│    searchText
│
└── ProductList
```

`ProductList` cannot read `searchText`.

---

## After

```text
App
│
│ searchText
│
├── SearchBox
│
└── ProductList
```

Now:

- App owns the State.
- SearchBox updates it.
- ProductList reads it through Props.

This creates a **single source of truth**.

---

# Derived State

Sometimes data doesn't need its own State.

Instead, it can be calculated from existing State.

Example:

```jsx
const [price, setPrice] = useState(100);

const tax = price * 0.18;
```

Notice:

`tax` is derived from `price`.

There is no need for:

```jsx
const [tax, setTax] = useState(...);
```

Whenever possible:

✅ Compute values.

❌ Don't duplicate State.

Duplicated State easily becomes inconsistent.

---

# Single Source of Truth

Every piece of information should have one owner.

Example:

```text
Shopping Cart

↓

Cart Items

↓

Total Price

↓

Tax

↓

Grand Total
```

Only the cart items need State.

Everything else can be calculated.

This makes applications easier to maintain.

---

# Props vs State (Advanced)

You've already learned the basic differences.

Let's look at them from an architectural perspective.

| Props | State |
|--------|-------|
| Input to a Component | Internal Memory |
| Parent Owns | Component Owns |
| Immutable | Updated through setState |
| Configure UI | Drive UI Changes |
| External Data | Local Data |

Think of it like this:

```text
Parent

↓

Props

↓

Component

↓

State

↓

Rendered UI
```

Props flow into a component.

State lives inside it.

Events change State.

Rendering updates the UI.

---

# Under the Hood

When you call:

```jsx
setCount(count + 1);
```

React performs far more work than simply assigning a value.

```text
User Click

↓

Event Handler

↓

setCount()

↓

React Update Queue

↓

Automatic Batching

↓

Scheduler

↓

Render Phase

↓

Component Executes

↓

New React Elements

↓

Virtual DOM

↓

Reconciliation

↓

Commit Phase

↓

Browser DOM Updated

↓

Browser Paint

↓

User Sees Updated UI
```

This entire process usually completes in just a few milliseconds.

---

# Engineering Perspective

State is the foundation of interactivity in React.

Instead of manually manipulating the DOM, developers update State.

React then determines:

- What changed
- Which components should render
- Which DOM nodes need updating

This separation between **application data** and **DOM manipulation** is one of React's biggest architectural strengths.

It enables predictable updates, efficient rendering, and scalable applications.

---

# Best Practices

## Keep State Minimal

Store only the information that cannot be derived.

Good:

```jsx
const [cartItems, setCartItems] = useState([]);
```

Avoid:

```jsx
cartItems

totalPrice

tax

grandTotal
```

Most of these values can be calculated.

---

## Group Related State

Good:

```jsx
const [user, setUser] = useState({

    name: "",

    email: ""

});
```

Avoid creating dozens of unrelated state variables when they naturally belong together.

---

## Avoid Deeply Nested State

Instead of:

```text
User

↓

Profile

↓

Settings

↓

Preferences

↓

Theme
```

Prefer flatter structures whenever practical.

Nested updates become more difficult to maintain.

---

## Never Mutate State

Incorrect:

```jsx
user.name = "John";
```

Correct:

```jsx
setUser({

    ...user,

    name: "John"

});
```

---

## Use Functional Updates When Necessary

Whenever the next value depends on the previous value:

```jsx
setCount(previous =>

    previous + 1

);
```

This prevents stale state bugs.

---

# Common Mistakes

## Mistake 1

Updating State directly.

```jsx
count++;
```

React won't know anything changed.

---

## Mistake 2

Duplicating State.

Example:

```text
price

tax

total
```

When only `price` actually needs State.

---

## Mistake 3

Expecting State to update immediately.

```jsx
setCount(1);

console.log(count);
```

State updates become available during the next render.

---

## Mistake 4

Using State when Props are sufficient.

Ask yourself:

> Does this value belong to the component?

If not,

it probably belongs in Props.

---

## Mistake 5

Putting every value into State.

Not everything needs State.

Constants, derived values, and configuration data usually do not.

---

# Real-World Example

Imagine a shopping cart.

```text
Cart

↓

Items

↓

Total Price

↓

Discount

↓

Tax

↓

Final Amount
```

Only one piece of information truly changes.

```text
Cart Items
```

Everything else can be calculated.

```text
Items

↓

Subtotal

↓

Discount

↓

Tax

↓

Grand Total
```

This produces a simpler and more maintainable application.

---

# Quick Reference

| Scenario | Use State? |
|-----------|------------|
| User typing in a form | ✅ Yes |
| Counter value | ✅ Yes |
| Shopping cart items | ✅ Yes |
| Modal open/close | ✅ Yes |
| Theme toggle | ✅ Yes |
| Static configuration | ❌ No |
| Derived calculations | ❌ Calculate instead |
| Parent configuration | ❌ Use Props |

---

# Key Takeaways

✅ State is component-owned data.

✅ State makes React applications interactive.

✅ Updating State schedules a render.

✅ State should never be mutated directly.

✅ Objects and arrays require immutable updates.

✅ Functional updates prevent stale state bugs.

✅ Keep State minimal and derive values whenever possible.

---

# Interview Questions

## Beginner

1. What is State in React?

2. How is State different from Props?

3. What does `useState()` return?

4. Why does updating State re-render the component?

---

## Intermediate

5. Why is State immutable?

6. What are functional State updates?

7. Why doesn't `setState()` update immediately?

8. What is Lifting State Up?

---

## Advanced

9. Explain React's State lifecycle.

10. What is automatic batching?

11. Why should derived data usually not be stored in State?

12. How does State interact with Rendering, Virtual DOM, and Reconciliation?

---

# Hands-on Exercises

## Exercise 1

Build a counter application.

Implement:

- Increment
- Decrement
- Reset

---

## Exercise 2

Create a form with:

- Name
- Email
- Password

Store each field using State.

---

## Exercise 3

Create a shopping cart.

Store:

- Cart Items

Calculate:

- Total
- Tax
- Grand Total

without additional State.

---

## Exercise 4

Build a search feature.

Lift the search State into the parent component so multiple child components can share it.

---

# Summary

State is React's mechanism for storing data that changes over time.

Unlike Props, which are controlled by a parent component, State belongs to the component itself and represents its internal memory.

When State changes, React schedules a new render, creates a new Virtual DOM tree, performs reconciliation, and updates only the necessary parts of the Browser DOM.

Understanding State is essential because it forms the basis of every interactive React application.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What is State?
- How is State different from Props?
- Why is State immutable?
- Why shouldn't State be updated directly?
- What is a functional update?
- What is Lifting State Up?
- Why should derived values usually not be stored in State?
- What happens internally after calling `setState()`?

If you can confidently answer these questions, you're ready for **Events**.

---

# Further Reading

- 📖 Events
- 📖 Conditional Rendering
- 📖 Rendering Lists

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Props | ↑ React Core Concepts | 🗺 Module Home | Events → |

---

# Continue Your Journey

You've learned how React components store and update their own data using **State**.

```text
Props

↓

State

↓

Rendering

↓

Updated UI
```

In the next chapter, you'll learn **Events**—how users interact with React applications and how those interactions trigger State updates.

Together, **Props**, **State**, and **Events** form the foundation of every interactive React application.

- ⬅ **Previous:** [07 - Props](07-props.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [09 - Events](09-events.md)