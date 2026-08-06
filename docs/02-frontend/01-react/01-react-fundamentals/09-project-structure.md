# Project Structure

> Module: React Fundamentals
>
> Reading Time: 20–25 Minutes
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
> → Project Structure

---

# Overview

A React application is much more than a collection of JavaScript files.

As applications grow, organizing code becomes just as important as writing it.

A well-structured project improves readability, maintainability, scalability, and collaboration between developers.

In this article, you'll learn how a modern React project is organized, what each file and folder is responsible for, and how professional teams structure their applications.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Fundamentals |
| Topic | Project Structure |
| Level | Beginner |
| Reading Time | 20–25 Minutes |
| Hands-on Required | Yes |
| Prerequisites | Setting Up React |
| Next Topic | Your First React App |

---

# Why This Matters

Many beginners focus only on writing components.

However, poorly organized projects quickly become difficult to maintain.

A good folder structure provides:

- Better organization
- Easier navigation
- Improved collaboration
- Scalable architecture
- Cleaner codebase

As projects grow from a few files to hundreds of components, structure becomes essential.

---

# Learning Objectives

After completing this article, you'll be able to:

- Understand the default Vite project structure
- Explain the purpose of each file
- Organize React applications effectively
- Distinguish between configuration files and application code
- Understand feature-based architecture at a high level

---

# Default Vite Project Structure

After creating a React application with Vite, you'll see a structure similar to this:

```text
my-react-app/

├── node_modules/
├── public/
├── src/
│
├── .gitignore
├── index.html
├── package.json
├── package-lock.json (or pnpm-lock.yaml)
├── tsconfig.json
├── vite.config.ts
└── README.md
```

Let's understand the purpose of each part.

---

# Root Folder

The root folder contains configuration files that control how the application is built and managed.

```text
my-react-app/

├── src/
├── public/
├── package.json
├── vite.config.ts
└── tsconfig.json
```

Most development happens inside the `src` folder.

Configuration files are usually modified only when necessary.

---

# src/

The `src` folder contains the application's source code.

```text
src/

├── App.tsx
├── main.tsx
├── assets/
└── index.css
```

Everything related to the application's functionality lives here.

Examples include:

- Components
- Pages
- Hooks
- Utilities
- Styles
- Services

---

# main.tsx

This is the application's entry point.

Its responsibilities include:

- Creating the React application
- Connecting React to the browser
- Rendering the root component

Conceptually:

```text
Browser

↓

main.tsx

↓

<App />

↓

React Application
```

Every React application begins here.

---

# App.tsx

`App.tsx` is the root component of your application.

Initially, it contains the default Vite example.

As you build your application, this component becomes the starting point for your UI.

```text
App

├── Header

├── Main

├── Footer
```

Every other component eventually connects to the `App` component.

---

# public/

The `public` folder stores static assets that are served directly without being processed by Vite.

Examples include:

- favicon.ico
- robots.txt
- manifest.json
- Static images

These files are copied directly into the production build.

---

# assets/

The `assets` folder is typically used for files imported into your React application.

Examples:

- Images
- Fonts
- SVG files
- Icons

Unlike the `public` folder, these assets are processed and optimized during the build.

---

# package.json

The `package.json` file is the project's manifest.

It contains:

- Project name
- Version
- Dependencies
- Scripts
- Metadata

Example scripts:

```json
{
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  }
}
```

Most React projects rely on `package.json` to define their development workflow.

---

# node_modules/

This folder contains all installed dependencies.

Examples include:

- React
- React DOM
- Vite
- TypeScript

> ⚠️ **Important**
>
> Never edit files inside `node_modules`.
>
> They are managed automatically by your package manager.

---

# Configuration Files

Modern React projects include several configuration files.

Examples:

| File | Purpose |
|------|---------|
| `vite.config.ts` | Configure Vite |
| `tsconfig.json` | Configure TypeScript |
| `.gitignore` | Ignore files in Git |
| `package.json` | Project configuration |

These files define how the project behaves during development and production.

---

# Typical Project Growth

Projects evolve over time.

A small application may begin like this:

```text
src/

├── App.tsx
├── main.tsx
└── index.css
```

As the application grows:

```text
src/

├── components/
├── pages/
├── hooks/
├── services/
├── utils/
├── assets/
├── styles/
└── App.tsx
```

Eventually, larger applications often adopt a feature-based structure.

```text
src/

├── features/
│
├── shared/
│
├── layouts/
│
├── routes/
│
├── services/
│
└── App.tsx
```

We'll explore feature-based architecture in later modules.

---

# Recommended Folder Organization

For medium and large React applications, a clean folder organization improves maintainability.

```text
src/

├── assets/
├── components/
├── features/
├── hooks/
├── layouts/
├── pages/
├── routes/
├── services/
├── styles/
├── types/
├── utils/
└── App.tsx
```

Each folder has a single responsibility.

Avoid placing unrelated files together.

---

# Engineering Perspective

Project structure is an architectural decision.

A good structure should:

- Be easy to navigate
- Support growth
- Encourage code reuse
- Reduce duplication
- Improve collaboration

There is no single "perfect" folder structure.

Instead, choose a structure that matches the size and complexity of your application.

---

# Best Practices

- Keep related files together.
- Use clear folder names.
- Separate configuration from application code.
- Avoid deeply nested folders.
- Organize by feature as applications grow.

---

# Common Mistakes

❌ Putting every component in one folder.

❌ Mixing business logic with UI components.

❌ Editing `node_modules`.

❌ Creating complex folder structures too early.

---

# Summary

A well-organized React project is easier to understand, maintain, and scale.

The default Vite structure provides a simple starting point, while larger applications often adopt feature-based architectures to support long-term growth.

Understanding the purpose of each file and folder will help you build cleaner, more maintainable React applications.

---

# Knowledge Check

1. What is the purpose of the `src` folder?
2. What does `main.tsx` do?
3. Why shouldn't you edit `node_modules`?
4. What is stored in the `public` folder?
5. When should you adopt a feature-based structure?

---

# Further Reading

- 📖 Setting Up React
- 📖 Your First React App

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← Setting Up React | ↑ React Fundamentals | 🗺 React Learning Path | Your First React App → |

---

# Continue Your Journey

You now understand how a React project is organized.

Next, you'll build your **first React application**, learn how the project starts, and explore the default Vite template before customizing it.

- ⬅ **Previous:** [08 - Setting Up React](08-setting-up-react.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [10 - Your First React App](10-your-first-react-app.md)