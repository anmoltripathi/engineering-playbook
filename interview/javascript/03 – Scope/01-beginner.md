# 🟢 Chapter 1 — Beginner

> **Module:** JavaScript
>
> **Topic:** Scope
>
> **Level:** Beginner
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 40–60 Minutes
>
> **Target Audience:** Beginners, Frontend Developers, Full Stack Developers, JavaScript Interview Preparation

---

## Learning Path

Frontend Engineering Playbook

└── Interview

&nbsp;&nbsp;&nbsp;&nbsp;└── JavaScript

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── Scope

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 🟢 Beginner

---

# Overview

Scope defines **where variables and functions are accessible** in JavaScript.

Without Scope, every variable would exist everywhere, making applications difficult to understand, debug, and maintain.

This chapter introduces the basic concepts of Scope before moving to Lexical Scope, Scope Chain, and Closures in later chapters.

---

## 💼 Best For

- JavaScript Beginners
- Frontend Developers
- Full Stack Developers
- React Developers
- Angular Developers

---

# Topics Covered

| Category | Topics |
|----------|--------|
| Fundamentals | Scope, Variable Accessibility |
| Types | Global Scope, Function Scope, Block Scope |
| Variables | Global Variables, Local Variables |
| Basics | `var`, `let`, `const` and Scope |
| Comparison | Scope vs Execution Context |

---

# Interview Questions

<details>
<summary><strong>What is Scope in JavaScript?</strong></summary>

## 🎯 Real Interview Context

This is one of the most frequently asked JavaScript interview questions.

Most interviewers expect more than the textbook definition. They want to know **why Scope exists** and how it affects real applications.

---

## 🤔 Think Before Scrolling

Think about:

- What does Scope control?
- Does Scope store variables?
- Does Scope control execution?

---

## ✅ Answer

Scope defines **where variables and functions can be accessed** in a JavaScript program.

It acts like a set of rules that determines the visibility and lifetime of identifiers.

Scope does **not** execute code.

Instead, it controls whether code is allowed to access a particular variable or function.

---

## 🔍 Internal Working

Whenever JavaScript tries to access a variable, it checks whether that variable is available in the current Scope.

If it isn't found, JavaScript continues searching in the parent Scope until it reaches the Global Scope.

This lookup process is known as the **Scope Chain**, which you'll learn in the next chapter.

---

## 📊 Visual Representation

```text
Global Scope

│

├── Function Scope

│      │

│      └── Block Scope

│

└── Another Function Scope
```

---

## 💻 Example

```javascript
const language = "JavaScript";

function greet() {
    console.log(language);
}

greet();
```

Output:

```text
JavaScript
```

The function can access `language` because it exists in an outer Scope.

---

## ❌ Common Mistake

❌ Scope is where variables are stored.

✅ Scope defines **whether variables can be accessed**.

Variables are stored as part of the execution environment, while Scope determines visibility.

---

## 💡 Interview Follow-up

- Is Scope created at runtime?
- Can a function access variables outside its own Scope?
- Is Scope the same as Execution Context?

---

## 🔑 Key Takeaways

- Scope controls accessibility.
- Scope prevents naming conflicts.
- Scope is fundamental to Closures and variable lookup.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Why does JavaScript need Scope?</strong></summary>

## 🎯 Real Interview Context

Interviewers often ask this after "What is Scope?" to see if you understand its purpose rather than just its definition.

---

## 🤔 Think Before Scrolling

Imagine JavaScript had **no Scope**.

What problems would occur?

---

## ✅ Answer

JavaScript needs Scope to organize code and control access to variables.

Without Scope:

- Every variable would be globally accessible.
- Variables could accidentally overwrite one another.
- Functions would interfere with each other's data.
- Applications would become difficult to debug and maintain.

Scope creates clear boundaries between different parts of a program.

---

## 🔍 Internal Working

Each Scope acts like a separate workspace.

Variables declared inside one Scope are generally isolated from other unrelated Scopes.

This isolation improves readability, maintainability, and reliability.

---

## 📊 Visual Representation

```text
Without Scope

Variable A

↓

Accessible Everywhere

↓

High Risk of Conflicts

────────────────────────

With Scope

Function A

↓

Own Variables

────────────────────────

Function B

↓

Own Variables
```

---

## 💻 Example

```javascript
function first() {
    let message = "Hello";
}

function second() {
    let message = "Hi";
}
```

Both functions use the same variable name without conflict because each variable belongs to a different Scope.

---

## ❌ Common Mistake

❌ Scope exists only to improve performance.

✅ Scope primarily exists to organize code, control variable accessibility, and prevent conflicts.

---

## 💡 Interview Follow-up

- What would happen if JavaScript had only Global Scope?
- Why is Scope especially important in large applications?

---

## 🔑 Key Takeaways

- Scope isolates variables.
- Scope prevents accidental modification.
- Scope makes applications easier to maintain.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What problem does Scope solve?</strong></summary>

## 🎯 Real Interview Context

Interviewers ask this question to determine whether you understand the practical purpose of Scope rather than just its definition.

---

## 🤔 Think Before Scrolling

Think about:

- What would happen if every variable were global?
- Could two functions safely use the same variable name?

---

## ✅ Answer

Scope solves the problem of **variable accessibility and naming conflicts**.

Without Scope:

- Variables could accidentally overwrite each other.
- Functions would interfere with one another.
- Applications would become difficult to debug.
- Code would be harder to maintain.

By restricting where variables can be accessed, Scope keeps different parts of an application isolated.

---

## 🔍 Internal Working

Each Scope creates its own namespace.

Variables declared inside one Scope are generally inaccessible from unrelated Scopes.

This allows developers to reuse variable names safely in different parts of the application.

---

## 📊 Visual Representation

```text
Without Scope

name

↓

Used Everywhere

↓

Conflicts

────────────────────────

With Scope

login()

↓

name

────────────────────────

profile()

↓

name

(No Conflict)
```

---

## 💻 Example

```javascript
function login() {
    const message = "Login Successful";

    console.log(message);
}

function logout() {
    const message = "Logout Successful";

    console.log(message);
}

login();
logout();
```

Output

```text
Login Successful
Logout Successful
```

Each `message` variable exists in its own Function Scope.

---

## ❌ Common Mistake

❌ Scope exists only to hide variables.

✅ Scope isolates variables, prevents naming conflicts, and controls accessibility.

---

## 💡 Interview Follow-up

- Can two functions have variables with the same name?
- Why don't these variables conflict?

---

## 🔑 Key Takeaways

- Prevents variable collisions.
- Improves maintainability.
- Creates isolated execution boundaries.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What are the different types of Scope in JavaScript?</strong></summary>

## 🎯 Real Interview Context

This is one of the most frequently asked JavaScript interview questions.

Interviewers often follow it with questions about `var`, `let`, and `const`.

---

## 🤔 Think Before Scrolling

Can you name all the types of Scope before reading the answer?

---

## ✅ Answer

JavaScript has three primary types of Scope.

### 1. Global Scope

Variables declared outside every function and block.

---

### 2. Function Scope

Variables declared inside a function.

---

### 3. Block Scope

Variables declared inside a block (`{}`) using `let` or `const`.

---

## 📊 Visual Representation

```text
Global Scope

│

├── Function Scope

│      │

│      └── Block Scope

│

└── Function Scope
```

---

## 💻 Example

```javascript
const company = "OpenAI";

function developer() {

    const role = "Frontend";

    if (true) {

        const level = "Senior";

    }

}
```

Here:

- `company` → Global Scope
- `role` → Function Scope
- `level` → Block Scope

---

## ❌ Common Mistake

❌ JavaScript has only Global and Function Scope.

✅ Modern JavaScript also has Block Scope.

---

## 💡 Interview Follow-up

- Which keyword creates Block Scope?
- Does `var` create Block Scope?

---

## 🔑 Key Takeaways

- Global Scope
- Function Scope
- Block Scope

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is Global Scope?</strong></summary>

## 🎯 Real Interview Context

Global Scope is one of the first concepts interviewers test because many JavaScript bugs are caused by unintended global variables.

---

## 🤔 Think Before Scrolling

Where should a variable be declared if it must be accessible throughout the application?

---

## ✅ Answer

A variable declared outside all functions and blocks belongs to the **Global Scope**.

It can be accessed from anywhere within the same JavaScript environment unless shadowed by another variable.

---

## 🔍 Internal Working

The Global Scope is created when the JavaScript program starts.

Variables declared here remain available until the application or page finishes execution.

---

## 📊 Visual Representation

```text
Global Scope

│

├── Function A

├── Function B

└── Function C
```

All functions can access Global Scope variables.

---

## 💻 Example

```javascript
const language = "JavaScript";

function greet() {
    console.log(language);
}

function learn() {
    console.log(language);
}

greet();
learn();
```

Output

```text
JavaScript
JavaScript
```

---

## ❌ Common Mistake

❌ Global variables are always bad.

✅ Global variables are useful for application-wide constants and configuration but should be used carefully.

---

## 💡 Interview Follow-up

- Can a Function Scope access Global Scope?
- Can Global Scope access Function Scope?

---

## 🔑 Key Takeaways

- Created when the program starts.
- Accessible from inner scopes.
- Should be used sparingly.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is Function Scope?</strong></summary>

## 🎯 Real Interview Context

Function Scope is fundamental to JavaScript and often appears in interviews alongside Global Scope and Block Scope.

---

## 🤔 Think Before Scrolling

Can a variable declared inside a function be accessed outside that function?

---

## ✅ Answer

Variables declared inside a function belong to that function's **Function Scope**.

They are accessible only within that function and any nested functions.

Code outside the function cannot access them directly.

---

## 🔍 Internal Working

Whenever a function is called, JavaScript creates a new Function Execution Context.

The variables declared inside that function belong to its Function Scope.

When execution leaves the function, those variables are no longer directly accessible.

---

## 📊 Visual Representation

```text
Global Scope

│

└── greet()

      │

      ├── message

      └── count
```

---

## 💻 Example

```javascript
function greet() {

    const message = "Hello";

    console.log(message);

}

greet();

console.log(message);
```

Output

```text
Hello

ReferenceError
```

The second `console.log()` cannot access `message` because it is outside the function's Scope.

---

## ❌ Common Mistake

❌ Variables declared inside a function become global after the function executes.

✅ Function Scope variables remain local to that function.

---

## 💡 Interview Follow-up

- Can nested functions access Function Scope variables?
- Does every function create a new Function Scope?

---

## 🔑 Key Takeaways

- Function Scope is local to a function.
- Outside code cannot access Function Scope variables.
- Nested functions can access parent Function Scope.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is Block Scope?</strong></summary>

## 🎯 Real Interview Context

Block Scope is one of the biggest differences between ES5 and modern JavaScript (ES6+).

Interviewers frequently compare Block Scope with Function Scope and ask how `let` and `const` behave inside blocks.

---

## 🤔 Think Before Scrolling

Think about:

- What is considered a block?
- Can variables declared inside a block be accessed outside it?

---

## ✅ Answer

A **Block Scope** is created by a pair of curly braces `{}`.

Variables declared inside a block using **`let`** or **`const`** are only accessible within that block.

Once execution leaves the block, those variables are no longer accessible.

---

## 🔍 Internal Working

Blocks include:

- `if`
- `else`
- `for`
- `while`
- `switch`
- Standalone `{}` blocks

Each block creates a separate scope for variables declared with `let` and `const`.

---

## 📊 Visual Representation

```text
Global Scope

│

└── if Block

      │

      ├── let age

      └── const city
```

---

## 💻 Example

```javascript
if (true) {
    let age = 25;
    const city = "Delhi";

    console.log(age);
    console.log(city);
}

console.log(age);
```

Output

```text
25

Delhi

ReferenceError
```

---

## ❌ Common Mistake

❌ Every variable inside `{}` belongs to Block Scope.

✅ Only variables declared using `let` or `const` are block scoped.

---

## 💡 Interview Follow-up

- Does an `if` statement create Block Scope?
- Does a `for` loop create Block Scope?
- Does `var` follow Block Scope?

---

## 🔑 Key Takeaways

- Block Scope exists only inside `{}`.
- Created by `let` and `const`.
- Prevents accidental access outside the block.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Which keywords create Block Scope?</strong></summary>

## 🎯 Real Interview Context

Interviewers often ask this immediately after introducing Block Scope.

Many candidates incorrectly answer **`var`**, making this a common interview trap.

---

## 🤔 Think Before Scrolling

Which JavaScript declarations are block scoped?

---

## ✅ Answer

Only two keywords create Block Scope:

- `let`
- `const`

Variables declared with these keywords are accessible only inside the block where they are declared.

---

## 📊 Comparison

| Keyword | Block Scope |
|----------|-------------|
| `var` | ❌ No |
| `let` | ✅ Yes |
| `const` | ✅ Yes |

---

## 💻 Example

```javascript
if (true) {

    var a = 1;

    let b = 2;

    const c = 3;

}

console.log(a);

console.log(b);

console.log(c);
```

Output

```text
1

ReferenceError

ReferenceError
```

---

## ❌ Common Mistake

❌ `var` is block scoped.

✅ `var` is function scoped.

---

## 💡 Interview Follow-up

- Why wasn't Block Scope available before ES6?
- Why were `let` and `const` introduced?

---

## 🔑 Key Takeaways

- `let` → Block Scope
- `const` → Block Scope
- `var` → Function Scope

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Can <code>var</code> create Block Scope?</strong></summary>

## 🎯 Real Interview Context

This is one of the most common JavaScript interview questions.

Interviewers use it to check whether you understand the difference between `var` and `let`.

---

## 🤔 Think Before Scrolling

Predict the output before reading the answer.

---

## 💻 Example

```javascript
if (true) {

    var language = "JavaScript";

}

console.log(language);
```

---

## ✅ Output

```text
JavaScript
```

---

## ✅ Answer

No.

`var` does **not** create Block Scope.

Variables declared with `var` ignore block boundaries and remain accessible throughout the enclosing function or the global scope if declared outside a function.

---

## 🔍 Internal Working

The `if` block does not create a separate scope for `var`.

Therefore, `language` becomes available after the block finishes.

---

## 📊 Visual Representation

```text
Function Scope

│

├── if Block

│      │

│      └── var language

│

└── language Accessible Here
```

---

## ❌ Common Mistake

❌ Every `{}` creates a new scope for all variables.

✅ `var` ignores Block Scope.

---

## 💡 Interview Follow-up

- What changes if `let` replaces `var`?
- Why was `let` introduced in ES6?

---

## 🔑 Key Takeaways

- `var` is Function Scoped.
- `var` ignores Block Scope.
- Prefer `let` and `const` in modern JavaScript.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Can <code>let</code> access Global Scope?</strong></summary>

## 🎯 Real Interview Context

This question checks whether you understand how Scope lookup works.

Many developers mistakenly believe that `let` variables are isolated from Global Scope.

---

## 🤔 Think Before Scrolling

Can a variable declared with `let` access variables declared outside its block?

---

## ✅ Answer

Yes.

A variable declared using `let` can access variables from its parent scopes, including the Global Scope, provided they are accessible through the Scope Chain.

---

## 💻 Example

```javascript
const company = "OpenAI";

function developer() {

    let role = "Frontend Developer";

    console.log(company);

    console.log(role);

}

developer();
```

Output

```text
OpenAI

Frontend Developer
```

---

## 🔍 Internal Working

JavaScript first searches for `company` inside the function.

Since it is not found, JavaScript follows the Scope Chain to the Global Scope, where it finds the variable.

---

## 📊 Visual Representation

```text
Function Scope

│

└── company ❌

        │

        ▼

Global Scope

│

└── company ✅
```

---

## ❌ Common Mistake

❌ `let` variables cannot access Global Scope.

✅ `let` variables can access parent scopes through the Scope Chain.

---

## 💡 Interview Follow-up

- Can Global Scope access Function Scope?
- What happens if another `company` variable exists inside the function?

---

## 🔑 Key Takeaways

- `let` follows the Scope Chain.
- Parent Scope variables remain accessible.
- Lookup always starts from the current Scope.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is Variable Accessibility in JavaScript?</strong></summary>

## 🎯 Real Interview Context

Interviewers often ask this question after discussing Scope to determine whether you understand **how JavaScript decides whether a variable can be used**.

---

## 🤔 Think Before Scrolling

Think about:

- Why can some variables be accessed while others cannot?
- Does JavaScript search the entire program?

---

## ✅ Answer

**Variable Accessibility** refers to whether a variable can be accessed from a particular location in the program.

JavaScript determines accessibility based on **Scope**.

If a variable exists in the current Scope or any parent Scope, it is accessible.

Otherwise, JavaScript throws a `ReferenceError`.

---

## 🔍 Internal Working

When JavaScript encounters a variable:

1. Search the current Scope.
2. If not found, search the parent Scope.
3. Continue until reaching the Global Scope.
4. If still not found, throw a `ReferenceError`.

This lookup process is called the **Scope Chain**.

---

## 📊 Visual Representation

```text
Current Scope

↓

Found?
│
├── Yes → Use Variable
│
└── No
      ↓
Parent Scope
      ↓
Found?
│
├── Yes → Use Variable
│
└── No
      ↓
Global Scope
      ↓
ReferenceError
```

---

## 💻 Example

```javascript
const language = "JavaScript";

function learn() {
    console.log(language);
}

learn();
```

Output

```text
JavaScript
```

The variable is accessible because it exists in the Global Scope.

---

## ❌ Common Mistake

❌ JavaScript searches every variable in the application.

✅ JavaScript searches only along the Scope Chain.

---

## 💡 Interview Follow-up

- What happens if the variable doesn't exist anywhere?
- Which Scope is searched first?

---

## 🔑 Key Takeaways

- Accessibility depends on Scope.
- Lookup starts from the current Scope.
- JavaScript never searches unrelated Scopes.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is the difference between Scope and Execution Context?</strong></summary>

## 🎯 Real Interview Context

This is one of the most common follow-up questions in JavaScript interviews.

Many developers confuse these two concepts.

---

## 🤔 Think Before Scrolling

Can Scope execute code?

Can Execution Context control variable visibility?

---

## ✅ Answer

Although closely related, **Scope** and **Execution Context** are different concepts.

- **Scope** determines **where variables and functions can be accessed**.
- **Execution Context** is the environment in which JavaScript executes code.

Scope is about **accessibility**.

Execution Context is about **execution**.

---

## 📊 Comparison

| Scope | Execution Context |
|--------|-------------------|
| Controls variable accessibility | Controls code execution |
| Created by lexical structure | Created when code executes |
| Used for variable lookup | Stores variables, `this`, and execution state |
| Exists because of code structure | Exists while JavaScript is executing |

---

## 💻 Example

```javascript
const language = "JavaScript";

function greet() {
    console.log(language);
}

greet();
```

Here:

- **Execution Context** executes the function.
- **Scope** allows `greet()` to access `language`.

---

## ❌ Common Mistake

❌ Scope and Execution Context are the same thing.

✅ Execution Context manages execution, while Scope controls accessibility.

---

## 💡 Interview Follow-up

- Which concept creates the Scope Chain?
- Which concept contains the value of `this`?

---

## 🔑 Key Takeaways

- Scope → Accessibility
- Execution Context → Execution
- They work together but represent different concepts.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>What is the difference between Global Variables and Local Variables?</strong></summary>

## 🎯 Real Interview Context

Interviewers use this question to verify your understanding of variable lifetime and accessibility.

---

## 🤔 Think Before Scrolling

Which variable can be accessed everywhere?

Which variable exists only inside a function or block?

---

## ✅ Answer

A **Global Variable** is declared in the Global Scope and can be accessed from any inner Scope.

A **Local Variable** is declared inside a Function Scope or Block Scope and is accessible only within that Scope.

---

## 📊 Comparison

| Global Variable | Local Variable |
|-----------------|----------------|
| Declared outside functions and blocks | Declared inside functions or blocks |
| Accessible from inner scopes | Accessible only within its own scope |
| Lives for the lifetime of the application | Exists only while its scope is accessible |
| Should be used sparingly | Preferred for most application logic |

---

## 💻 Example

```javascript
const appName = "Frontend Engineering Playbook";

function showApp() {
    const version = "1.0";

    console.log(appName);
    console.log(version);
}

showApp();
```

Output

```text
Frontend Engineering Playbook
1.0
```

Outside the function:

```javascript
console.log(version);
```

Output

```text
ReferenceError
```

---

## ❌ Common Mistake

❌ Global variables should always be used.

✅ Prefer local variables unless shared application state is required.

---

## 💡 Interview Follow-up

- Why should global variables be minimized?
- When is a global constant acceptable?

---

## 🔑 Key Takeaways

- Global variables have wider accessibility.
- Local variables improve encapsulation.
- Prefer the smallest practical scope.

---

## ⭐ Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Explain Scope using a real-world example.</strong></summary>

## 🎯 Real Interview Context

Senior interviewers sometimes ask you to explain technical concepts in simple language.

This tests both your understanding and your communication skills.

---

## 🤔 Think Before Scrolling

Can you explain Scope without using JavaScript terminology?

---

## ✅ Answer

Imagine a company office.

- The **reception area** is accessible to everyone.
- Individual **department offices** are accessible only to employees of that department.
- A **manager's cabin** is accessible only to the manager and authorized staff.

Scope works in a similar way.

- **Global Scope** is like the reception area.
- **Function Scope** is like a department office.
- **Block Scope** is like a restricted meeting room.

People inside a department can access the reception area, but visitors in the reception cannot access private offices.

JavaScript follows the same principle when resolving variables.

---

## 📊 Visual Representation

```text
Office Building

Reception
(Global Scope)

│

├── HR Office
(Function Scope)

│      │

│      └── Meeting Room
(Block Scope)

│

└── Engineering Office
(Function Scope)
```

---

## 💻 JavaScript Example

```javascript
const company = "OpenAI";

function engineering() {

    const team = "Frontend";

    if (true) {

        const project = "Playbook";

        console.log(company);
        console.log(team);
        console.log(project);

    }

}

engineering();
```

---

## ❌ Common Mistake

❌ Scope is difficult because it's only a programming concept.

✅ Scope follows the same access rules we encounter in everyday life.

---

## 💡 Interview Follow-up

- Can the reception directly access the manager's cabin?
- Which JavaScript Scope does the meeting room represent?

---

## 🔑 Key Takeaways

- Scope defines accessibility.
- Inner scopes can access outer scopes.
- Outer scopes cannot access inner scopes.
- Real-world analogies help explain Scope clearly.

---

## ⭐ Difficulty

🟢 Easy

</details>

---

# Chapter Summary

After completing this chapter, you should be able to:

- Explain what Scope is and why JavaScript needs it.
- Describe the purpose of Scope in organizing and protecting variables.
- Differentiate between Global Scope, Function Scope, and Block Scope.
- Explain how `var`, `let`, and `const` behave with different types of Scope.
- Distinguish between Global Variables and Local Variables.
- Explain the difference between Scope and Execution Context.
- Understand how JavaScript determines whether a variable is accessible.
- Use real-world examples to explain Scope confidently during interviews.

---

# What's Next?

In the next chapter, you'll move beyond the basics and learn how JavaScript actually resolves variables.

You'll explore:

- Lexical Scope
- Scope Chain
- Variable Lookup Algorithm
- Parent and Child Scope
- Nested Scope
- Shadowing
- Illegal Shadowing
- Scope inside Functions, Blocks, Loops, and Arrow Functions

These concepts form the foundation for understanding Closures, Hoisting, and advanced JavaScript behavior.


---

## Navigation

🏠 Home: [Scope](./README.md)

➡️ Next: [02. Intermediate](./02-intermediate.md)