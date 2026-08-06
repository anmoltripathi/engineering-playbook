# Events

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
> → Events

---

# Overview

So far in this module, you've learned how React applications are built and how components manage data using **Props** and **State**.

However, one important question remains.

> **How does State actually change?**

Imagine a button.

```
Count: 0

[ Increment ]
```

The user clicks the button.

Now the UI becomes:

```
Count: 1
```

What caused that update?

The answer is **Events**.

Events are React's mechanism for responding to user interactions.

Every time a user:

- clicks a button,
- types into an input,
- submits a form,
- moves the mouse,
- presses a key,

React can execute JavaScript code.

That code usually updates State.

State updates trigger rendering.

Rendering updates the user interface.

Events connect users to your application.

Without Events, React applications would display information but users couldn't interact with them.

---

# How It Connects

```text
Props

↓

State

↓

Events

↓

State Update

↓

Rendering

↓

Updated UI
```

Props provide data.

State stores changing data.

Events request changes to State.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Events |
| Level | Beginner → Intermediate |
| Reading Time | 60–75 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | State |
| Next Topic | Conditional Rendering |

---

# Why This Matters

Every interactive feature in React depends on Events.

Examples include:

- Buttons
- Forms
- Search bars
- Dropdowns
- Checkboxes
- Keyboard shortcuts
- Drag & Drop
- File Uploads
- Context Menus

Without Events,

applications would be static.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain what Events are.
- Attach event handlers.
- Handle user interactions.
- Pass arguments to event handlers.
- Understand Synthetic Events.
- Prevent default browser behavior.
- Stop event propagation.
- Connect Events with State updates.
- Build interactive React components.

---

# The Problem Events Solve

Imagine building a Like button.

```text
❤️ Like
```

The user clicks.

Now it should display:

```text
❤️ Liked
```

Something must detect that click.

Something must execute JavaScript.

Something must update State.

That "something" is an Event Handler.

---

# What is an Event?

An Event is an action that occurs inside the browser.

Examples:

- Mouse Click
- Keyboard Press
- Input Change
- Form Submit
- Mouse Hover
- Scroll
- Drag
- Drop

React listens for these browser events and allows your components to respond to them.

Conceptually:

```text
User

↓

Clicks Button

↓

React Event

↓

Event Handler

↓

State Update

↓

Render

↓

Updated UI
```

---

# Event Handlers

An Event Handler is simply a JavaScript function.

Example:

```jsx
function handleClick() {

    console.log("Button clicked");

}
```

This function executes whenever the associated event occurs.

---

# Attaching an Event Handler

React uses camelCase event names.

Example:

```jsx
<button

    onClick={handleClick}

>

    Click Me

</button>
```

Notice:

```jsx
onClick
```

not

```html
onclick
```

React follows JavaScript naming conventions rather than HTML attribute names.

---

# What Happens When a Button is Clicked?

Suppose the user clicks:

```jsx
<button

    onClick={handleClick}

>

    Save

</button>
```

Flow:

```text
User Click

↓

Browser Event

↓

React Synthetic Event

↓

handleClick()

↓

JavaScript Executes
```

If the handler updates State:

```text
setCount()

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

Everything you've learned in previous chapters now comes together.

---

# Inline Event Handlers

Handlers can also be written inline.

Example:

```jsx
<button

    onClick={() => {

        console.log("Clicked");

    }}

>

    Click

</button>
```

Although convenient,

large inline handlers reduce readability.

Prefer named functions when the logic becomes more complex.

---

# Passing Arguments

Sometimes an event handler needs additional information.

Incorrect:

```jsx
<button

    onClick={handleDelete(id)}

>
```

This executes immediately during rendering.

Correct:

```jsx
<button

    onClick={() => handleDelete(id)}

>
```

Flow:

```text
Render

↓

Create Function

↓

User Click

↓

Function Executes

↓

handleDelete(id)
```

---

# Updating State from Events

This is the most common pattern in React.

```jsx
function Counter() {

    const [

        count,

        setCount

    ] = useState(0);

    function handleIncrement() {

        setCount(count + 1);

    }

    return (

        <button

            onClick={handleIncrement}

        >

            {count}

        </button>

    );

}
```

Flow:

```text
User Click

↓

Event Handler

↓

setCount()

↓

Render

↓

Updated UI
```

This is the fundamental interaction model of React.

# React Synthetic Events

So far you've learned that React responds to browser events.

However, React does **not** expose native browser events directly.

Instead, React wraps them inside a **Synthetic Event**.

This provides a consistent event system across different browsers.

---

# What is a Synthetic Event?

A Synthetic Event is a React object that wraps the browser's native event.

Conceptually:

```text
User Click

↓

Browser Event

↓

React Synthetic Event

↓

Event Handler
```

Instead of working with browser-specific implementations,

React provides a consistent API.

This means your event-handling code behaves the same across modern browsers.

---

# Why Does React Use Synthetic Events?

Different browsers have historically implemented events differently.

React hides these differences.

Benefits include:

- Consistent behavior
- Cross-browser compatibility
- Simpler API
- Predictable event handling

As a React developer, you rarely need to worry about browser-specific event differences.

---

# The Event Object

Every event handler automatically receives an event object.

Example:

```jsx
function handleClick(event) {

    console.log(event);

}

<button

    onClick={handleClick}

>
    Click
</button>
```

The `event` object contains information about what happened.

Examples include:

- Which element triggered the event
- Mouse position
- Keyboard key pressed
- Input value
- Modifier keys (Ctrl, Shift, Alt)

---

# Common Event Properties

Some frequently used properties are:

```jsx
event.target
```

The element that triggered the event.

---

```jsx
event.currentTarget
```

The element whose handler is currently executing.

---

```jsx
event.type
```

The event type.

Examples:

```text
click

change

submit

keydown
```

---

```jsx
event.preventDefault()
```

Prevents the browser's default behavior.

---

```jsx
event.stopPropagation()
```

Stops the event from bubbling to parent elements.

We'll study both shortly.

---

# Common React Events

React supports many event types.

Here are the most frequently used ones.

| Event | Description |
|--------|-------------|
| onClick | Mouse click |
| onChange | Input value changes |
| onSubmit | Form submission |
| onKeyDown | Key pressed |
| onKeyUp | Key released |
| onFocus | Element receives focus |
| onBlur | Element loses focus |
| onMouseEnter | Mouse enters element |
| onMouseLeave | Mouse leaves element |

React event names always use **camelCase**.

Example:

```jsx
onClick
```

Not:

```html
onclick
```

---

# Working with Input Events

One of the most common React patterns is handling user input.

Example:

```jsx
function SearchBox() {

    const [

        search,

        setSearch

    ] = useState("");

    function handleChange(event) {

        setSearch(event.target.value);

    }

    return (

        <input

            value={search}

            onChange={handleChange}

        />

    );

}
```

Flow:

```text
User Types

↓

onChange

↓

Event Object

↓

event.target.value

↓

setSearch()

↓

Render

↓

Updated Input
```

---

# Form Submission

HTML forms normally reload the page when submitted.

Example:

```html
<form>

</form>
```

React applications usually prevent this behavior.

Example:

```jsx
function handleSubmit(event) {

    event.preventDefault();

    console.log("Form Submitted");

}
```

Attach it:

```jsx
<form

    onSubmit={handleSubmit}

>
```

Flow:

```text
Submit Button

↓

Browser Wants to Reload

↓

preventDefault()

↓

Stay on Same Page

↓

React Handles Submission
```

---

# preventDefault()

Many browser actions have default behavior.

Examples include:

- Form submission
- Opening links
- Right-click menus

React allows you to prevent these defaults.

Example:

```jsx
event.preventDefault();
```

Conceptually:

```text
Browser Default

↓

Blocked

↓

React Logic Runs
```

This is commonly used with forms and links.

---

# stopPropagation()

Events normally travel upward through the DOM.

Example:

```text
Button

↓

Card

↓

Dashboard
```

Clicking the button also triggers parent click handlers.

Sometimes this isn't desirable.

Example:

```jsx
event.stopPropagation();
```

Flow:

```text
Button Click

↓

Handler Executes

↓

Propagation Stops

↓

Parent Doesn't Receive Event
```

---

# Event Bubbling

By default, events bubble upward.

Example:

```text
App

↓

Card

↓

Button
```

User clicks the button.

Execution order:

```text
Button

↓

Card

↓

App
```

This behavior is called **Event Bubbling**.

React follows the browser's bubbling model.

---

# Event Capturing

Events can also travel in the opposite direction.

```text
App

↓

Card

↓

Button
```

Capture order:

```text
App

↓

Card

↓

Button
```

Although React supports capturing,

most applications primarily use bubbling.

---

# Mouse Events

React provides many mouse-related events.

Examples:

```jsx
onClick

onDoubleClick

onMouseEnter

onMouseLeave

onMouseMove
```

These are useful for:

- Tooltips
- Menus
- Hover effects
- Drag-and-drop interactions

---

# Keyboard Events

Keyboard events are essential for accessibility and productivity.

Examples:

```jsx
onKeyDown

onKeyUp
```

Example:

```jsx
function handleKeyDown(event) {

    if (event.key === "Enter") {

        console.log("Search");

    }

}
```

This enables keyboard shortcuts and form interactions.

---

# Event Flow

Everything you've learned connects together.

```text
User Interaction

↓

Browser Event

↓

React Synthetic Event

↓

Event Handler

↓

setState()

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

This is the complete lifecycle of a user interaction in React.

---

> 🏗️ Engineering Note
>
> React's event system is designed to provide a consistent programming model across browsers.
>
> Rather than handling browser-specific quirks, developers interact with a predictable Synthetic Event API.
>
> Most event handlers ultimately trigger State updates, allowing React to recalculate and efficiently update the user interface.

# Engineering Perspective

Events are the bridge between the user and your application.

Without events, a React application can display information but cannot respond to user actions.

From React's perspective, every interaction follows the same lifecycle.

```text
User Interaction

↓

Event Triggered

↓

Event Handler Executes

↓

State Updates

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

Notice that **events themselves do not update the UI**.

Events execute JavaScript.

That JavaScript usually updates State.

State changes trigger React's rendering pipeline.

This separation makes React applications predictable and easy to reason about.

---

# Best Practices

## Keep Event Handlers Small

An event handler should focus on one responsibility.

Good:

```jsx
function handleSave() {

    saveUser();

}
```

Avoid putting hundreds of lines of business logic directly inside an event handler.

Move complex logic into helper functions or services.

---

## Use Named Functions

For simple handlers, inline functions are acceptable.

```jsx
<button

    onClick={() => setOpen(true)}

>
```

For larger logic, prefer named functions.

```jsx
function handleOpen() {

    setOpen(true);

}
```

This improves readability and debugging.

---

## Prevent Default Behavior Only When Needed

Use:

```jsx
event.preventDefault();
```

only when you intentionally want to stop the browser's default action.

Typical examples include:

- Form submissions
- Link navigation
- Context menus

Avoid calling it unnecessarily.

---

## Don't Mutate State Inside Events

Incorrect:

```jsx
count++;
```

Correct:

```jsx
setCount(previous =>

    previous + 1

);
```

Always update State through its updater function.

---

## Keep Business Logic Separate

Avoid mixing UI code with complex calculations.

Example:

```text
Button Click

↓

Event Handler

↓

Service Function

↓

Update State

↓

Render
```

This keeps components focused on rendering the UI.

---

# Common Mistakes

## Mistake 1

Calling the event handler during rendering.

Incorrect:

```jsx
<button

    onClick={handleDelete(id)}

>
```

The function executes immediately.

Correct:

```jsx
<button

    onClick={() => handleDelete(id)}

>
```

The function executes only after the click.

---

## Mistake 2

Using HTML event names.

Incorrect:

```html
onclick
```

Correct:

```jsx
onClick
```

React uses camelCase event names.

---

## Mistake 3

Forgetting `preventDefault()`

Forms reload the page by default.

Always prevent the default behavior when handling forms in React.

```jsx
event.preventDefault();
```

---

## Mistake 4

Trying to modify Props inside an event handler.

Incorrect:

```jsx
props.count++;
```

Instead, call a callback passed from the parent or update local State.

---

## Mistake 5

Writing very large inline event handlers.

Bad:

```jsx
<button

    onClick={() => {

        // 60 lines of code

    }}

>
```

Prefer extracting the logic into a named function.

---

# Real-World Example

Imagine an employee management system.

```
Employee List

↓

Click Employee

↓

Open Details

↓

Edit Employee

↓

Save

↓

Update UI
```

Flow inside React:

```text
User Click

↓

onClick

↓

Open Modal

↓

User Edits Form

↓

onSubmit

↓

preventDefault()

↓

Validate Data

↓

Update State

↓

Render

↓

Updated Employee List
```

Every interaction is driven by events.

---

# Quick Reference

| Task | Event |
|------|-------|
| Button Click | `onClick` |
| Input Change | `onChange` |
| Form Submit | `onSubmit` |
| Key Press | `onKeyDown` |
| Focus Input | `onFocus` |
| Blur Input | `onBlur` |
| Mouse Enter | `onMouseEnter` |
| Mouse Leave | `onMouseLeave` |

---

# Key Takeaways

✅ Events allow users to interact with React applications.

✅ Event handlers are JavaScript functions.

✅ React uses Synthetic Events for consistent behavior.

✅ Most event handlers update State.

✅ Updating State triggers React's rendering pipeline.

✅ `preventDefault()` stops the browser's default behavior.

✅ `stopPropagation()` prevents events from bubbling upward.

---

# Interview Questions

## Beginner

1. What is an event in React?

2. What is an event handler?

3. How do you attach an event handler?

4. Why does React use `onClick` instead of `onclick`?

---

## Intermediate

5. What is a Synthetic Event?

6. What does `preventDefault()` do?

7. What does `stopPropagation()` do?

8. Explain event bubbling in React.

---

## Advanced

9. Explain the complete lifecycle of a click event in React.

10. How do events interact with State updates?

11. Why does React provide a Synthetic Event system?

12. When would you use event capturing instead of bubbling?

---

# Hands-on Exercises

## Exercise 1

Create a counter.

Requirements:

- Increment
- Decrement
- Reset

Use separate event handlers for each action.

---

## Exercise 2

Build a login form.

Handle:

- Input changes
- Form submission

Prevent the default page reload.

---

## Exercise 3

Create a card containing a button.

Attach click handlers to both the card and the button.

Observe event bubbling.

Then use:

```jsx
event.stopPropagation();
```

Observe the difference.

---

## Exercise 4

Create keyboard shortcuts.

Requirements:

- Press **Enter** to submit.
- Press **Escape** to clear the form.

Use keyboard event handlers.

---

# Summary

Events are React's mechanism for responding to user interactions.

They allow components to execute JavaScript in response to browser actions such as clicks, keyboard input, and form submissions.

Most event handlers update State.

State updates trigger React's rendering pipeline, ultimately producing an updated user interface.

Understanding events completes the core interaction model of React applications.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What is a React event?
- What is a Synthetic Event?
- How do you attach an event handler?
- Why does React use camelCase event names?
- What does `preventDefault()` do?
- What does `stopPropagation()` do?
- How do events trigger UI updates?

If you can confidently answer these questions, you're ready for **Conditional Rendering**.

---

# Further Reading

- 📖 Conditional Rendering
- 📖 Rendering Lists
- 📖 Keys

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← State | ↑ React Core Concepts | 🗺 Module Home | Conditional Rendering → |

---

# Continue Your Journey

You've learned how React applications respond to user interactions using **Events**.

```text
User Interaction

↓

Event Handler

↓

State Update

↓

Rendering

↓

Updated UI
```

In the next chapter, you'll learn **Conditional Rendering**—how React decides **what** to display based on Props, State, or other conditions.

Together, **Props**, **State**, **Events**, and **Conditional Rendering** form the foundation of every interactive React application.

- ⬅ **Previous:** [08 - State](08-state.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [10 - Conditional Rendering](10-conditional-rendering.md)