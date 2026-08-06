# Conditional Rendering

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
> → Conditional Rendering

---

# Overview

Until now, every React component you've built has rendered the same UI every time it executed.

For example:

```jsx
function Welcome() {

    return <h1>Welcome</h1>;

}
```

No matter what happens,

the output is always:

```
Welcome
```

However, real applications rarely work this way.

Imagine a login page.

If the user is **not authenticated**, show:

```
Login
```

After the user signs in, show:

```
Dashboard
```

The same component now needs to render different user interfaces depending on the application's current state.

This concept is called **Conditional Rendering**.

Conditional Rendering allows React components to decide **what to render** based on conditions such as:

- State
- Props
- User permissions
- API responses
- Feature flags
- Device type

Without Conditional Rendering, React applications couldn't adapt to changing situations.

---

# How It Connects

```text
Props

↓

State

↓

Events

↓

Condition

↓

Conditional Rendering

↓

Updated UI
```

Events update State.

State changes the condition.

The condition determines which UI React renders.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Core Concepts |
| Topic | Conditional Rendering |
| Level | Beginner → Intermediate |
| Reading Time | 60–75 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Practice | 90 Minutes |
| Prerequisites | Props, State, Events |
| Next Topic | Rendering Lists |

---

# Why This Matters

Almost every React application relies on Conditional Rendering.

Examples include:

- Authentication
- Loading screens
- Error messages
- Empty states
- Permissions
- Notifications
- Responsive layouts
- Feature toggles

Without Conditional Rendering,

applications couldn't respond intelligently to changing data.

---

# Learning Objectives

After completing this chapter, you'll be able to:

- Explain Conditional Rendering.
- Render UI using `if`.
- Use the ternary operator.
- Use logical AND (`&&`).
- Return `null`.
- Render loading and error states.
- Build dynamic interfaces using conditions.

---

# The Problem Conditional Rendering Solves

Imagine building an online store.

Initially:

```
Cart

↓

No Products
```

The page should display:

```
Your cart is empty.
```

Later:

```
Cart

↓

3 Products
```

Now the page should display:

```
Product List

Checkout Button
```

The component must decide which UI to render.

This is exactly what Conditional Rendering solves.

---

# What is Conditional Rendering?

Conditional Rendering means rendering different user interfaces depending on a condition.

Conceptually:

```text
Condition

↓

True ?

↓

UI A

↓

False ?

↓

UI B
```

React evaluates the condition during rendering and returns the appropriate JSX.

---

# Rendering Depends on State

Suppose a user logs in.

Initially:

```text
isLoggedIn = false
```

Render:

```
Login Page
```

Later:

```text
isLoggedIn = true
```

Render:

```
Dashboard
```

The component itself didn't change.

Only its State changed.

React simply rendered a different UI.

---

# Using if Statements

The most straightforward approach is using an `if` statement.

Example:

```jsx
function Welcome({

    isLoggedIn

}) {

    if (isLoggedIn) {

        return <Dashboard />;

    }

    return <Login />;

}
```

Flow:

```text
isLoggedIn

↓

if

↓

Dashboard

or

Login
```

---

# Using the Ternary Operator

For smaller conditions,

the ternary operator is often more concise.

Example:

```jsx
return (

    isLoggedIn

        ? <Dashboard />

        : <Login />

);
```

Conceptually:

```text
Condition

↓

?

↓

True UI

:

False UI
```

This is one of the most commonly used conditional rendering patterns in React.

---

# Rendering with Logical AND (&&)

Sometimes you only want to render something when a condition is true.

Example:

```jsx
{

    isAdmin &&

    <AdminPanel />

}
```

If:

```text
isAdmin = true
```

Render:

```
Admin Panel
```

If:

```text
isAdmin = false
```

Render:

```
Nothing
```

This pattern is ideal for optional UI.

---

# Returning null

A React component can render nothing.

Example:

```jsx
function Banner({

    show

}) {

    if (!show) {

        return null;

    }

    return <PromotionBanner />;

}
```

Returning `null` tells React:

```
Don't render anything.
```

The component still executes,

but no DOM elements are produced.

---

# Choosing a Rendering Strategy

Different situations call for different approaches.

| Situation | Recommended Approach |
|------------|----------------------|
| Two completely different UIs | `if` statement |
| Small inline choice | Ternary operator |
| Optional UI | `&&` |
| Render nothing | `return null` |

Understanding these patterns helps keep components clean and readable.

---

> 🏗️ Engineering Note
>
> Conditional Rendering doesn't modify the existing UI.
>
> Instead, React calculates a new UI tree during rendering.
>
> That new tree is compared with the previous one through **Reconciliation**, and only the necessary Browser DOM updates are applied.


# Loading States

One of the most common uses of Conditional Rendering is displaying a loading indicator while data is being fetched.

Imagine opening an employee dashboard.

Immediately after opening the page:

```text
Employees

↓

Loading...
```

A few seconds later:

```text
Employees Loaded

↓

Employee Table
```

The UI changes depending on the application's current state.

---

## Example

```jsx
function EmployeeList() {

    const [

        loading,

        setLoading

    ] = useState(true);

    if (loading) {

        return <LoadingSpinner />;

    }

    return <EmployeeTable />;

}
```

Flow:

```text
loading = true

↓

Loading Spinner

--------------------

loading = false

↓

Employee Table
```

Loading states improve the user experience by providing immediate feedback.

---

# Error States

Applications don't always succeed.

APIs can fail.

Networks can disconnect.

Servers can return errors.

Instead of displaying a broken interface,

React can render an error message.

Example:

```jsx
function Dashboard({

    error

}) {

    if (error) {

        return <ErrorMessage />;

    }

    return <DashboardContent />;

}
```

Flow:

```text
Error?

↓

Yes

↓

Error UI

------------------

No

↓

Normal UI
```

---

# Empty States

Sometimes data loads successfully,

but nothing exists.

Example:

```text
Employees

↓

0 Records
```

Instead of showing an empty table,

display:

```
No employees found.
```

Example:

```jsx
if (employees.length === 0) {

    return <EmptyState />;

}
```

Flow:

```text
Employees Found?

↓

No

↓

Empty State

----------------

Yes

↓

Employee List
```

Good empty states help users understand what happened and what to do next.

---

# Combining Conditions

Real applications often evaluate multiple conditions.

Example:

```text
Loading

↓

Error

↓

Empty

↓

Data
```

React evaluates them in order.

Example:

```jsx
if (loading) {

    return <LoadingSpinner />;

}

if (error) {

    return <ErrorMessage />;

}

if (employees.length === 0) {

    return <EmptyState />;

}

return <EmployeeTable />;
```

This pattern is common in dashboards, admin panels, and data-driven applications.

---

# Rendering Priority

Order matters.

Consider:

```text
Loading

↓

Error

↓

Data
```

If loading is still true,

the application shouldn't display an error or the data.

React renders the first matching condition.

Think of conditions as checkpoints.

```text
Loading?

↓

Yes

↓

Stop

---------------------

No

↓

Error?

↓

Yes

↓

Stop

---------------------

No

↓

Render Data
```

---

# Nested Conditions

Sometimes conditions exist inside other conditions.

Example:

```jsx
if (user) {

    if (user.isAdmin) {

        return <AdminDashboard />;

    }

    return <UserDashboard />;

}

return <LoginPage />;
```

Flow:

```text
Logged In?

↓

No

↓

Login

----------------

Yes

↓

Admin?

↓

Yes

↓

Admin Dashboard

↓

No

↓

User Dashboard
```

Nested conditions are useful,

but too many levels reduce readability.

---

# Avoid Deep Nesting

Bad example:

```text
if

↓

if

↓

if

↓

if

↓

Render
```

Deep nesting becomes difficult to understand.

Instead,

split logic into smaller components.

Good:

```text
Dashboard

├── LoadingView

├── ErrorView

├── EmptyView

└── DataView
```

Each component handles one responsibility.

---

# Conditional Component Composition

React encourages composing components instead of writing large conditional blocks.

Instead of:

```jsx
if (loading) {

    ...

}

if (error) {

    ...

}

if (empty) {

    ...

}
```

Consider:

```jsx
return (

    <Page>

        <LoadingView />

        <ErrorView />

        <ContentView />

    </Page>

);
```

Each component decides whether it should render.

This produces cleaner, more maintainable code.

---

# Real-World Example

Imagine an employee management dashboard.

Possible application states:

```text
Application

↓

Loading

↓

Error

↓

No Employees

↓

Employee List
```

React evaluates them one by one.

```text
Loading?

↓

Error?

↓

Employees?

↓

Render Table
```

Every production dashboard follows a similar pattern.

---

# Authentication Example

Conditional Rendering is heavily used for authentication.

Example:

```text
User

↓

Logged In?

↓

Yes

↓

Dashboard

-------------------

No

↓

Login Page
```

Example:

```jsx
return (

    isAuthenticated

        ? <Dashboard />

        : <LoginPage />

);
```

The application automatically changes the visible UI when the authentication state changes.

---

# Feature Flags

Large applications often enable features only for certain users.

Example:

```jsx
{

    isPremium &&

    <PremiumFeatures />

}
```

Or:

```jsx
{

    isAdmin &&

    <AdminPanel />

}
```

Conditional Rendering makes it easy to enable or disable features without creating separate applications.

---

# Conditional Rendering Flow

Everything you've learned now fits together.

```text
Props

↓

State

↓

Events

↓

Condition

↓

Render

↓

React Elements

↓

Virtual DOM

↓

Reconciliation

↓

Commit

↓

Browser Paint
```

Conditional Rendering changes the React Elements returned during rendering.

React then determines the minimum Browser DOM updates required.

---

> 🏗️ Engineering Note
>
> Conditional Rendering is **not** about hiding HTML with CSS.
>
> Instead, React decides which components should exist in the Virtual DOM.
>
> Components that aren't rendered don't participate in reconciliation or produce Browser DOM nodes, making this approach cleaner and more efficient than rendering everything and hiding it afterward.

# Engineering Perspective

Conditional Rendering is one of the core ideas behind React's declarative programming model.

In traditional JavaScript applications, developers often manually show and hide elements.

Example:

```javascript
document.getElementById("login").style.display = "none";

document.getElementById("dashboard").style.display = "block";
```

The developer tells the browser **how** to update the UI.

React takes a different approach.

Instead of manually manipulating the DOM, you describe **what the UI should look like** for the current application state.

Example:

```jsx
return isLoggedIn
    ? <Dashboard />
    : <LoginPage />;
```

React determines:

- Which components should exist.
- Which components should be removed.
- Which DOM nodes should be updated.

This declarative approach produces applications that are easier to understand, maintain, and scale.

---

# Under the Hood

Suppose the user logs in.

Current State

```text
isLoggedIn = false
```

User clicks **Login**.

```text
Click Login

↓

Event Handler

↓

setIsLoggedIn(true)

↓

Render

↓

Condition Evaluated

↓

<Dashboard />

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

Notice something important.

React never "shows" the dashboard.

Instead, it calculates a **new UI tree** and updates the Browser DOM accordingly.

---

# Best Practices

## Prefer Early Returns

Instead of deeply nested conditions:

```jsx
if (!user) {

    if (loading) {

        ...

    }

}
```

Prefer:

```jsx
if (loading) {

    return <LoadingSpinner />;

}

if (!user) {

    return <LoginPage />;

}

return <Dashboard />;
```

Early returns make components much easier to read.

---

## Keep Conditions Simple

Good:

```jsx
isLoggedIn

isAdmin

loading
```

Avoid:

```jsx
user &&
user.permissions &&
user.permissions.admin &&
!loading &&
config?.featureFlags?.dashboard
```

Extract complex conditions into descriptive variables.

Example:

```jsx
const canViewDashboard =
    isLoggedIn &&
    isAdmin &&
    !loading;
```

Then:

```jsx
return canViewDashboard
    ? <Dashboard />
    : <AccessDenied />;
```

---

## Split Large Components

If a component contains dozens of conditional branches,

consider splitting it into smaller components.

Example:

```text
Dashboard

├── LoadingState

├── ErrorState

├── EmptyState

└── ContentState
```

Smaller components are easier to test and maintain.

---

## Render Components, Not HTML Fragments

Instead of:

```jsx
if (loading) {

    return (

        <div>

            <div>

                Loading...

            </div>

        </div>

    );

}
```

Prefer:

```jsx
if (loading) {

    return <LoadingSpinner />;

}
```

Reusable components improve consistency across the application.

---

## Keep Business Logic Outside JSX

Avoid writing large expressions directly inside JSX.

Instead of:

```jsx
return (

    user &&
    user.role === "admin" &&
    permissions.includes("dashboard") &&
    !loading

        ? <Dashboard />

        : <Login />

);
```

Compute the condition first.

```jsx
const canAccessDashboard =

    user &&
    user.role === "admin" &&
    permissions.includes("dashboard") &&
    !loading;
```

Then:

```jsx
return canAccessDashboard

    ? <Dashboard />

    : <Login />;
```

---

# Common Mistakes

## Mistake 1

Using nested ternary operators.

Bad:

```jsx
loading

?

<Loading />

:

error

?

<Error />

:

<Data />
```

Prefer:

```jsx
if (loading) {

    return <Loading />;

}

if (error) {

    return <Error />;

}

return <Data />;
```

---

## Mistake 2

Rendering with CSS instead of React.

Bad:

```css
display: none;
```

for application state.

Prefer letting React decide whether the component should exist.

---

## Mistake 3

Writing complex conditions directly inside JSX.

Extract them into variables.

This improves readability.

---

## Mistake 4

Duplicating conditional logic.

Instead of repeating the same condition in multiple places,

calculate it once.

```jsx
const canEdit =

    user.role === "admin";
```

Use:

```jsx
canEdit && <EditButton />
```

wherever needed.

---

## Mistake 5

Returning multiple unrelated conditions from one component.

If the component becomes difficult to understand,

split it into smaller components.

---

# Real-World Example

Consider an HR Management Dashboard.

Possible application states:

```text
Application

↓

Loading

↓

Authentication

↓

Permission

↓

Employee Data

↓

Dashboard
```

React evaluates each state in order.

```text
Loading?

↓

Login Required?

↓

Permission Granted?

↓

Employees Found?

↓

Render Dashboard
```

Every enterprise application follows a similar rendering strategy.

---

# Quick Reference

| Requirement | Recommended Pattern |
|-------------|---------------------|
| Two different UIs | `if` or ternary |
| Show optional component | `&&` |
| Render nothing | `return null` |
| Loading screen | Early return |
| Error page | Early return |
| Empty state | Early return |
| Multiple conditions | Extract variables |

---

# Key Takeaways

✅ Conditional Rendering determines **what React renders**.

✅ Rendering decisions usually depend on Props or State.

✅ Use `if` for larger rendering branches.

✅ Use the ternary operator for concise choices.

✅ Use `&&` for optional UI.

✅ Return `null` when nothing should be rendered.

✅ Prefer early returns over deeply nested conditions.

---

# Interview Questions

## Beginner

1. What is Conditional Rendering?

2. Why do React applications need Conditional Rendering?

3. What is the difference between `if` and the ternary operator?

4. When would you use `&&`?

---

## Intermediate

5. Why would a component return `null`?

6. How do loading and error states use Conditional Rendering?

7. Why are early returns preferred?

8. What problems do nested conditions create?

---

## Advanced

9. Explain how Conditional Rendering interacts with Rendering and Reconciliation.

10. Why is Conditional Rendering considered declarative?

11. How would you organize conditional rendering in a large dashboard?

12. Why should business logic be separated from JSX?

---

# Hands-on Exercises

## Exercise 1

Create a Login component.

Requirements:

- Show Login page when logged out.
- Show Dashboard after login.

---

## Exercise 2

Create a Product List.

Requirements:

- Loading state
- Error state
- Empty state
- Product table

Render the correct UI for each condition.

---

## Exercise 3

Create an Admin Panel.

Requirements:

- Admin → Admin Dashboard
- Manager → Manager Dashboard
- Employee → Employee Dashboard
- Guest → Access Denied

---

## Exercise 4

Refactor a component with nested ternary operators into early returns.

Compare the readability.

---

# Summary

Conditional Rendering allows React components to render different user interfaces based on application state.

Instead of manually manipulating the DOM, React evaluates conditions during rendering and returns the appropriate React Elements.

These elements become part of the Virtual DOM, where React compares them with the previous render and applies only the necessary Browser DOM updates.

Mastering Conditional Rendering enables you to build responsive, dynamic, and user-friendly interfaces.

---

# Knowledge Check

Before moving on, verify that you can answer the following:

- What is Conditional Rendering?
- When should you use `if`, the ternary operator, or `&&`?
- Why would a component return `null`?
- How do loading, error, and empty states use Conditional Rendering?
- Why are early returns considered a best practice?
- How does Conditional Rendering interact with React's rendering pipeline?

If you can confidently answer these questions, you're ready for **Rendering Lists**.

---

# Further Reading

- 📖 Rendering Lists
- 📖 Keys
- 📖 Component Composition

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Events | ↑ React Core Concepts | 🗺 Module Home | Rendering Lists → |

---

# Continue Your Journey

You've learned how React decides **what** to render based on Props, State, and application conditions.

```text
Props / State

↓

Condition

↓

Render

↓

Virtual DOM

↓

Reconciliation

↓

Updated UI
```

In the next chapter, you'll learn **Rendering Lists**—how React efficiently renders collections of data such as employees, products, notifications, and messages.

Together, Conditional Rendering and Rendering Lists allow you to build the majority of real-world application interfaces.

- ⬅ **Previous:** [09 - Events](09-events.md)
- ⬆ **Module Home:** [README.md](README.md)
- ➡ **Next:** [11 - Rendering Lists](11-rendering-lists.md)
