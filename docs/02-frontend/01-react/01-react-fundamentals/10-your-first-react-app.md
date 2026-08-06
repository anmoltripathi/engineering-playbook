# Your First React App

> Module: React Fundamentals
>
> Reading Time: 25–30 Minutes
>
> Difficulty: 🟢 Beginner

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
> → React Fundamentals
>
> → Your First React App

---

# Overview

You've spent the previous chapters understanding what React is, why it exists, how it works, how modern React applications are structured, and how to set up a development environment.

Now it's time to bring everything together by creating and running your first React application.

Unlike many beginner tutorials, this article doesn't simply show how to display **"Hello World"**.

Instead, you'll understand the complete journey of a React application—from creating the project to seeing your first component rendered in the browser.

By the end of this article, you'll not only have a working application but also understand **how it starts, how it runs, and how React updates it during development.**

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Fundamentals |
| Topic | Your First React App |
| Level | Beginner |
| Reading Time | 25–30 Minutes |
| Hands-on Required | ✅ Yes |
| Estimated Time | 20 Minutes |
| Prerequisites | Setting Up React, Project Structure |
| Next Topic | React Fundamentals Summary |

---

# Why This Matters

Creating your first application is an important milestone.

However, understanding **what happens behind the scenes** is even more valuable.

Many tutorials teach:

```text
Create Project

↓

Write Hello World

↓

Done
```

This playbook teaches:

```text
Create Project

↓

Understand Project

↓

Run Development Server

↓

Understand Startup Process

↓

Understand Rendering

↓

Modify UI

↓

Observe React Update
```

Understanding this workflow makes learning future React concepts much easier.

---

# Learning Objectives

After completing this article, you'll be able to:

- Create a React project using Vite.
- Run a React development server.
- Understand how a React application starts.
- Explain the roles of `main.tsx` and `App.tsx`.
- Make your first change and observe Hot Module Replacement.
- Build confidence navigating a React project.

---

# Step 1 — Create a New React Project

Create a new React application using Vite.

```bash
pnpm create vite my-first-react-app
```

Select:

```text
Framework

↓

React

↓

Variant

↓

TypeScript
```

Navigate into the project.

```bash
cd my-first-react-app
```

Install the project dependencies.

```bash
pnpm install
```

---

# Step 2 — Start the Development Server

Run the development server.

```bash
pnpm dev
```

You should see output similar to:

```text
VITE vX.X.X

Local:

http://localhost:5173/
```

Open the URL in your browser.

Congratulations!

Your first React application is now running.

---

# Step 3 — What Just Happened?

Many beginners stop here.

Let's understand what actually happened.

```text
pnpm dev

↓

Vite Starts

↓

Development Server Starts

↓

Browser Opens

↓

index.html Loads

↓

main.tsx Executes

↓

<App />

↓

React Renders UI

↓

Browser Displays Application
```

Although it feels like "React started," multiple tools worked together behind the scenes.

---

# Understanding the Startup Process

Let's examine the application's startup flow.

```text
Developer

↓

Runs

pnpm dev

↓

Node.js Executes Vite

↓

Vite Starts Development Server

↓

Browser Requests

localhost:5173

↓

index.html Loads

↓

main.tsx Executes

↓

<App />

↓

React DOM

↓

Browser DOM

↓

Visible User Interface
```

This is the complete startup lifecycle for a modern React application.

---

# Step 4 — Understanding `main.tsx`

Open:

```text
src/main.tsx
```

You'll see code similar to:

```tsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

ReactDOM.createRoot(
    document.getElementById("root")!
).render(
    <App />
);
```

Don't worry about every line yet.

For now, understand the responsibilities.

`main.tsx` is responsible for:

- Starting the React application.
- Connecting React to the browser.
- Rendering the root component.

Think of it as the application's entry point.

```text
Browser

↓

main.tsx

↓

<App />

↓

React Application Starts
```

---

# Step 5 — Understanding `App.tsx`

Now open:

```text
src/App.tsx
```

This file contains your application's root component.

Initially, it displays the default Vite template.

Conceptually:

```text
App

├── Header

├── Main

└── Footer
```

Every future component you create will eventually connect somewhere beneath the `App` component.

---

# Step 6 — Make Your First Change

Replace the default Vite content with:

```tsx
function App() {
    return (
        <h1>Welcome to React!</h1>
    );
}

export default App;
```

Save the file.

Immediately, the browser updates.

Notice something important.

You didn't:

- Refresh the page.
- Restart the server.
- Rebuild the project.

React updated the interface automatically.

---

# Hot Module Replacement (HMR)

When you save a file, Vite detects the change.

```text
Developer Saves File

↓

Vite Detects Change

↓

React Re-renders

↓

Browser Updates

↓

No Page Reload
```

This feature is called **Hot Module Replacement (HMR)**.

It dramatically improves developer productivity by updating only the changed parts of the application.

---

# Frequently Asked Questions

## Why is the root component called `App`?

It doesn't have to be.

`App` is simply a convention.

You could rename it to:

- Main
- Root
- Dashboard
- Website

As long as `main.tsx` imports the correct component.

---

## Who calls `App()`?

You never call `App()` directly.

React does.

```text
main.tsx

↓

<App />

↓

React Executes App()

↓

Returns UI
```

---

## Why doesn't `main.tsx` change?

`main.tsx` starts the application only once.

Most of your development work happens inside components such as `App.tsx`.

---

## Why don't I refresh the browser?

Because Vite uses Hot Module Replacement.

Only the changed modules are updated.

---

## What is `localhost:5173`?

`localhost` refers to your own computer.

Port `5173` is the default development server port used by Vite.

The application is running locally and is not yet deployed to the internet.

---

# Complete Startup Flow

Here's the complete lifecycle of your first React application.

```text
Create Project

↓

Install Dependencies

↓

Start Development Server

↓

Browser Opens

↓

index.html

↓

main.tsx

↓

<App />

↓

React DOM

↓

Browser DOM

↓

User Sees UI

↓

Developer Makes Changes

↓

Vite Detects Changes

↓

React Re-renders

↓

Browser Updates

↓

Continue Development
```

Everything you've learned in previous chapters comes together in this workflow.

---

# Engineering Perspective

Although your first React application is small, it follows the same lifecycle as enterprise applications used by millions of users.

Whether your application contains:

- 5 components
- 500 components
- 5,000 components

the startup process remains fundamentally the same.

Understanding this lifecycle provides a strong foundation for learning more advanced React concepts.

---

# Best Practices

- Keep your first application simple.
- Focus on understanding the project structure.
- Experiment with small UI changes.
- Read the code generated by Vite.
- Don't memorize the startup code—understand its purpose.

---

# Common Mistakes

❌ Editing files inside `node_modules`.

❌ Deleting `main.tsx`.

❌ Thinking `App.tsx` is a special keyword.

❌ Restarting the development server after every code change.

❌ Memorizing code without understanding the startup flow.

---

# Summary

You have successfully created and run your first React application.

More importantly, you now understand how the application starts, how `main.tsx` and `App.tsx` work together, and how React updates the interface during development.

This knowledge forms the bridge between React Fundamentals and the Core Concepts module.

---

# Knowledge Check

1. What happens after running `pnpm dev`?
2. What is the responsibility of `main.tsx`?
3. What is the responsibility of `App.tsx`?
4. Who renders the `App` component?
5. What is Hot Module Replacement?
6. Why doesn't the browser reload after every change?
7. What is `localhost:5173`?

---

# Further Reading

- 📖 Project Structure
- 📖 How React Works

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Project Structure | ↑ React Fundamentals | 🗺 React Learning Path | React Fundamentals Summary → |

---

# Continue Your Journey

🎉 Congratulations!

You've completed your first React application and now understand how a React project starts, renders, and updates.

In the next article, you'll review everything you've learned in **React Fundamentals** before moving into **Core Concepts**, where you'll begin exploring JSX, Components, Props, State, and the building blocks of React development.

- ⬅ **Previous:** [09 - Project Structure](09-project-structure.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [11 - React Fundamentals Summary](11-summary.md)