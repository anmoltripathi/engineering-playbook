# Reconciliation

> Module: React Core Concepts
>
> Reading Time: 70–90 Minutes
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
> → Reconciliation

---

# Overview

In the previous chapter, you learned that React creates a new Virtual DOM tree whenever your application renders.

A natural question follows:

> **How does React compare the previous Virtual DOM with the new one?**

The answer is **Reconciliation**.

Reconciliation is the algorithm React uses to determine what has changed between two versions of the user interface.

Rather than rebuilding the entire page, React compares the previous tree with the new tree and identifies the smallest set of changes required to keep the browser synchronized with your application's state.

This process is one of React's most important optimizations and is fundamental to understanding rendering, performance, keys, and state preservation.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Reconciliation |
| Level | Intermediate |
| Reading Time | 70–90 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | Rendering, Virtual DOM |
| Next Topic | Props |

---

# How It Connects

```
Rendering

↓

Virtual DOM

↓

Reconciliation

↓

DOM Updates
```

Rendering creates the next UI.

The Virtual DOM stores that UI.

Reconciliation compares the previous and new Virtual DOM trees.

Only then does React update the Browser DOM.

---

# Why This Matters

Without Reconciliation, React would need to recreate the entire DOM tree after every update.

Imagine typing one character into an input field.

Without comparison:

```
Destroy Everything

↓

Rebuild Everything
```

With Reconciliation:

```
Compare Trees

↓

Update Only Input Value
```

This dramatically reduces unnecessary browser work.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain what Reconciliation is.
- Understand why React compares trees.
- Explain React's Diffing Algorithm.
- Understand how React handles element updates.
- Explain why Keys exist.
- Understand state preservation.
- Prepare for Props and State.

---

# What is Reconciliation?

Reconciliation is the process of comparing two Virtual DOM trees to determine what has changed.

React asks one question:

> **"What is different?"**

Conceptually:

```
Old Virtual DOM

↓

Compare

↓

New Virtual DOM

↓

Generate Update List

↓

Commit Changes
```

Reconciliation does not update the DOM directly.

Instead, it produces a list of changes that React later applies during the Commit Phase.

---

# Why Compare Trees?

Imagine a dashboard.

```
Dashboard

├── Header

├── Sidebar

├── Statistics

├── Chart

└── Footer
```

Only the statistics value changes.

Without comparison:

```
Delete Entire Dashboard

↓

Create Entire Dashboard
```

With Reconciliation:

```
Compare Trees

↓

Statistics Changed

↓

Update One Text Node
```

Everything else remains untouched.

---

# The Diffing Algorithm

React's comparison process is called the **Diffing Algorithm**.

Its goal is simple:

> Find the minimum number of DOM updates required.

Conceptually:

```
Old Tree

↓

Diff

↓

New Tree

↓

List of Changes
```

React performs this comparison extremely quickly because it follows a few assumptions.

These assumptions make the algorithm practical for real-world applications.

---

# React's Two Core Assumptions

To avoid expensive comparisons, React assumes:

### Assumption 1

Elements with different types produce different trees.

Example:

```
<div>

↓

<section>
```

React assumes these trees are unrelated.

The old subtree is removed and a new one is created.

---

### Assumption 2

Developers provide stable Keys for lists.

Keys help React identify which items stayed the same, moved, were added, or were removed.

You'll study Keys in detail later in this module.

---

# Comparing Elements

When comparing two elements, React checks their type first.

Example:

Previous render:

```jsx
<h1>Hello</h1>
```

Next render:

```jsx
<h1>Welcome</h1>
```

The element type is the same.

Only the text changed.

Result:

```
Reuse DOM Node

↓

Update Text
```

---

Now consider:

Previous:

```jsx
<h1>Hello</h1>
```

Next:

```jsx
<p>Hello</p>
```

The types differ.

Result:

```
Remove h1

↓

Create p
```

React replaces the entire node because the element type changed.

---

# Reconciliation Is Recursive

React doesn't compare only the root element.

It recursively walks through the entire component tree.

Example:

```
App

├── Header

├── Sidebar

└── Main

    ├── Chart

    └── Statistics
```

Every level of the tree is examined independently.

Only the changed branches continue through the reconciliation process.
# Child Reconciliation

React compares the UI one level at a time.

This process is recursive, meaning React continues comparing child elements until it has examined the entire tree.

Consider the following component hierarchy.

```text
App

├── Header

├── Sidebar

├── Main

│   ├── Statistics

│   ├── Chart

│   └── Activity

└── Footer
```

Suppose only the `Statistics` component changes.

React performs reconciliation like this.

```text
App
    │
    ├── Header          ✓ No Changes
    │
    ├── Sidebar         ✓ No Changes
    │
    ├── Main
    │      │
    │      ├── Statistics    ✱ Changed
    │      │
    │      ├── Chart         ✓ Same
    │      │
    │      └── Activity      ✓ Same
    │
    └── Footer          ✓ No Changes
```

Only the affected branch continues through the update process.

Everything else is reused.

---

# Element Type Comparison

The very first thing React compares is the element type.

Example 1

Previous render

```jsx
<h1>Hello</h1>
```

Next render

```jsx
<h1>Welcome</h1>
```

Both elements have the same type.

```text
h1

↓

h1

↓

Reuse DOM Node

↓

Update Text
```

Only the text changes.

---

Example 2

Previous render

```jsx
<h1>Hello</h1>
```

Next render

```jsx
<p>Hello</p>
```

Now the type has changed.

```text
h1

↓

p

↓

Remove Old Node

↓

Create New Node
```

React destroys the old subtree and creates a new one.

---

# Component Type Comparison

The same rule applies to components.

Previous

```jsx
<UserCard />
```

Next

```jsx
<UserCard />
```

Same component type.

React attempts to preserve the existing component instance and compare its output.

---

Now consider:

Previous

```jsx
<UserCard />
```

Next

```jsx
<ProductCard />
```

Different component type.

React treats them as completely different trees.

```text
Unmount UserCard

↓

Mount ProductCard
```

The previous component is removed and a new component is created.

---

# Reconciliation Walkthrough

Let's follow an actual update.

Initial UI

```text
Dashboard

├── Header

├── Statistics

│      120 Users

└── Footer
```

A user is added.

New UI

```text
Dashboard

├── Header

├── Statistics

│      121 Users

└── Footer
```

React performs these steps.

```text
Render

↓

New Virtual DOM

↓

Compare Root

↓

Header Same

↓

Statistics Changed

↓

Footer Same

↓

Commit

↓

Update Statistics Text Only
```

Notice that neither the Header nor Footer is recreated.

---

# Why Doesn't React Compare Every Possibility?

Imagine comparing two trees containing thousands of nodes.

A perfect comparison algorithm would be extremely slow.

Instead, React uses heuristics.

React assumes:

• Different element types produce different trees.

• Developers provide stable keys for lists.

These assumptions reduce comparison time dramatically.

Instead of solving an expensive general tree comparison problem, React follows predictable rules that work well for most user interfaces.

---

# Recursive Tree Comparison

React compares the tree from top to bottom.

```text
App

↓

Header

↓

Navigation

↓

Menu Item
```

Every node is compared independently.

If React determines a subtree hasn't changed, it can avoid unnecessary work in deeper parts of that branch.

This recursive strategy helps React efficiently process even large component hierarchies.

---

# Engineering Perspective

Reconciliation is not about rebuilding the interface.

It is about identifying the **smallest possible set of changes** required to transform one UI tree into another.

By comparing element types, recursively walking the tree, and applying simple heuristics, React avoids expensive DOM operations while keeping the rendering model predictable.

Understanding this process explains why component identity, element types, and stable keys are so important in React applications.

# List Reconciliation

So far, we've compared individual elements.

However, React applications frequently render **lists** of elements.

Examples include:

- Product lists
- Chat messages
- Notifications
- Tables
- Navigation menus

Lists introduce a new challenge.

> **How does React know which item changed?**

This is where list reconciliation becomes important.

---

# A Simple Example

Suppose React renders:

```text
Users

1. Alex

2. John

3. Sarah
```

Later the application updates to:

```text
Users

1. Alex

2. David

3. Sarah
```

React compares both lists.

```text
Previous

Alex

John

Sarah

↓

Compare

↓

Current

Alex

David

Sarah
```

React identifies that only the second item changed.

Only that part of the UI is updated.

---

# Adding an Item

Now consider another update.

Previous list

```text
Alex

John

Sarah
```

New list

```text
Alex

John

Sarah

Emma
```

React detects:

```text
First Item

↓

Same

Second Item

↓

Same

Third Item

↓

Same

Fourth Item

↓

New
```

Only one new DOM node is created.

---

# Removing an Item

Previous

```text
Alex

John

Sarah
```

Current

```text
Alex

Sarah
```

React identifies:

```text
John

↓

Removed
```

The corresponding DOM node is removed.

The remaining nodes are preserved whenever possible.

---

# Reordering Items

Reordering is much more challenging.

Previous

```text
Alex

John

Sarah
```

Current

```text
Sarah

Alex

John
```

Without additional information,

React cannot reliably determine whether:

- Items moved
- Items were removed
- New items were created

This is why **Keys** exist.

---

# Why React Needs Keys

Imagine identical boxes without labels.

```text
□

□

□
```

If someone rearranges them,

how would you know which box is which?

You couldn't.

Now add labels.

```text
A

B

C
```

After reordering:

```text
C

A

B
```

You immediately know which item moved.

Keys work exactly the same way.

They give every element a stable identity.

---

# What Are Keys?

A **Key** is a unique identifier assigned to elements inside a list.

Example:

```jsx
users.map(user => (
    <UserCard
        key={user.id}
        user={user}
    />
))
```

React uses the `key` to identify each element across renders.

Notice something important.

The key is **not** passed to the component as a prop.

It is used internally by React during reconciliation.

---

# Without Keys

Imagine this list.

```text
Apple

Banana

Orange
```

Now insert a new item at the beginning.

```text
Mango

Apple

Banana

Orange
```

Without keys,

React compares by position.

```text
Apple

↓

Mango

Banana

↓

Apple

Orange

↓

Banana
```

Every item appears different.

React performs far more work than necessary.

---

# With Keys

Now every item has an identity.

```text
1 Apple

2 Banana

3 Orange
```

After insertion:

```text
4 Mango

1 Apple

2 Banana

3 Orange
```

React immediately recognizes:

```text
1

↓

Same

2

↓

Same

3

↓

Same

4

↓

New
```

Only one new element is created.

Everything else is preserved.

---

# Stable Keys

Keys should remain stable across renders.

Good examples:

```jsx
key={user.id}

key={product.id}

key={email.id}
```

Bad examples:

```jsx
key={Math.random()}

key={Date.now()}
```

These values change every render.

React assumes every item is new.

This destroys many of React's optimizations.

---

# Using Array Index as Key

Many beginners write:

```jsx
items.map((item, index) => (

    <Item

        key={index}

    />

))
```

This works for static lists,

but it becomes problematic when:

- Items are inserted
- Items are deleted
- Items are reordered

Indexes change,

so React may associate the wrong DOM node with the wrong data.

As a general rule:

✅ Use stable IDs whenever possible.

Only use indexes when the list is completely static.

---

# Component Identity

Keys don't just help React update the DOM.

They also determine **component identity**.

Identity answers an important question.

> **Is this the same component as before?**

If React determines the answer is **yes**,

the existing component is reused.

If the answer is **no**,

the old component is removed and a new one is created.

This directly affects component state.

---

# State Preservation

Suppose a component contains local state.

```text
Counter

↓

Count = 10
```

If React determines that the component is still the same,

its state is preserved.

```text
Counter

↓

Count = 10

↓

Render Again

↓

Count = 10
```

Nothing is lost.

---

# State Reset

Now imagine React determines that the component is different.

```text
Old Component

↓

Unmount

↓

New Component

↓

Mount
```

The previous state disappears.

The new component starts with fresh state.

This is why changing component types or unstable keys can unexpectedly reset user input, form values, or other local state.

---

> 🏗️ Engineering Note
>
> Reconciliation is about more than updating the DOM.
>
> It also determines **component identity**.
>
> Identity influences whether React preserves or discards component state.
>
> Understanding this behavior is essential for building predictable React applications.

# Performance Implications

Reconciliation is one of the key reasons React applications can remain responsive even as they grow in complexity.

Instead of rebuilding the entire user interface after every update, React performs three steps:

1. Calculate the next UI.
2. Compare it with the previous UI.
3. Update only what changed.

Conceptually:

```text
State Changes

↓

Render

↓

Reconciliation

↓

Minimal DOM Updates

↓

Browser Paint
```

This dramatically reduces expensive browser operations.

---

# Why Browser DOM Updates Are Expensive

Creating JavaScript objects is generally inexpensive.

Updating the Browser DOM is much more costly because it may require:

- Creating or removing DOM nodes
- Updating attributes
- Recalculating styles
- Performing layout calculations
- Repainting pixels
- Compositing layers

Conceptually:

```text
JavaScript Object

↓

Cheap

-----------------------

Browser DOM Update

↓

Expensive
```

React's reconciliation process minimizes these expensive operations whenever possible.

---

# How Reconciliation Improves Performance

Imagine a dashboard with 500 components.

A user changes one notification count.

Without reconciliation:

```text
500 Components

↓

500 DOM Updates
```

With reconciliation:

```text
500 Components

↓

Compare Trees

↓

1 Changed Node

↓

1 DOM Update
```

The browser performs far less work.

---

# Reconciliation Isn't Magic

Although reconciliation is highly efficient, it is not free.

React still needs to:

- Execute components
- Create new React Elements
- Build a new Virtual DOM tree
- Compare trees

Poor component design can still result in unnecessary rendering work.

Examples include:

- Frequently changing unstable keys
- Rendering extremely large component trees unnecessarily
- Passing new object or function references on every render without need

Understanding reconciliation helps you recognize and avoid these patterns.

---

# Engineering Perspective

Reconciliation is a trade-off.

React performs additional JavaScript work so that it can reduce much more expensive Browser DOM work.

Modern browsers are highly optimized for executing JavaScript.

However, DOM manipulation, layout calculation, and painting remain relatively expensive operations.

React's architecture is designed around this principle:

> Spend a little time calculating.

> Save a lot of time updating the browser.

This trade-off enables React applications to remain predictable while efficiently updating complex user interfaces.

---

# Best Practices

## Use Stable Keys

Always prefer stable identifiers.

Good:

```jsx
key={user.id}
```

Avoid:

```jsx
key={Math.random()}
```

Stable keys allow React to correctly identify elements between renders.

---

## Preserve Component Identity

Whenever possible, keep component types consistent.

Instead of switching between unrelated component types unnecessarily, update their content through Props or State.

This allows React to preserve component state.

---

## Keep Components Focused

Smaller, well-defined components produce smaller reconciliation units.

Example:

```text
Dashboard

├── Header

├── Sidebar

├── Statistics

└── Footer
```

Instead of one very large component.

---

## Avoid Unnecessary Re-renders

Although rendering is inexpensive, unnecessary work still adds up in large applications.

Design components so they receive only the data they actually need.

Later modules will introduce optimization techniques such as:

- React.memo
- useMemo
- useCallback

---

# Common Mistakes

## Mistake 1

Using unstable keys.

```jsx
key={Math.random()}
```

This forces React to treat every item as new.

---

## Mistake 2

Using array indexes for dynamic lists.

```jsx
key={index}
```

When items move, React may preserve the wrong component identity.

---

## Mistake 3

Thinking reconciliation rebuilds the whole page.

React updates only the parts that actually changed.

---

## Mistake 4

Confusing rendering with reconciliation.

Rendering:

```text
Calculate UI
```

Reconciliation:

```text
Compare UI Trees
```

Commit:

```text
Update Browser DOM
```

Each phase has a different responsibility.

---

# Real-World Example

Imagine a messaging application.

```text
Messages

├── Alex

├── John

├── Sarah

└── Emma
```

A new message arrives from Sarah.

Without reconciliation:

```text
Rebuild Entire Message List
```

With reconciliation:

```text
Previous Tree

↓

Compare

↓

Sarah Updated

↓

Update One Message

↓

Preserve Everything Else
```

Only the affected message is updated.

This approach scales efficiently even when thousands of messages are displayed.

---

# Key Takeaways

✅ Reconciliation compares two Virtual DOM trees.

✅ React uses a diffing algorithm to identify changes.

✅ Elements with different types are treated as different trees.

✅ Stable keys help React preserve element identity.

✅ Reconciliation determines both DOM updates and component identity.

✅ Preserving identity allows React to preserve component state.

---

# Interview Questions

## Beginner

1. What is Reconciliation?

2. Why does React compare Virtual DOM trees?

3. What is the purpose of the Diffing Algorithm?

4. Why doesn't React rebuild the entire page?

---

## Intermediate

5. What assumptions does React's Diffing Algorithm make?

6. How does React compare elements?

7. Why are keys important?

8. What happens when an element's type changes?

---

## Advanced

9. How does reconciliation preserve component state?

10. Why can unstable keys cause performance issues?

11. Explain the relationship between Rendering, Virtual DOM, and Reconciliation.

12. How does reconciliation reduce Browser DOM work?

---

# Hands-on Exercises

## Exercise 1

Create a list of users.

Add a new user.

Observe how React updates only the new list item.

---

## Exercise 2

Replace stable IDs with array indexes.

Insert a new item at the beginning of the list.

Observe how component identity changes.

---

## Exercise 3

Replace:

```jsx
<UserCard />
```

with:

```jsx
<ProductCard />
```

Observe how React unmounts one component and mounts another.

---

## Exercise 4

Draw the complete update pipeline.

```text
State Change

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

Explain the responsibility of each step.

---

# Summary

Reconciliation is React's process for comparing the previous and new Virtual DOM trees.

Instead of rebuilding the entire interface, React identifies the smallest set of changes required to synchronize the Browser DOM with the application's current state.

This process relies on the Diffing Algorithm, component identity, and stable keys to preserve state, minimize DOM updates, and keep applications performant.

Understanding reconciliation is essential because it explains many of React's core behaviors, including rendering performance, state preservation, and list rendering.

---

# Knowledge Check

Before moving on, verify that you can answer the following questions.

- What is Reconciliation?
- What is the Diffing Algorithm?
- Why does React compare Virtual DOM trees?
- Why are keys important?
- What happens when an element type changes?
- Why does changing a key sometimes reset component state?
- How does reconciliation improve performance?

If you can confidently answer these questions, you're ready to move on to **Props**.

---

# Further Reading

- 📖 Props
- 📖 State
- 📖 Rendering Lists
- 📖 Keys

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Virtual DOM | ↑ React Core Concepts | 🗺 Module Home | Props → |

---

# Continue Your Journey

You've now completed React's rendering pipeline.

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
```

From this point forward, you'll focus on how applications become dynamic.

The next chapter introduces **Props**—React's mechanism for passing data from parent components to child components. Props make reusable components configurable and establish React's one-way data flow model.

- ⬅ **Previous:** [05 - Virtual DOM](05-virtual-dom.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [07 - Props](07-props.md)