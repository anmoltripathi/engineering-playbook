# 🟢 Chapter 1 — Beginner

> **Module:** JavaScript
>
> **Topic:** Execution Context
>
> **Level:** Beginner
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 45–60 Minutes
>
> **Target Audience:** Beginners, Frontend Developers, Full Stack Developers

---

## Learning Path

Frontend Engineering Playbook

└── Interview

&nbsp;&nbsp;&nbsp;&nbsp;└── JavaScript

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── Execution Context

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 🟢 Beginner

---

# Overview

Execution Context is one of the most fundamental concepts in JavaScript.

Before JavaScript executes any code, it creates an environment called an **Execution Context**. This environment stores information required to execute the code, such as variables, functions, and the value of the `this` keyword.

Every JavaScript program begins by creating a **Global Execution Context**. Whenever a function is called, JavaScript creates a new **Function Execution Context**.

Understanding Execution Context is essential because many advanced JavaScript concepts—including Hoisting, Scope, Closures, and the Call Stack—are built on top of it.

---

## 💼 Best For

- Frontend Developers
- Full Stack Developers
- JavaScript Beginners
- Technical Interview Preparation

---

# Topics Covered

| Category | Topics |
|----------|--------|
| Introduction | Execution Context, Why It Exists |
| Types | Global Execution Context, Function Execution Context, Eval Execution Context |
| Lifecycle | Creation and Destruction |
| Function Calls | Context Creation for Functions |
| Execution | How JavaScript Executes Code |

---

# Interview Questions

<details>
<summary><strong>What is an Execution Context in JavaScript?</strong></summary>

An **Execution Context** is the environment in which JavaScript code is evaluated and executed.

It contains everything the JavaScript engine needs to run the current piece of code, including:

- Variables
- Function declarations
- The value of `this`
- References to the outer scope

Every line of JavaScript code executes inside an Execution Context.

Whenever a JavaScript program starts, a **Global Execution Context** is created automatically. Each function call creates a new **Function Execution Context**.

### Visual Representation

```text
JavaScript Program
        │
        ▼
Create Global Execution Context
        │
        ▼
Execute Global Code
        │
        ▼
Function Call
        │
        ▼
Create Function Execution Context
        │
        ▼
Execute Function
```

**Interview Tip**

Execution Context is an execution environment, **not** a block of code or a memory location.

</details>

---

<details>
<summary><strong>Why does JavaScript need an Execution Context?</strong></summary>

JavaScript needs an Execution Context because it must know how to execute code correctly.

Before execution begins, JavaScript prepares an environment to:

- Allocate memory for variables.
- Store function declarations.
- Determine the value of `this`.
- Maintain scope information.
- Execute statements in the correct order.

Without an Execution Context, the JavaScript engine would have no structured way to manage code execution.

</details>

---

<details>
<summary><strong>What are the different types of Execution Context?</strong></summary>

JavaScript has three types of Execution Context:

### 1. Global Execution Context (GEC)

Created once when the JavaScript program starts.

### 2. Function Execution Context (FEC)

Created every time a function is invoked.

### 3. Eval Execution Context

Created when code is executed using `eval()`.

> **Note:** `eval()` is rarely used in modern JavaScript because it has security and performance drawbacks.

</details>

---

<details>
<summary><strong>What is the Global Execution Context?</strong></summary>

The **Global Execution Context (GEC)** is the first execution context created by the JavaScript engine.

It is created only once for each JavaScript program.

Characteristics:

- Created automatically.
- Executes global code.
- Creates the global object.
- Determines the global value of `this`.
- Remains active until the program finishes.

Example:

```javascript
const language = "JavaScript";

function greet() {
    console.log("Hello");
}

greet();
```

The variables and functions declared outside any function belong to the Global Execution Context.

</details>

---

<details>
<summary><strong>What is the Function Execution Context?</strong></summary>

A **Function Execution Context (FEC)** is created every time a function is called.

Each function call receives its own independent execution environment.

Example:

```javascript
function greet(name) {
    console.log(name);
}

greet("Anmol");

greet("John");
```

Although the same function is called twice, JavaScript creates **two separate Function Execution Contexts**.

Each execution context stores its own parameters, local variables, and execution state.

</details>

---

<details>
<summary><strong>What is the Eval Execution Context?</strong></summary>

The **Eval Execution Context** is created when JavaScript executes code using the `eval()` function.

Example:

```javascript
eval("console.log('Hello')");
```

Modern JavaScript applications rarely use `eval()` because:

- It introduces security risks.
- It reduces performance.
- It makes code harder to debug and optimize.

For these reasons, its use is generally discouraged.

</details>

<details>
<summary><strong>How is an Execution Context created?</strong></summary>

An Execution Context is created automatically by the JavaScript engine whenever it needs to execute code.

There are two common situations:

- When a JavaScript program starts, the engine creates the **Global Execution Context (GEC)**.
- Whenever a function is invoked, the engine creates a new **Function Execution Context (FEC)**.

The creation process consists of two phases:

1. **Creation Phase**
2. **Execution Phase**

These phases are explained in detail in the **Intermediate** chapter.

### Visual Representation

```text
JavaScript Starts
        │
        ▼
Create Global Execution Context
        │
        ▼
Execute Global Code
        │
        ▼
Function Call
        │
        ▼
Create Function Execution Context
```

</details>

---

<details>
<summary><strong>What happens before JavaScript executes code?</strong></summary>

Before executing any JavaScript code, the engine prepares an Execution Context.

During this preparation, JavaScript:

- Creates the Execution Context.
- Allocates memory for variables.
- Stores function declarations.
- Determines the value of `this`.
- Sets up references required for execution.

Only after this preparation does JavaScript begin executing the code line by line.

> **Note:** The detailed Creation Phase is covered in the Intermediate chapter.

</details>

---

<details>
<summary><strong>Does every function create a new Execution Context?</strong></summary>

Yes.

Every time a function is called, JavaScript creates a new Function Execution Context.

Example:

```javascript
function greet(name) {
    console.log(`Hello ${name}`);
}

greet("Alice");
greet("Bob");
```

Although the same function is called twice, JavaScript creates two separate Function Execution Contexts.

Each context maintains its own:

- Parameters
- Local variables
- Execution state
- `this` value

This ensures that one function call does not interfere with another.

</details>

---

<details>
<summary><strong>What happens after a function finishes execution?</strong></summary>

After a function completes execution:

1. Its Function Execution Context is removed from the Call Stack.
2. Control returns to the previous Execution Context.
3. Local variables inside that function become inaccessible.
4. Memory can later be reclaimed by the Garbage Collector if no references remain.

### Visual Representation

```text
Call Stack

┌──────────────┐
│ greet()      │
├──────────────┤
│ Global       │
└──────────────┘

↓

greet() finishes

↓

┌──────────────┐
│ Global       │
└──────────────┘
```

</details>

---

<details>
<summary><strong>Can multiple Execution Contexts exist at the same time?</strong></summary>

Yes.

During program execution, multiple Execution Contexts may exist simultaneously.

However, only the Execution Context at the top of the Call Stack is actively executing.

Example:

```javascript
function first() {
    second();
}

function second() {
    third();
}

function third() {
    console.log("Hello");
}

first();
```

While `third()` is executing, the execution contexts for `first()` and `second()` still exist on the Call Stack.

</details>

---

<details>
<summary><strong>Is an Execution Context created for blocks such as <code>if</code>, <code>for</code>, or <code>while</code>?</strong></summary>

No.

JavaScript does **not** create a new Execution Context for block statements such as:

- `if`
- `for`
- `while`
- `switch`

Instead, blocks create **Block Scope** when variables are declared using `let` or `const`.

Example:

```javascript
if (true) {
    let age = 25;
}
```

No new Execution Context is created.

The concept of Block Scope is covered in the **Scope** module.

</details>

---

<details>
<summary><strong>What is the difference between Global Execution Context and Function Execution Context?</strong></summary>

| Global Execution Context | Function Execution Context |
|--------------------------|----------------------------|
| Created once per program | Created every time a function is called |
| Executes global code | Executes function code |
| Exists until the program ends | Destroyed after the function finishes |
| Creates the global object | Creates local execution environment |

Every JavaScript application has exactly one Global Execution Context, but it may create many Function Execution Contexts during execution.

</details>

---

<details>
<summary><strong>Explain Execution Context with a simple example.</strong></summary>

Consider the following code:

```javascript
const language = "JavaScript";

function greet() {
    console.log("Hello");
}

greet();
```

Execution occurs as follows:

```text
Start Program
        │
        ▼
Create Global Execution Context
        │
        ▼
Store:
language
greet()
        │
        ▼
Execute Global Code
        │
        ▼
Call greet()
        │
        ▼
Create Function Execution Context
        │
        ▼
Execute greet()
        │
        ▼
Remove Function Execution Context
        │
        ▼
Continue Global Execution
```

This demonstrates how JavaScript creates and removes Execution Contexts during program execution.

</details>

---

# Chapter Summary

After completing this chapter, you should be able to:

- Explain what an Execution Context is.
- Identify the different types of Execution Context.
- Describe when JavaScript creates a new Execution Context.
- Explain the purpose of the Global Execution Context.
- Understand how functions create new execution environments.
- Answer common beginner interview questions on Execution Context.

---

# What's Next?

In the next chapter, you'll explore the internal structure of an Execution Context, including:

- Creation Phase
- Execution Phase
- Variable Environment
- Lexical Environment
- Scope Chain
- `this` Binding

These concepts explain what actually happens inside an Execution Context before and during code execution.

---

## Navigation

🏠 Home: [Execution Context](./README.md)

➡️ Next: [02. Intermediate](./02-intermediate.md)