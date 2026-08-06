# SPA vs MPA

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
> → SPA vs MPA

---

# Overview

Before React, most websites followed a traditional architecture known as the **Multi-Page Application (MPA)** model.

Every navigation required the browser to request a completely new HTML page from the server.

As users began expecting faster and more interactive experiences, a new architecture emerged—the **Single-Page Application (SPA)**.

React became one of the technologies that made building SPAs practical and maintainable.

Understanding the differences between MPAs and SPAs explains why React became so popular and why modern web applications behave differently from traditional websites.

---

# At a Glance

| Property | Value |
|----------|-------|
| Module | React Fundamentals |
| Topic | SPA vs MPA |
| Level | Beginner |
| Reading Time | 20–25 Minutes |
| Hands-on Required | No |
| Code Examples | None |
| Prerequisites | How React Works |
| Next Topic | React Ecosystem |

---

# Why This Matters

Every React developer builds Single-Page Applications.

However, many beginners don't understand:

- Why SPAs were introduced
- What problems they solve
- Their advantages and limitations
- When an MPA is still the better choice

Without this understanding, it's difficult to appreciate React's role in modern frontend development.

---

# Learning Objectives

After completing this article, you'll be able to:

- Explain the difference between SPAs and MPAs.
- Understand how each architecture works.
- Compare their advantages and disadvantages.
- Choose the right architecture for different types of projects.

---

# The Evolution of Web Applications

The web has evolved significantly over the years.

```text
Static Websites

↓

Dynamic Websites

↓

Multi-Page Applications (MPA)

↓

Single-Page Applications (SPA)

↓

Modern Hybrid Applications
```

Each stage addressed new user expectations and engineering challenges.

---

# What is a Multi-Page Application (MPA)?

A Multi-Page Application loads a completely new HTML document whenever the user navigates to another page.

For example:

```text
User Opens Home

↓

Server Sends Home.html

↓

User Clicks Products

↓

Browser Requests Products.html

↓

Server Sends Products.html

↓

Entire Page Reloads

↓

User Clicks Contact

↓

Browser Requests Contact.html

↓

Server Sends Contact.html
```

Each navigation replaces the previous page entirely.

---

# Characteristics of an MPA

Multi-Page Applications typically have the following characteristics:

- Full page reload on navigation
- HTML generated on the server
- Browser requests a new document for every page
- Simple architecture
- Strong SEO by default
- Minimal JavaScript requirements

Traditional websites built with PHP, ASP.NET, JSP, or server-side frameworks commonly follow this model.

---

# Advantages of MPAs

Multi-Page Applications provide several benefits.

- Simple request-response model
- Excellent SEO
- Easy server-side rendering
- Works well with content-driven websites
- Progressive enhancement is straightforward
- Initial page load is often lightweight

MPAs remain an excellent choice for many projects.

---

# Limitations of MPAs

As applications became more interactive, several limitations emerged.

Every page navigation required:

- A network request
- Server processing
- HTML generation
- Browser reload
- JavaScript reinitialization
- CSS recalculation

For highly interactive applications, this resulted in slower and less fluid user experiences.

---

# What is a Single-Page Application (SPA)?

A Single-Page Application loads the application shell once.

After that, JavaScript updates the interface without reloading the entire page.

```text
Initial Load

↓

Download Application

↓

User Clicks Products

↓

JavaScript Updates UI

↓

No Full Reload

↓

User Clicks Cart

↓

JavaScript Updates UI

↓

No Full Reload
```

Instead of requesting a new HTML page, the application updates only the necessary parts of the interface.

---

# Characteristics of an SPA

Single-Page Applications generally provide:

- One initial HTML page
- Client-side routing
- Dynamic UI updates
- Rich interactivity
- JavaScript-driven rendering
- Smooth navigation

React, Angular, and Vue are commonly used to build SPAs.

---

# MPA vs SPA

| Feature | MPA | SPA |
|---------|-----|-----|
| Full Page Reload | ✅ | ❌ |
| Client-side Routing | ❌ | ✅ |
| Initial Load | Faster | Often Larger |
| Subsequent Navigation | Slower | Faster |
| User Experience | Traditional | App-like |
| JavaScript Dependency | Low | High |
| Offline Possibilities | Limited | Better |
| Interactivity | Moderate | High |

---

# Real-World Examples

### Multi-Page Applications

Examples include:

- News websites
- Blogs
- Government portals
- Documentation sites
- Company marketing websites

These sites primarily serve content.

---

### Single-Page Applications

Examples include:

- Gmail
- Trello
- Notion
- Slack
- Spotify Web Player
- Banking Dashboards
- CRM Systems

These applications focus on user interaction rather than simple content delivery.

---

# How React Fits In

React doesn't create the SPA architecture.

Instead, React makes building SPAs easier.

React provides:

- Component-based UI
- Declarative rendering
- Efficient updates
- Reusable components
- Predictable rendering model

Routing, data fetching, and other SPA features are provided by additional libraries within the React ecosystem.

---

# Modern Hybrid Applications

Today, many applications combine SPA and MPA techniques.

Examples include:

- Server-Side Rendering (SSR)
- Static Site Generation (SSG)
- Incremental Static Regeneration (ISR)
- Streaming
- Partial Hydration

Frameworks such as Next.js combine these techniques to achieve better performance, SEO, and user experience.

This demonstrates that modern frontend development is no longer simply SPA vs MPA—it's about choosing the right rendering strategy for each page.

---

# Engineering Perspective

Choosing between an SPA and an MPA isn't about which architecture is better.

It's about selecting the architecture that best matches the application's requirements.

Content-heavy websites often benefit from MPA or hybrid rendering.

Highly interactive applications often benefit from SPA architectures.

Experienced engineers evaluate trade-offs rather than following trends.

---

# Best Practices

- Understand the strengths of both architectures.
- Choose based on project requirements.
- Don't assume SPA is always better.
- Consider SEO, performance, and user experience together.

---

# Common Mistakes

❌ Thinking React automatically creates an SPA.

❌ Assuming MPAs are outdated.

❌ Ignoring SEO when building SPAs.

❌ Choosing architecture based on popularity rather than requirements.

---

# Summary

MPAs and SPAs solve different problems.

Traditional Multi-Page Applications provide simplicity and strong server-rendered experiences.

Single-Page Applications prioritize rich interactivity and smoother user experiences.

React excels at building SPAs, while modern frameworks increasingly combine SPA and MPA techniques to provide the best of both worlds.

---

# Knowledge Check

1. What is a Multi-Page Application?
2. What is a Single-Page Application?
3. Why were SPAs introduced?
4. What are the advantages of MPAs?
5. What are the advantages of SPAs?
6. Does React automatically create an SPA?
7. When would you choose an MPA over an SPA?

---

# Further Reading

- 📖 How React Works
- 📖 React Ecosystem

---

# Navigation

| Previous | Module | Learning Path | Next |
|----------|--------|---------------|------|
| ← How React Works | ↑ React Fundamentals | 🗺 React Learning Path | React Ecosystem → |

---

# Continue Your Journey

Now that you understand how modern web applications are architected, you're ready to explore the broader **React Ecosystem** and learn about the tools that complement React in real-world applications.

- ⬅ **Previous:** [04 - How React Works](04-how-react-works.md)
- ⬆ **Module Home:** [React Fundamentals](README.md)
- 🗺 **Learning Path:** [React Learning Path](../00-learning-path.md)
- ➡ **Next:** [07 - React vs Other Frameworks](07-react-vs-other-frameworks.md)