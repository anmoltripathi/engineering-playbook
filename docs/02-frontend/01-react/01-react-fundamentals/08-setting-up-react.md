# Setting Up React

> Module: React Fundamentals
>
> Reading Time: 20–25 Minutes
>
> Difficulty: 🟢 Beginner

---

> **📍 Location**
>
> Frontend Engineering Playbook
>
> → Docs
>
> → Frontend
>
> → React
>
> → React Fundamentals
>
> → Setting Up React

---

# Overview

Before building React applications, developers need a modern development environment.

Unlike traditional HTML websites, React applications use modern JavaScript features, modules, bundlers, development servers, and build tools.

Fortunately, modern tooling makes setting up a React project fast, reliable, and developer-friendly.

This article explains the tools required to build React applications, why they are needed, and how to create your first React project using the recommended modern setup.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Fundamentals |
| Topic | Setting Up React |
| Level | Beginner |
| Reading Time | 20–25 Minutes |
| Hands-on Required | Yes |
| Estimated Time | 15 Minutes |
| Prerequisites | React Fundamentals |
| Next Topic | Project Structure |

---

# Why This Matters

Writing React code is only part of frontend development.

Before your application can run in the browser, several tools work together behind the scenes.

Understanding these tools helps you:

- Create projects correctly
- Debug environment issues
- Understand React project structure
- Build production-ready applications
- Follow industry best practices

Modern React development relies on tooling, and every professional React project starts with a proper setup.

---

# Learning Objectives

After completing this article, you'll be able to:

- Install the required development tools
- Understand why each tool is needed
- Create a React application using Vite
- Run a development server
- Build a production version of the application
- Understand the basic development workflow

---

# Prerequisites

Before installing React, make sure you have:

- Basic HTML knowledge
- Basic CSS knowledge
- Intermediate JavaScript
- A code editor
- Terminal or Command Prompt familiarity

If you're new to JavaScript modules or npm, don't worry—we'll introduce the necessary concepts throughout this guide.

---

# What Do You Need?

A modern React project typically requires the following tools.

```text
Computer

↓

Operating System

↓

Node.js

↓

Package Manager (npm)

↓

Code Editor

↓

Browser

↓

React Project
```

Each tool has a specific responsibility.

---

# Required Tools

## Node.js

Node.js allows JavaScript to run outside the browser.

In React development, Node.js is primarily used for:

- Installing packages
- Running development servers
- Executing build tools
- Creating production builds

Although React runs in the browser, the development workflow depends heavily on Node.js.

---

## npm

npm (Node Package Manager) is installed automatically with Node.js.

It allows developers to:

- Install libraries
- Update dependencies
- Run project scripts
- Manage package versions

Examples:

- React
- React DOM
- Vite
- TypeScript
- ESLint

All are installed using npm (or an alternative package manager).

---

## Code Editor

A modern editor improves productivity.

Popular choices include:

- Visual Studio Code
- WebStorm
- Cursor
- Windsurf

Throughout this playbook, Visual Studio Code will be used for examples.

---

## Web Browser

Modern browsers provide powerful developer tools.

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Firefox

Developer Tools will help inspect HTML, CSS, network requests, and JavaScript execution.

---

# Choosing a Package Manager

Several package managers are available.

| Package Manager | Description |
|-----------------|-------------|
| npm | Default package manager for Node.js |
| pnpm | Fast, disk-efficient, recommended for large projects |
| Yarn | Popular alternative with workspace support |
| Bun | Modern runtime and package manager |

For this playbook, we'll use **pnpm** because it offers excellent performance and efficient dependency management.

> 💡 **Note**
>
> Most concepts remain the same regardless of which package manager you choose.

---

# Why Vite?

In the past, many React projects used Create React App (CRA).

Today, the React community recommends **Vite** for most new projects.

Benefits include:

- Faster startup
- Fast Hot Module Replacement (HMR)
- Modern build pipeline
- Smaller configuration
- Excellent developer experience

Vite has become the preferred choice for many React projects.

---

# Creating Your First Project

Create a new React project using Vite.

```bash
pnpm create vite my-react-app
```

Choose:

```text
Framework

↓

React

↓

Variant

↓

TypeScript
```

Once the project is created:

```bash
cd my-react-app
```

Install dependencies:

```bash
pnpm install
```

Start the development server:

```bash
pnpm dev
```

You should see output similar to:

```text
Local: http://localhost:5173
```

Open the URL in your browser to view the application.

---

# Development Workflow

A typical React development workflow looks like this.

```text
Write Code

↓

Save File

↓

Vite Detects Change

↓

Hot Module Replacement

↓

Browser Updates

↓

Continue Development
```

This rapid feedback loop is one of the reasons modern React development feels productive.

---

# Common Project Scripts

Most Vite React projects include the following scripts.

| Command | Purpose |
|----------|---------|
| `pnpm dev` | Start development server |
| `pnpm build` | Create production build |
| `pnpm preview` | Preview production build locally |
| `pnpm lint` | Run code quality checks |

You'll use these commands frequently throughout your React journey.

---

# Engineering Perspective

Modern React development is built around tooling.

Node.js, package managers, Vite, and development servers automate many tasks that developers previously performed manually.

This allows engineers to focus on building features rather than configuring complex build systems.

Understanding the purpose of each tool makes troubleshooting and maintaining projects much easier.

---

# Best Practices

- Install the latest LTS version of Node.js.
- Use TypeScript for new projects.
- Keep dependencies updated.
- Commit `package.json` and lock files to version control.
- Learn basic terminal commands.

---

# Common Mistakes

❌ Installing outdated tutorials that use Create React App.

❌ Running commands from the wrong directory.

❌ Ignoring package manager lock files.

❌ Editing files inside `node_modules`.

---

# Summary

A professional React development environment consists of Node.js, a package manager, a code editor, a modern browser, and a build tool such as Vite.

These tools work together to provide a fast, reliable development experience and prepare applications for production deployment.

Understanding the setup process gives you the foundation needed to build and maintain modern React applications.

---

# Knowledge Check

1. Why is Node.js required for React development?
2. What is npm or pnpm responsible for?
3. Why is Vite recommended for modern React projects?
4. What does `pnpm dev` do?
5. What is Hot Module Replacement?

---

# Further Reading

- 📖 React Ecosystem
- 📖 Project Structure

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← React vs Other Frameworks | ↑ React Fundamentals | 🗺 React Learning Path | Project Structure → |

---

# Continue Your Journey

Congratulations! You now have a modern React development environment.

Next, you'll explore the **Project Structure** generated by Vite and understand how professional React applications are organized.

- ⬅ **Previous:** [07 - React vs Other Frameworks](07-react-vs-other-frameworks.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [09 - Project Structure](09-project-structure.md)