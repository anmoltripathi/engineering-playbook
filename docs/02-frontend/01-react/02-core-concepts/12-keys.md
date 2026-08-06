# Keys

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
> → Keys

---

# Overview

In the previous chapter, you learned how React renders arrays using `map()`.

Example:

```jsx
employees.map(employee => (

    <EmployeeCard

        employee={employee}

    />

));
```

Soon after writing code like this, React displays a warning.

```
Warning:

Each child in a list should have a unique "key" prop.
```

Many developers immediately fix the warning.

```jsx
key={employee.id}
```

The warning disappears.

Problem solved.

Or is it?

Not really.

The warning is only a symptom.

The real question is:

> **Why does React need Keys at all?**

The answer has nothing to do with removing warnings.

Keys allow React to identify elements across renders.

Without Keys, React cannot reliably determine:

- Which item stayed the same.
- Which item moved.
- Which item was removed.
- Which item was inserted.

Keys are the foundation of React's reconciliation algorithm for lists.

Understanding Keys also explains:

- Component identity
- State preservation
- Efficient DOM updates
- Reordering behavior

---

# How It Connects

```text
Rendering Lists

↓

Multiple Components

↓

Identity Problem

↓

Keys

↓

Reconciliation

↓

State Preservation

↓

Efficient DOM Updates
```

Rendering Lists creates multiple components.

Keys allow React to distinguish between them.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Keys |
| Level | Intermediate |
| Reading Time | 70–90 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 120 Minutes |
| Prerequisites | Rendering Lists, Reconciliation |
| Next Topic | Component Composition |

---

# Why This Matters

Every production React application renders lists.

Examples:

- Employees
- Products
- Orders
- Notifications
- Messages
- Tasks
- Files
- Reports

Whenever data changes,

React must determine what happened.

Keys make this possible.

Without stable Keys:

- State can move to the wrong component.
- Performance suffers.
- UI bugs appear.
- Forms lose user input.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain why Keys exist.
- Understand component identity.
- Explain how Keys help Reconciliation.
- Choose good Keys.
- Avoid unstable Keys.
- Understand why array indexes are problematic.
- Explain how Keys preserve State.

---

# The Problem Keys Solve

Imagine an employee list.

```
John

Sarah

Alex
```

Later,

a new employee joins.

```
Emma

John

Sarah

Alex
```

React now compares:

```text
Old List

↓

New List
```

Without additional information,

React doesn't know whether:

- Emma is new.
- John moved.
- Sarah moved.
- Alex moved.

It simply sees different positions.

This creates an identity problem.

---

# Identity

Imagine identical luggage at an airport.

```
🧳

🧳

🧳
```

Someone rearranges them.

Which suitcase belongs to whom?

Impossible to know.

Now add luggage tags.

```
A

B

C
```

After rearranging:

```
C

A

B
```

Each suitcase still has the same identity.

Keys work exactly the same way.

---

# What is a Key?

A Key is a unique identifier that React uses to distinguish one element from another.

Example:

```jsx
employees.map(employee => (

    <EmployeeCard

        key={employee.id}

        employee={employee}

    />

));
```

Notice something important.

The Key is **not** passed into the component.

```jsx
function EmployeeCard(props) {

}
```

There is **no**:

```jsx
props.key
```

because React consumes Keys internally.

Keys exist for React—not for your component.

---

# How React Sees a List

Imagine this JSX.

```jsx
employees.map(employee => (

    <EmployeeCard

        key={employee.id}

        employee={employee}

    />

));
```

React conceptually sees:

```text
Key: 101

↓

<EmployeeCard>

-------------------

Key: 102

↓

<EmployeeCard>

-------------------

Key: 103

↓

<EmployeeCard>
```

The key becomes the identity of each element.

When rendering happens again,

React compares identities rather than positions.

---

# Without Keys

Suppose React compares by position.

Old list:

```text
John

Sarah

Alex
```

New list:

```text
Emma

John

Sarah

Alex
```

React sees:

```text
Position 1

↓

Changed

Position 2

↓

Changed

Position 3

↓

Changed

Position 4

↓

New
```

Nearly everything appears different.

This leads to unnecessary work.

---

# With Keys

Now every employee has an ID.

Old:

```text
101 John

102 Sarah

103 Alex
```

New:

```text
104 Emma

101 John

102 Sarah

103 Alex
```

React compares:

```text
101

↓

Same

102

↓

Same

103

↓

Same

104

↓

New
```

React immediately understands what happened.

Only one component needs to be created.

The others are preserved.

---

# Keys Enable Reconciliation

Recall the Reconciliation chapter.

React compares two Virtual DOM trees.

Keys make that comparison much more accurate.

Conceptually:

```text
Previous Tree

↓

Keys

↓

Current Tree

↓

Compare Identity

↓

Generate Updates
```

Keys reduce unnecessary DOM operations and preserve component identity.

---

> 🏗️ Engineering Note
>
> Keys are not a rendering feature.
>
> They are an **identity mechanism**.
>
> React uses them during reconciliation to determine whether two elements represent the same logical component across different renders.

# Component Identity

The most important thing to understand about Keys is this:

> **Keys define the identity of a component.**

Imagine two renders.

First render:

```text
Employee

Key = 101
```

Second render:

```text
Employee

Key = 101
```

React concludes:

```text
Same Key

↓

Same Component

↓

Preserve State

↓

Update Props
```

Now imagine:

First render:

```text
Employee

Key = 101
```

Second render:

```text
Employee

Key = 205
```

React concludes:

```text
Different Key

↓

Different Component

↓

Unmount Old

↓

Mount New

↓

New State
```

Changing a key tells React:

> "This is not the same component anymore."

---

# Keys Preserve State

Consider a list of editable employees.

```text
John

Sarah

Alex
```

Each row contains an input.

```jsx
<EmployeeRow />
```

Internally each row has State.

```text
EmployeeRow

↓

inputValue
```

Suppose Sarah types:

```
Senior Accountant
```

React stores:

```text
Key 102

↓

State

↓

"Senior Accountant"
```

Now another employee is inserted above Sarah.

Without stable Keys,

React may think Sarah became another row.

The input value can suddenly appear under the wrong employee.

Stable Keys prevent this.

---

# Visualizing State Preservation

Imagine React's internal memory.

Before update:

```text
101

↓

John

↓

State A

----------------

102

↓

Sarah

↓

State B

----------------

103

↓

Alex

↓

State C
```

New employee inserted:

```text
104 Emma

101 John

102 Sarah

103 Alex
```

React compares Keys.

```text
104

↓

New Component

----------------

101

↓

Reuse State A

----------------

102

↓

Reuse State B

----------------

103

↓

Reuse State C
```

Every employee keeps the correct State.

---

# When State Resets

Sometimes resetting State is exactly what you want.

Example:

```jsx
<UserProfile

    key={user.id}

    user={user}

/>
```

Suppose:

```text
User A

↓

Edit Form
```

Switch to:

```text
User B
```

Because the Key changes,

React creates a brand-new component.

Result:

```text
Old State Removed

↓

New Empty Form

↓

Fresh Component
```

This is a legitimate use of changing Keys.

---

# The Problem with Array Indexes

Many beginners write:

```jsx
employees.map((employee, index) => (

    <EmployeeCard

        key={index}

        employee={employee}

    />

));
```

Initially:

```text
0 John

1 Sarah

2 Alex
```

Insert Emma at the beginning.

```text
0 Emma

1 John

2 Sarah

3 Alex
```

Notice what happened.

John's Key changed.

Sarah's Key changed.

Alex's Key changed.

React now thinks almost every component is different.

---

# Why Index Keys Cause Bugs

Imagine each employee row contains:

- Checkbox
- Input
- Expanded panel
- Selected state

Using index keys:

```text
0

↓

John

↓

Checked
```

Insert Emma.

Now:

```text
0

↓

Emma

↓

Checked
```

The checkbox appears on the wrong employee.

React preserved State,

but for the wrong component.

This is one of the most common React bugs.

---

# Good Keys

A good Key should satisfy three properties.

## Unique

Every sibling should have a different Key.

Good:

```jsx
key={employee.id}
```

---

## Stable

The Key should not change between renders.

Good:

```jsx
employee.id
```

Bad:

```jsx
Date.now()
```

---

## Predictable

The same data should always produce the same Key.

Avoid randomly generated values.

---

# Bad Keys

Avoid:

```jsx
key={Math.random()}
```

Every render creates a new Key.

React thinks every component is brand new.

---

Avoid:

```jsx
key={Date.now()}
```

Keys constantly change.

State cannot be preserved.

---

Avoid:

```jsx
key={crypto.randomUUID()}
```

inside rendering.

Although UUIDs are unique,

generating new ones during every render defeats the purpose of Keys.

Generate IDs when creating the data,

not while rendering.

---

# Nested Lists

Nested collections also require Keys.

Example:

```text
Department

↓

Employees
```

Example:

```jsx
departments.map(department => (

    <Department

        key={department.id}

        department={department}

    />

));
```

Inside:

```jsx
department.employees.map(employee => (

    <EmployeeRow

        key={employee.id}

        employee={employee}

    />

));
```

Each level manages its own Keys.

---

# Dynamic Lists

Lists often change.

Users can:

- Add items
- Delete items
- Reorder items
- Filter items
- Sort items

Keys allow React to understand these changes.

Conceptually:

```text
Old List

↓

Keys

↓

Compare

↓

Insert

↓

Remove

↓

Move

↓

Reuse
```

Without stable Keys,

React cannot accurately track these operations.

---

# Keys During Reconciliation

Remember the reconciliation pipeline.

```text
Previous Virtual DOM

↓

Current Virtual DOM

↓

Compare Keys

↓

Compare Types

↓

Reuse Components

↓

Update DOM
```

Keys are one of the first things React checks when comparing lists.

Without Keys,

React falls back to comparing positions,

which is much less reliable.

---

> 🏗️ Engineering Note
>
> Keys are **not about performance first**.
>
> Their primary purpose is to preserve **component identity**.
>
> Performance improvements are a consequence of React being able to correctly identify which components can be reused instead of recreated.

# Engineering Perspective

Keys are one of the most misunderstood features in React.

Many developers believe Keys exist simply to remove React warnings.

In reality, Keys are a fundamental part of React's reconciliation algorithm.

React does not identify components by:

- Their position in the UI
- Their displayed content
- Their Props

Instead, React identifies components by their:

```text
Component Type

+

Key
```

Together, these define a component's identity.

This identity determines whether React should:

- Reuse an existing component
- Preserve its State
- Update its Props
- Remove it
- Create a new one

Keys are therefore an architectural concept, not merely a syntax requirement.

---

# Under the Hood

Imagine the following list.

First Render

```text
Key:101 → John

Key:102 → Sarah

Key:103 → Alex
```

Second Render

```text
Key:104 → Emma

Key:101 → John

Key:102 → Sarah

Key:103 → Alex
```

React performs something conceptually similar to:

```text
Old Virtual DOM

↓

Find Key 101

↓

Reuse Component

↓

Find Key 102

↓

Reuse Component

↓

Find Key 103

↓

Reuse Component

↓

Find Key 104

↓

Create New Component
```

Notice that React never compares names.

It compares identities.

---

# Identity vs Position

This is the most important mental model in React.

Without Keys:

```text
Position

↓

Identity
```

With Keys:

```text
Key

↓

Identity

↓

State Preservation
```

React does not care where an element appears.

React cares whether it represents the same logical component.

---

# Best Practices

## Use Stable Database IDs

Best:

```jsx
key={employee.id}
```

Database IDs remain stable across renders.

---

## Keep Keys Close to the Array

Correct:

```jsx
employees.map(employee => (

    <EmployeeCard

        key={employee.id}

        employee={employee}

    />

))
```

Don't move Keys inside `EmployeeCard`.

React needs them where the list is created.

---

## Keys Must Be Unique Among Siblings

This is valid:

```text
Department A

Employee 1

Employee 2

----------------

Department B

Employee 1

Employee 2
```

Keys only need to be unique within the same list.

They do not need to be globally unique.

---

## Generate IDs When Data is Created

Good:

```text
Create Employee

↓

Generate ID

↓

Store ID

↓

Render
```

Bad:

```text
Render

↓

Generate Random ID

↓

Render Again

↓

Different ID
```

A changing key breaks component identity.

---

## Prefer Real IDs Over Array Indexes

Good:

```jsx
key={employee.id}
```

Avoid:

```jsx
key={index}
```

unless the list is completely static and will never change.

---

# Common Mistakes

## Mistake 1

Using:

```jsx
key={Math.random()}
```

Every render creates a new component.

State is always lost.

---

## Mistake 2

Using:

```jsx
key={Date.now()}
```

Keys constantly change.

React cannot preserve identity.

---

## Mistake 3

Using Array Indexes

```jsx
key={index}
```

Works initially.

Breaks when:

- Items move
- Items are removed
- Items are inserted

---

## Mistake 4

Forgetting Keys

```jsx
employees.map(employee => (

    <EmployeeCard

        employee={employee}

    />

))
```

React cannot reliably identify components.

---

## Mistake 5

Expecting Keys Inside Props

This will not work.

```jsx
props.key
```

Keys are consumed internally by React.

If your component needs an identifier,

pass it separately.

```jsx
<EmployeeCard

    key={employee.id}

    employeeId={employee.id}

/>
```

---

# Real-World Example

Imagine a payroll management system.

Employees:

```text
John

Sarah

Alex
```

HR adds a new employee.

```text
Emma

John

Sarah

Alex
```

Without Keys:

```text
Position Changed

↓

Wrong Component Reused

↓

Incorrect Input Values

↓

Checkboxes Move

↓

UI Bugs
```

With Keys:

```text
Employee ID

↓

Identity Preserved

↓

Correct State

↓

Minimal DOM Updates
```

This is why enterprise applications always use stable identifiers.

---

# Quick Reference

| Situation | Recommended Key |
|------------|-----------------|
| Database record | `id` |
| UUID stored in data | `uuid` |
| Email (if unique) | `email` |
| Static list | Index (acceptable only if the list never changes) |
| Dynamic list | Stable unique ID |
| Random value | ❌ Never |

---

# Key Takeaways

✅ Keys identify React elements across renders.

✅ Keys preserve component identity.

✅ Stable Keys preserve component State.

✅ Changing a Key creates a new component.

✅ React compares Keys during reconciliation.

✅ Array indexes should generally be avoided for dynamic lists.

---

# Interview Questions

## Beginner

1. What is a Key in React?

2. Why does React require Keys?

3. Where should the Key prop be placed?

4. Can a component access its own Key?

---

## Intermediate

5. Why are array indexes discouraged?

6. How do Keys help reconciliation?

7. What makes a good Key?

8. Why should Keys remain stable?

---

## Advanced

9. Explain the relationship between Keys and component identity.

10. How do Keys preserve component State?

11. What happens when a Key changes?

12. Explain how React compares two lists during reconciliation.

---

# Hands-on Exercises

## Exercise 1

Render an employee list using:

```jsx
key={employee.id}
```

Insert a new employee at the beginning.

Observe that existing rows preserve their state.

---

## Exercise 2

Replace:

```jsx
key={employee.id}
```

with:

```jsx
key={index}
```

Repeat the insertion.

Observe how component state moves unexpectedly.

---

## Exercise 3

Build a Todo application.

Requirements:

- Add items
- Delete items
- Reorder items

Use stable IDs for every Todo.

---

## Exercise 4

Create nested lists:

- Departments
- Employees

Assign appropriate Keys at both levels.

---

# Summary

Keys provide a stable identity for React elements rendered from collections.

During reconciliation, React compares Keys to determine which components can be reused, which should be removed, and which need to be created.

This preserves component state, minimizes DOM updates, and keeps applications predictable even when lists change.

Understanding Keys is essential for building reliable, scalable React applications.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What is a React Key?
- Why does React use Keys?
- Why aren't Keys passed as Props?
- What makes a good Key?
- Why are array indexes risky?
- How do Keys preserve State?
- How do Keys improve reconciliation?

If you can confidently answer these questions, you're ready for **Component Composition**.

---

# Further Reading

- 📖 Component Composition
- 📖 Thinking in React
- 📖 React.memo (later module)
- 📖 Performance Optimization (later module)

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Rendering Lists | ↑ React Core Concepts | 🗺 Module Home | Component Composition → |

---

# Continue Your Journey

You've learned how React identifies components across renders using **Keys**.

```text
Array

↓

map()

↓

Keys

↓

Component Identity

↓

Reconciliation

↓

State Preservation

↓

Browser DOM
```

With **Props**, **State**, **Events**, **Conditional Rendering**, **Rendering Lists**, and **Keys**, you now understand how individual React components behave.

In the next chapter, you'll learn **Component Composition**—how to combine small, reusable components into larger features and complete application interfaces.

- ⬅ **Previous:** [11 - Rendering Lists](11-rendering-lists.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [13 - Component Composition](13-component-composition.md)