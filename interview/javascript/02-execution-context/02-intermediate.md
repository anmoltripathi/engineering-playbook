# 🟡 Chapter 2 — Intermediate

> **Module:** JavaScript
>
> **Topic:** Execution Context
>
> **Level:** Intermediate
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 60–90 Minutes
>
> **Target Audience:** Frontend Developers, Full Stack Developers, JavaScript Interview Preparation

---

## Learning Path

Engineering Playbook

└── Interview

&nbsp;&nbsp;&nbsp;&nbsp;└── JavaScript

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── Execution Context

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 🟡 Intermediate

---

# Overview

In the Beginner chapter, you learned what an Execution Context is and why JavaScript creates one.

This chapter explains **how an Execution Context works internally**.

You'll learn what happens before your code executes, how JavaScript allocates memory, initializes variables, stores function declarations, creates lexical environments, determines the value of `this`, and prepares the Scope Chain.

These concepts form the foundation for understanding Hoisting, Closures, Scope, the `this` keyword, and many JavaScript interview questions.

---

## 💼 Best For

- Frontend Developers
- Full Stack Developers
- JavaScript Interview Preparation
- React Developers
- Angular Developers
- Vue Developers

---

# Topics Covered

| Category | Topics |
|----------|--------|
| Execution Lifecycle | Creation Phase, Execution Phase |
| Memory | Memory Creation Phase, Variable Initialization |
| Environment | Variable Environment, Lexical Environment |
| Scope | Outer Environment Reference, Scope Chain |
| Function Behavior | Function Declaration, Function Expression |
| Runtime | `this` Binding, Variable Object |
| Modern JavaScript | Temporal Dead Zone (Introduction) |

---

# Interview Questions

<details>
<summary><strong>What are the phases of an Execution Context?</strong></summary>

Every Execution Context is created in **two phases**:

1. **Creation Phase**
2. **Execution Phase**

During the **Creation Phase**, JavaScript prepares everything required before executing the code.

During the **Execution Phase**, JavaScript executes the code line by line.

### Visual Representation

```text
Execution Context
        │
        ▼
┌────────────────────┐
│ 1. Creation Phase  │
└────────────────────┘
        │
        ▼
┌────────────────────┐
│ 2. Execution Phase │
└────────────────────┘
```

Understanding these two phases explains concepts such as Hoisting, Scope, Closures, and the `this` keyword.

</details>

---

<details>
<summary><strong>What is the Creation Phase?</strong></summary>

The **Creation Phase** is the first phase of an Execution Context.

Before executing any code, JavaScript prepares the execution environment.

During this phase, JavaScript:

- Allocates memory for variables.
- Stores function declarations.
- Determines the value of `this`.
- Creates the Lexical Environment.
- Creates the Variable Environment.
- Establishes the Outer Environment Reference.

No JavaScript statements are executed during this phase.

### Visual Representation

```text
Creation Phase

Allocate Memory
        │
        ▼
Store Functions
        │
        ▼
Determine this
        │
        ▼
Create Lexical Environment
        │
        ▼
Prepare for Execution
```

</details>

---

<details>
<summary><strong>What is the Execution Phase?</strong></summary>

The **Execution Phase** begins after the Creation Phase is complete.

During this phase, JavaScript executes the code from top to bottom.

Typical activities include:

- Assigning values to variables.
- Executing functions.
- Evaluating expressions.
- Calling other functions.
- Returning values.

Example:

```javascript
let a = 10;

console.log(a);
```

During execution:

- `a` receives the value `10`.
- `console.log()` is executed.

### Visual Representation

```text
Creation Phase
        │
        ▼
Execution Phase
        │
        ▼
Run Statements
        │
        ▼
Complete Execution
```

</details>

---

<details>
<summary><strong>What is the Memory Creation Phase?</strong></summary>

The **Memory Creation Phase** is a part of the Creation Phase.

During this step, JavaScript allocates memory for:

- Variables
- Function declarations

Example:

```javascript
var age = 25;

function greet() {}
```

Memory is prepared before any code executes.

Initially:

```text
age → undefined

greet → function
```

No assignments have occurred yet.

</details>

---

<details>
<summary><strong>How are variables initialized during the Creation Phase?</strong></summary>

JavaScript initializes variables differently depending on how they are declared.

| Declaration | Initial Value |
|-------------|---------------|
| var | undefined |
| let | Uninitialized (TDZ) |
| const | Uninitialized (TDZ) |

Example:

```javascript
var a = 10;

let b = 20;

const c = 30;
```

Before execution:

```text
a → undefined

b → <uninitialized>

c → <uninitialized>
```

Assignments happen later during the Execution Phase.

</details>

---

<details>
<summary><strong>How are function declarations stored during the Creation Phase?</strong></summary>

Function declarations are stored completely during the Creation Phase.

Example:

```javascript
function greet() {
    console.log("Hello");
}
```

Before execution starts:

```text
greet → function
```

This is why function declarations can be called before they appear in the source code.

Example:

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

This executes successfully because the function already exists in memory.

</details>

<details>
<summary><strong>How are function expressions handled during the Creation Phase?</strong></summary>

Unlike function declarations, **function expressions are not fully initialized during the Creation Phase**.

Their behavior depends on how they are declared.

Example:

```javascript
var greet = function () {
    console.log("Hello");
};
```

During the Creation Phase:

```text
greet → undefined
```

During the Execution Phase:

```text
greet → function
```

If declared using `let` or `const`, the variable remains in the **Temporal Dead Zone (TDZ)** until execution reaches its declaration.

Example:

```javascript
greet();

var greet = function () {};
```

Output:

```text
TypeError: greet is not a function
```

This happens because `greet` exists but its value is `undefined`.

</details>

---

<details>
<summary><strong>What is the Variable Environment?</strong></summary>

The **Variable Environment** is a component of an Execution Context responsible for storing variable declarations.

Historically, it managed variables declared using `var` and function declarations.

In modern JavaScript, the Variable Environment is closely related to the Lexical Environment, but they are conceptually treated as separate components in the ECMAScript specification.

### Visual Representation

```text
Execution Context

├── Variable Environment
│      ├── var variables
│      └── Function declarations
```

For interview purposes, remember that the Variable Environment is created during the **Creation Phase**.

</details>

---

<details>
<summary><strong>What is the Lexical Environment?</strong></summary>

The **Lexical Environment** is a data structure that stores:

- Local variables
- Function declarations
- References to the outer scope

It determines how JavaScript resolves variable names during execution.

Every Execution Context has its own Lexical Environment.

### Visual Representation

```text
Lexical Environment

Current Scope
        │
        ▼
Outer Environment
        │
        ▼
Global Scope
```

The Lexical Environment forms the basis of **Scope**, **Closures**, and the **Scope Chain**.

</details>

---

<details>
<summary><strong>What is the Outer Environment Reference?</strong></summary>

The **Outer Environment Reference** is a reference from the current Lexical Environment to its parent Lexical Environment.

It allows JavaScript to search for variables outside the current scope.

Example:

```javascript
const language = "JavaScript";

function greet() {
    console.log(language);
}

greet();
```

The variable `language` is not found inside `greet()`, so JavaScript follows the Outer Environment Reference to the Global Execution Context.

### Visual Representation

```text
Function Context
        │
        ▼
Outer Environment
        │
        ▼
Global Context
```

</details>

---

<details>
<summary><strong>How is the Scope Chain created?</strong></summary>

The Scope Chain is created using the **Outer Environment Reference**.

When JavaScript cannot find a variable in the current scope, it searches the parent scope.

If necessary, it continues searching until it reaches the Global Scope.

### Visual Representation

```text
Current Scope
        │
        ▼
Parent Scope
        │
        ▼
Global Scope
        │
        ▼
Not Found
```

This mechanism is called the **Scope Chain**.

A detailed explanation is provided in the **Scope** module.

</details>

---

<details>
<summary><strong>How is <code>this</code> determined inside an Execution Context?</strong></summary>

The value of `this` is determined during the **Creation Phase** of an Execution Context.

Its value depends on **how a function is called**, not where it is defined.

Examples:

Global context (Browser):

```javascript
console.log(this);
```

Regular function:

```javascript
function greet() {
    console.log(this);
}
```

Object method:

```javascript
const user = {
    name: "John",
    greet() {
        console.log(this);
    }
};
```

Arrow functions behave differently because they inherit `this` from their surrounding lexical scope.

A complete discussion is provided in the **this Keyword** module.

</details>

---

<details>
<summary><strong>Why are function declarations available before execution?</strong></summary>

Function declarations are fully stored in memory during the Creation Phase.

Example:

```javascript
greet();

function greet() {
    console.log("Hello");
}
```

This works because the function already exists in memory before execution begins.

This behavior is commonly referred to as **function hoisting**.

</details>

---

<details>
<summary><strong>What is the Variable Object?</strong></summary>

The **Variable Object (VO)** is a historical concept used to explain how JavaScript stored variables and function declarations inside an Execution Context.

In modern ECMAScript specifications, the Variable Object has been replaced by concepts such as:

- Lexical Environment
- Environment Record

However, many interview questions still mention the Variable Object because older JavaScript books and articles use this terminology.

For interview purposes, understand that the Variable Object represents the internal storage used during the Creation Phase.

</details>

---

<details>
<summary><strong>What is the Temporal Dead Zone (TDZ)?</strong></summary>

The **Temporal Dead Zone (TDZ)** is the period between entering a scope and the execution of a `let` or `const` declaration.

During this period, the variable exists but cannot be accessed.

Example:

```javascript
console.log(age);

let age = 25;
```

Output:

```text
ReferenceError: Cannot access 'age' before initialization
```

### Visual Representation

```text
Enter Scope
        │
        ▼
Temporal Dead Zone
        │
        ▼
Declaration Executed
        │
        ▼
Variable Accessible
```

The TDZ prevents accidental access to variables before they are initialized.

A dedicated chapter covers the Temporal Dead Zone in greater detail.

</details>

---

# Chapter Summary

After completing this chapter, you should be able to:

- Explain the two phases of an Execution Context.
- Describe how JavaScript allocates memory.
- Explain Variable Environment and Lexical Environment.
- Understand how the Scope Chain is established.
- Explain how `this` is determined.
- Differentiate Function Declarations and Function Expressions during context creation.
- Describe the purpose of the Variable Object.
- Understand the basics of the Temporal Dead Zone.

---

# What's Next?

The next chapter explores advanced Execution Context concepts, including:

- Call Stack
- Stack Frames
- Recursive Execution Contexts
- Memory Cleanup
- Engine Optimizations
- Async Interaction with Execution Context

---

## Navigation

⬅️ Previous: [01. Beginner](./01-beginner.md)

🏠 Home: [Execution Context](./README.md)

➡️ Next: [03. Advanced](./03-advanced.md)