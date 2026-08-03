### 🟢 JavaScript Core Concepts — Beginner

> **Module:** JavaScript
>
> **Topic:** Core Concepts
>
> **Level:** Beginner
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 45–60 Minutes
>
> **Expected Experience:** 0–2 Years (Also asked in experienced interviews)

---

# Overview

Welcome to the **Beginner** chapter of JavaScript Core Concepts.

This chapter builds the foundation required to understand JavaScript before moving to advanced topics such as Execution Context, Scope, Closures, Prototypes, and Asynchronous JavaScript.

Although these questions are classified as "Beginner," they are frequently asked in interviews for developers with **0–10+ years of experience**. Interviewers often begin with these fundamentals before progressing to more advanced concepts.

Mastering this chapter will help you confidently answer the most common introductory JavaScript interview questions.

---

# Topics Covered

This chapter covers the following topics:

- JavaScript Introduction
- History of JavaScript
- Why JavaScript was Created
- JavaScript Features
- JavaScript vs Java
- JavaScript vs TypeScript
- JavaScript vs ECMAScript
- ECMAScript Versions
- Language Basics
- Identifiers
- Keywords
- Reserved Keywords
- Literals
- Statements
- Expressions
- Comments
- Semicolons
- Strict Mode
- Unicode
- Escape Characters

---

# Interview Questions

<details>
<summary><strong>What is JavaScript?</strong></summary>

JavaScript is a **high-level**, **dynamically typed**, **multi-paradigm** programming language primarily used to create interactive and dynamic web applications.

It is one of the three core web technologies:

- HTML → Structure
- CSS → Styling
- JavaScript → Behavior and Interactivity

Today, JavaScript is used beyond browsers for backend development (Node.js), mobile applications (React Native), desktop applications (Electron), cloud functions, and more.

</details>

<details>
<summary><strong>Why was JavaScript created?</strong></summary>

JavaScript was created to make web pages interactive.

Before JavaScript, websites were mostly static. Every user action required communication with the server.

JavaScript enabled browsers to execute code on the client side, allowing features like:

- Form validation
- Dynamic content updates
- Image sliders
- Shopping carts
- Interactive user interfaces

without reloading the page.

</details>

<details>
<summary><strong>Who created JavaScript?</strong></summary>

JavaScript was created by **Brendan Eich** in **1995** while working at **Netscape Communications**.

Interesting facts:

- Developed in just **10 days**
- Originally named **Mocha**
- Renamed to **LiveScript**
- Finally renamed to **JavaScript**

</details>

<details>
<summary><strong>Why is it called JavaScript?</strong></summary>

JavaScript was originally called **Mocha**, then **LiveScript**.

During its release, Java was becoming extremely popular. Netscape renamed LiveScript to **JavaScript** as a marketing strategy to attract developers.

Despite the similar names, **JavaScript and Java are completely different programming languages**.

</details>

<details>
<summary><strong>Is JavaScript a programming language or a scripting language?</strong></summary>

Modern JavaScript is considered a **programming language**.

Historically, it was called a scripting language because it was mainly used to automate tasks inside web browsers.

Today, JavaScript supports:

- Variables
- Functions
- Objects
- Classes
- Modules
- Asynchronous programming
- Object-Oriented Programming
- Functional Programming

making it a full-fledged programming language.

</details>

<details>
<summary><strong>Is JavaScript compiled or interpreted?</strong></summary>

Modern JavaScript is **both**.

JavaScript engines such as **V8** use **Just-In-Time (JIT) Compilation**.

The code is:

1. Parsed
2. Compiled into bytecode
3. Optimized into machine code
4. Executed

Therefore, saying JavaScript is only interpreted is no longer accurate.

</details>

<details>
<summary><strong>Is JavaScript case-sensitive?</strong></summary>

Yes.

JavaScript treats uppercase and lowercase letters as different characters.

Example:

```javascript
let name = "John";
let Name = "David";

console.log(name); // John
console.log(Name); // David
```

Here, `name` and `Name` are two different variables.

</details>

<details>
<summary><strong>Why is JavaScript called a high-level language?</strong></summary>

JavaScript is called a **high-level language** because developers do not need to manage low-level system operations such as memory allocation or processor instructions.

The JavaScript engine automatically handles:

- Memory management
- Garbage collection
- Optimization
- Machine code generation

This allows developers to focus on solving business problems instead of hardware details.

</details>

<details>
<summary><strong>Why is JavaScript called a lightweight language?</strong></summary>

JavaScript is called lightweight because:

- It has a relatively simple syntax.
- It requires minimal setup to start coding.
- It is interpreted/JIT compiled at runtime.
- It consumes fewer system resources compared to many traditional compiled languages for typical web workloads.

"Lightweight" refers to the language's design and ease of execution, **not** that JavaScript applications are always small.

</details>

<details>
<summary><strong>Why is JavaScript dynamically typed?</strong></summary>

JavaScript is dynamically typed because the data type of a variable is determined at runtime rather than at compile time.

Example:

```javascript
let value = 10;

value = "Hello";

value = true;
```

The same variable can store different data types during execution.

</details>

<details>
<summary><strong>What are the main features of JavaScript?</strong></summary>

Some of the key features of JavaScript are:

- High-level language
- Dynamically typed
- Multi-paradigm
- Prototype-based inheritance
- First-class functions
- Event-driven programming
- Asynchronous programming
- Automatic garbage collection
- Cross-platform support
- Large ecosystem

</details>

<details>
<summary><strong>What are the advantages of JavaScript?</strong></summary>

Advantages include:

- Easy to learn
- Runs in all modern browsers
- Full-stack development using one language
- Huge community support
- Rich ecosystem of libraries and frameworks
- Excellent browser compatibility
- Fast development cycle

</details>

<details>
<summary><strong>What are the limitations of JavaScript?</strong></summary>

Some limitations are:

- Single-threaded execution model
- Dynamic typing can lead to runtime errors
- Floating-point precision issues
- Source code is visible in browsers
- Browser compatibility challenges with older environments

Many of these limitations can be mitigated using modern tools and best practices.

</details>

<details>
<summary><strong>Where can JavaScript run?</strong></summary>

JavaScript can run in many environments, including:

- Web Browsers
- Node.js
- Deno
- Bun
- React Native
- Electron
- Cloud Functions
- Browser Extensions
- IoT devices

JavaScript is no longer limited to web browsers.

</details>

<details>
<summary><strong>Can JavaScript run outside the browser?</strong></summary>

Yes.

Technologies such as **Node.js**, **Deno**, and **Bun** allow JavaScript to run outside the browser.

Common use cases include:

- REST APIs
- Web servers
- CLI tools
- Desktop applications
- Cloud functions
- Automation scripts

</details>
<details>
<summary><strong>What is the difference between JavaScript and Java?</strong></summary>

Although their names are similar, JavaScript and Java are completely different programming languages.

| JavaScript | Java |
|------------|------|
| Dynamically Typed | Statically Typed |
| Prototype-based | Class-based |
| Runs in Browser & Node.js | Runs on JVM |
| Interpreted/JIT Compiled | Compiled to Bytecode |
| Used for Web, Backend, Mobile | Used for Enterprise, Android, Backend |

The name "JavaScript" was chosen for marketing purposes and does not indicate any technical relationship with Java.

</details>

<details>
<summary><strong>What is the difference between JavaScript and TypeScript?</strong></summary>

TypeScript is a superset of JavaScript developed by Microsoft.

| JavaScript | TypeScript |
|------------|------------|
| Dynamically Typed | Statically Typed (Optional) |
| Runs directly | Compiles to JavaScript |
| No type checking | Compile-time type checking |
| Easier to start | Better for large applications |

Every valid JavaScript program is also valid TypeScript, but not every TypeScript program is valid JavaScript.

</details>

<details>
<summary><strong>What is the difference between JavaScript and ECMAScript?</strong></summary>

ECMAScript is the official specification that defines how the JavaScript language should work.

JavaScript is an implementation of that specification.

Think of it like this:

- ECMAScript → Blueprint
- JavaScript → Actual Language

Modern JavaScript engines implement the ECMAScript standard.

</details>

<details>
<summary><strong>What is ECMAScript?</strong></summary>

ECMAScript (ES) is the standardized specification for JavaScript maintained by **ECMA International**.

It defines:

- Syntax
- Language Features
- Standard Objects
- Language Behavior

Every modern JavaScript engine follows the ECMAScript specification.

</details>

<details>
<summary><strong>What is ES5?</strong></summary>

ES5 (ECMAScript 5), released in **2009**, introduced many important improvements and became the foundation for modern JavaScript.

Popular features include:

- Strict Mode (`"use strict"`)
- `JSON.parse()`
- `JSON.stringify()`
- Array methods (`map`, `filter`, `reduce`, `forEach`)
- Object methods

ES5 is still widely supported across browsers.

</details>

<details>
<summary><strong>What is ES6 (ES2015)?</strong></summary>

ES6 (ECMAScript 2015) is one of the biggest updates to JavaScript.

Major features include:

- `let` and `const`
- Arrow Functions
- Classes
- Template Literals
- Destructuring
- Default Parameters
- Rest & Spread Operators
- Promises
- Modules

ES6 significantly improved developer productivity and modernized the language.

</details>

<details>
<summary><strong>Why is ES6 important?</strong></summary>

ES6 modernized JavaScript by introducing cleaner syntax, better readability, modular programming, and powerful language features.

Most modern JavaScript frameworks such as React, Angular, and Vue heavily rely on ES6+ features.

</details>

<details>
<summary><strong>What are the latest ECMAScript versions?</strong></summary>

ECMAScript is updated every year.

Some notable releases include:

- ES2015 (ES6)
- ES2016
- ES2017
- ES2018
- ES2019
- ES2020
- ES2021
- ES2022
- ES2023
- ES2024
- ES2025 (latest published standard at the time of writing)

Each version introduces new language features and improvements while maintaining backward compatibility.

</details>

<details>
<summary><strong>What are Identifiers in JavaScript?</strong></summary>

Identifiers are the names used to identify variables, functions, classes, objects, and other entities.

Examples:

```javascript
let firstName = "John";

function calculateTotal() {}

class Employee {}
```

Rules:

- Can contain letters, digits, `_`, and `$`
- Cannot start with a digit
- Cannot use reserved keywords
- Are case-sensitive

</details>

<details>
<summary><strong>What are Keywords in JavaScript?</strong></summary>

Keywords are reserved words that have predefined meanings in the language.

Examples include:

- `if`
- `else`
- `for`
- `while`
- `return`
- `function`
- `class`
- `const`
- `let`

Keywords cannot be used as identifiers.

</details>

<details>
<summary><strong>What are Reserved Keywords?</strong></summary>

Reserved keywords are words that are reserved for current or future use by JavaScript.

Examples include:

- `enum`
- `await`
- `implements`
- `interface`
- `package`
- `private`
- `protected`
- `public`

These words should not be used as variable or function names.

</details>

<details>
<summary><strong>What are Literals in JavaScript?</strong></summary>

Literals are fixed values written directly in the source code.

Examples:

```javascript
100
"Hello"
true
null
[1, 2, 3]
{ name: "John" }
```

Each of these is a literal value.

</details>

<details>
<summary><strong>What are Statements in JavaScript?</strong></summary>

A statement is an instruction that tells JavaScript to perform an action.

Examples:

```javascript
let age = 25;

if (age >= 18) {
    console.log("Adult");
}
```

Variable declarations, loops, and conditionals are all statements.

</details>

<details>
<summary><strong>What are Expressions in JavaScript?</strong></summary>

An expression is any piece of code that produces a value.

Examples:

```javascript
5 + 10

age > 18

user.name

sum(a, b)
```

Expressions can be assigned to variables or used inside statements.

</details>

<details>
<summary><strong>What are Comments in JavaScript?</strong></summary>

Comments are ignored by the JavaScript engine and are used to document code.

Single-line comment:

```javascript
// This is a comment
```

Multi-line comment:

```javascript
/*
This is
a multi-line comment
*/
```

Comments improve code readability and maintainability.

</details>

<details>
<summary><strong>Are semicolons mandatory in JavaScript?</strong></summary>

No.

JavaScript supports **Automatic Semicolon Insertion (ASI)**, which inserts semicolons automatically in many cases.

However, relying entirely on ASI can lead to unexpected behavior.

**Best Practice:** Write semicolons consistently according to your team's coding standards.

</details>

<details>
<summary><strong>What is <code>"use strict"</code>?</strong></summary>

`"use strict"` enables Strict Mode, which enforces stricter parsing and error handling.

Benefits include:

- Prevents accidental global variables
- Disallows certain unsafe syntax
- Makes debugging easier
- Encourages better coding practices

Example:

```javascript
"use strict";

x = 10; // Error
```

</details>

<details>
<summary><strong>What is Unicode in JavaScript?</strong></summary>

Unicode is a universal character encoding standard that allows JavaScript to represent text from almost every language.

Example:

```javascript
const greeting = "नमस्ते";
const emoji = "🚀";
```

JavaScript strings are Unicode-based, allowing multilingual text and emojis.

</details>

<details>
<summary><strong>What are Escape Characters?</strong></summary>

Escape characters are special sequences used inside strings.

Common examples:

| Escape | Meaning |
|--------|---------|
| `\n` | New Line |
| `\t` | Tab |
| `\\` | Backslash |
| `\"` | Double Quote |
| `\'` | Single Quote |

Example:

```javascript
console.log("Hello\nWorld");
```

Output:

```
Hello
World
```

</details>

<details>
<summary><strong>What is the difference between Source Code and Machine Code?</strong></summary>

**Source Code** is the human-readable code written by developers.

**Machine Code** is the binary instructions (`0s` and `1s`) executed directly by the CPU.

The JavaScript engine converts source code into executable machine code using parsing and Just-In-Time (JIT) compilation.

</details>

---

## Navigation

⬅️ Previous: [README](./README.md)

➡️ Next: [02. Intermediate](./02-intermediate.md)