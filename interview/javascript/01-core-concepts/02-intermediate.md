### 🟡 Intermediate

> **Module:** JavaScript
>
> **Topic:** Core Concepts
>
> **Level:** Intermediate
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 60–90 Minutes
>
> **Expected Experience:** 2–5+ Years

---

## Learning Path

Frontend Engineering Playbook

└── Interview

&nbsp;&nbsp;&nbsp;&nbsp;└── JavaScript

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── Core Concepts

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── 🟡 Intermediate

---

# Overview

This chapter explores how JavaScript works behind the scenes.

Rather than focusing on language syntax, you'll learn how JavaScript engines execute code, manage memory, perform type conversions, and optimize application performance.

These concepts are commonly discussed in technical interviews for frontend, full-stack, and JavaScript developer roles. A solid understanding of these topics will make advanced concepts such as Execution Context, Closures, Event Loop, and Async Programming much easier to understand.

---

# Topics Covered

This chapter covers the following topics:

| Category | Topics |
|----------|--------|
| JavaScript Engine | Engine, V8, SpiderMonkey, JavaScriptCore, Chakra |
| Runtime | Runtime, Browser Runtime, Node.js Runtime |
| Execution Pipeline | Parsing, AST, JIT, Bytecode, Machine Code |
| Memory | Stack, Heap, Primitive, Reference |
| Type System | typeof, instanceof, Object.is(), ==, === |
| Data Types | Number, String, Boolean, Null, Undefined, Symbol, BigInt |

---

# Interview Questions

---

<details>
<summary><strong>What is a JavaScript Engine?</strong></summary>

A JavaScript Engine is software responsible for reading, compiling, optimizing, and executing JavaScript code.

Its primary responsibilities include:

- Parsing JavaScript code
- Generating an Abstract Syntax Tree (AST)
- Compiling the code
- Optimizing execution
- Managing memory
- Executing the code

Without a JavaScript Engine, browsers and runtimes cannot execute JavaScript.

</details>

<details>
<summary><strong>Which are the most popular JavaScript Engines?</strong></summary>

The major JavaScript engines are:

| Engine | Used By |
|---------|----------|
| V8 | Google Chrome, Microsoft Edge, Node.js |
| SpiderMonkey | Mozilla Firefox |
| JavaScriptCore | Safari |
| Chakra | Legacy Microsoft Edge (deprecated) |

Each engine follows the ECMAScript specification while implementing its own optimizations.

</details>

<details>
<summary><strong>What is V8?</strong></summary>

V8 is Google's open-source JavaScript Engine.

It powers:

- Google Chrome
- Microsoft Edge (Chromium)
- Node.js
- Deno (initially used V8)
- Bun (uses JavaScriptCore, not V8)

V8 is known for its high performance due to its Just-In-Time (JIT) compilation and runtime optimizations.

</details>

<details>
<summary><strong>How does the V8 Engine work?</strong></summary>

The V8 engine processes JavaScript in several stages:

1. Parse the source code.
2. Generate an Abstract Syntax Tree (AST).
3. Convert the AST into Bytecode.
4. Execute the Bytecode using the Ignition Interpreter.
5. Frequently executed code ("hot code") is optimized into Machine Code by the TurboFan compiler.
6. If assumptions become invalid, V8 can de-optimize and fall back to Bytecode.

This combination of interpretation and optimization provides excellent performance.

</details>

<details>
<summary><strong>What is SpiderMonkey?</strong></summary>

SpiderMonkey is Mozilla Firefox's JavaScript Engine.

It was the first JavaScript engine ever created and continues to implement modern ECMAScript features while optimizing execution for Firefox.

</details>

<details>
<summary><strong>What is JavaScriptCore?</strong></summary>

JavaScriptCore (also known as Nitro) is Apple's JavaScript Engine.

It is used in:

- Safari
- WebKit-based browsers
- Bun Runtime

It focuses on fast execution and efficient memory management.

</details>

<details>
<summary><strong>What is Chakra?</strong></summary>

Chakra was Microsoft's JavaScript Engine for the legacy version of Microsoft Edge.

After Microsoft adopted Chromium, Edge switched to the V8 engine, and Chakra is no longer actively developed.

</details>

<details>
<summary><strong>What is the difference between a JavaScript Engine and a JavaScript Runtime?</strong></summary>

A JavaScript Engine executes JavaScript code.

A JavaScript Runtime provides the engine plus additional APIs required by applications.

| Engine | Runtime |
|---------|----------|
| Executes JavaScript | Complete execution environment |
| Parses and compiles code | Includes APIs, Event Loop, Call Stack, Memory, etc. |

Example:

- V8 → Engine
- Chrome → Runtime
- Node.js → Runtime

</details>

---

### Runtime

<details>
<summary><strong>What is a JavaScript Runtime?</strong></summary>

A JavaScript Runtime is the complete environment required to execute JavaScript.

It typically includes:

- JavaScript Engine
- Call Stack
- Memory Heap
- Event Loop
- Callback Queue
- Web APIs (Browser) or Node APIs (Node.js)

The runtime enables features that are not part of the JavaScript language itself, such as timers, network requests, file system access, and DOM manipulation.

</details>

<details>
<summary><strong>What is a JavaScript Runtime Environment?</strong></summary>

A JavaScript Runtime Environment refers to the combination of the JavaScript Engine and all supporting components needed to execute JavaScript applications.

Examples include:

- Browser Runtime (Chrome, Firefox, Safari)
- Node.js Runtime
- Deno Runtime
- Bun Runtime

Each runtime provides different APIs while sharing the same JavaScript language.

</details>

<details>
<summary><strong>What is the difference between Browser Runtime and Node.js Runtime?</strong></summary>

Both runtimes execute JavaScript but provide different APIs.

| Browser Runtime | Node.js Runtime |
|-----------------|-----------------|
| DOM APIs | File System APIs |
| Web APIs | OS & Process APIs |
| Window Object | Global Object |
| Used for Frontend | Used for Backend |

The JavaScript language remains the same, but the available APIs differ.

</details>

### Execution Pipeline

<details>
<summary><strong>How does JavaScript execute code?</strong></summary>

When JavaScript code is executed, it goes through several stages:

1. Source Code
2. Parsing
3. Abstract Syntax Tree (AST)
4. Compilation (JIT)
5. Bytecode Generation
6. Optimization
7. Machine Code Execution

All of this happens automatically inside the JavaScript Engine.

</details>

<details>
<summary><strong>What is Parsing?</strong></summary>

Parsing is the process of reading JavaScript source code and checking whether it follows the language syntax.

If the parser encounters invalid syntax, it throws a **SyntaxError**.

Example:

```javascript
let = 10;
```

This produces a syntax error because `let` is a reserved keyword.

</details>

<details>
<summary><strong>What is Lexical Analysis?</strong></summary>

Lexical Analysis is the first stage of parsing.

During this phase, the JavaScript engine converts the source code into small units called **Tokens**.

Example:

```javascript
let age = 25;
```

Tokens:

- let
- age
- =
- 25
- ;

These tokens are then used to build the Abstract Syntax Tree.

</details>

<details>
<summary><strong>What is an Abstract Syntax Tree (AST)?</strong></summary>

An Abstract Syntax Tree (AST) is a tree representation of JavaScript code.

Instead of reading plain text, the engine works with the AST to understand the program structure.

AST is also used by tools such as:

- Babel
- ESLint
- Prettier
- TypeScript Compiler

</details>

<details>
<summary><strong>What is Compilation?</strong></summary>

Compilation is the process of converting JavaScript into executable instructions.

Modern JavaScript engines use **Just-In-Time (JIT) Compilation**, compiling code during execution instead of before execution.

</details>

<details>
<summary><strong>What is Interpretation?</strong></summary>

Interpretation means executing code line by line without creating a permanent executable file.

Modern JavaScript engines still use interpreters as part of the execution pipeline before optimization.

</details>

<details>
<summary><strong>What is Bytecode?</strong></summary>

Bytecode is an intermediate representation generated by the JavaScript engine.

Instead of executing the original source code directly, the engine first converts it into Bytecode, which is then executed or optimized into Machine Code.

</details>

<details>
<summary><strong>What is Machine Code?</strong></summary>

Machine Code is the binary instructions that the CPU executes directly.

Modern JavaScript engines convert frequently executed JavaScript code into optimized Machine Code for better performance.

</details>

<details>
<summary><strong>What is Just-In-Time (JIT) Compilation?</strong></summary>

JIT (Just-In-Time) Compilation is a technique where JavaScript code is compiled while the program is running.

Benefits include:

- Faster execution
- Runtime optimizations
- Better overall performance

Modern engines such as V8 use JIT compilation extensively.

</details>

---

### Memory

<details>
<summary><strong>What is Stack Memory?</strong></summary>

Stack Memory stores primitive values and function execution information.

It is:

- Fast
- Automatically managed
- Used for function calls and local variables

Each function call creates a new stack frame.

</details>

<details>
<summary><strong>What is Heap Memory?</strong></summary>

Heap Memory stores objects, arrays, functions, maps, sets, and other reference types.

Characteristics:

- Dynamic size
- Slower than stack memory
- Managed automatically by the Garbage Collector

</details>

<details>
<summary><strong>What is the difference between Stack and Heap Memory?</strong></summary>

| Stack | Heap |
|--------|------|
| Stores primitive values | Stores objects |
| Faster | Slower |
| Fixed structure | Dynamic allocation |
| Function execution | Object storage |

</details>

<details>
<summary><strong>What are Primitive Data Types?</strong></summary>

JavaScript has **7 primitive data types**:

- String
- Number
- BigInt
- Boolean
- Undefined
- Null
- Symbol

Primitive values are immutable and copied by value.

</details>

<details>
<summary><strong>What are Reference Data Types?</strong></summary>

Reference types include:

- Object
- Array
- Function
- Date
- Map
- Set
- WeakMap
- WeakSet

Reference values are stored in Heap Memory.

</details>

<details>
<summary><strong>What is the difference between Primitive and Reference Types?</strong></summary>

Primitive values are copied by value.

Reference values copy the memory reference.

Example:

```javascript
let a = 10;
let b = a;

b = 20;

console.log(a); // 10
```

```javascript
const obj1 = { name: "John" };

const obj2 = obj1;

obj2.name = "David";

console.log(obj1.name); // David
```

</details>

<details>
<summary><strong>What is Copy by Value?</strong></summary>

Copy by Value creates an independent copy of the original value.

Changing one variable does not affect the other.

This behavior applies to primitive data types.

</details>

<details>
<summary><strong>What is Copy by Reference?</strong></summary>

Copy by Reference copies the memory address instead of the actual object.

Both variables point to the same object.

Changing one reference affects the other.

</details>

---

### Types

<details>
<summary><strong>What is Dynamic Typing?</strong></summary>

JavaScript is dynamically typed, meaning variable types are determined at runtime.

Example:

```javascript
let value = 100;

value = "Hello";

value = true;
```

The same variable can store different data types.

</details>

<details>
<summary><strong>What is Type Conversion?</strong></summary>

Type Conversion is the explicit conversion of one data type into another.

Examples:

```javascript
Number("100")

String(100)

Boolean(1)
```

The developer performs the conversion intentionally.

</details>

<details>
<summary><strong>What is Type Coercion?</strong></summary>

Type Coercion is JavaScript's automatic conversion of one data type into another.

Example:

```javascript
"5" + 1
// "51"

"5" - 1
// 4
```

JavaScript automatically converts values based on the operation.

</details>

<details>
<summary><strong>What is the difference between Type Conversion and Type Coercion?</strong></summary>

| Type Conversion | Type Coercion |
|-----------------|---------------|
| Explicit | Automatic |
| Done by developer | Done by JavaScript |
| Predictable | May produce unexpected results |

</details>

<details>
<summary><strong>What is <code>typeof</code>?</strong></summary>

`typeof` is an operator used to determine the data type of a value.

Example:

```javascript
typeof 10          // "number"

typeof "Hello"     // "string"

typeof true        // "boolean"
```

</details>

<details>
<summary><strong>What is <code>instanceof</code>?</strong></summary>

`instanceof` checks whether an object was created from a specific constructor.

Example:

```javascript
const arr = [];

arr instanceof Array;
// true
```

It works only with objects, not primitive values.

</details>

<details>
<summary><strong>What is <code>Object.is()</code>?</strong></summary>

`Object.is()` compares two values without the quirks of `==`.

Unlike `===`, it correctly distinguishes:

- `+0` and `-0`
- `NaN` and `NaN`

Example:

```javascript
Object.is(NaN, NaN)
// true

NaN === NaN
// false
```

</details>

<details>
<summary><strong>What is the difference between <code>==</code> and <code>===</code>?</strong></summary>

`==` compares values after type coercion.

`===` compares both value and type without coercion.

**Best Practice:** Prefer `===` in production code.

</details>

<details>
<summary><strong>What are Truthy and Falsy values?</strong></summary>

Falsy values are:

- false
- 0
- -0
- 0n
- ""
- null
- undefined
- NaN

Everything else is Truthy.

</details>

### Data Types

<details>
<summary><strong>What is the Number data type in JavaScript?</strong></summary>

The `Number` data type represents both integers and floating-point numbers.

Examples:

```javascript
let age = 25;
let price = 99.99;
let temperature = -10;
```

Special Number values include:

- `NaN`
- `Infinity`
- `-Infinity`

Unlike many programming languages, JavaScript has only one numeric type for both integers and decimal values.

</details>

<details>
<summary><strong>What is BigInt?</strong></summary>

`BigInt` is a primitive data type introduced in ES2020 that allows JavaScript to represent integers larger than the maximum safe integer supported by the `Number` type.

Example:

```javascript
const value = 9007199254740993n;
```

Use `BigInt` when working with extremely large integers such as financial calculations, cryptography, or scientific computations.

</details>

<details>
<summary><strong>When should you use BigInt?</strong></summary>

Use `BigInt` when integer values exceed JavaScript's safe integer limit:

```javascript
Number.MAX_SAFE_INTEGER
// 9007199254740991
```

Examples:

- Banking systems
- Blockchain applications
- Scientific calculations
- Large database IDs

For normal application development, the `Number` type is sufficient.

</details>

<details>
<summary><strong>What is the String data type?</strong></summary>

A String represents textual data.

Strings can be created using:

```javascript
"Hello"

'Hello'

`Hello`
```

Template literals (backticks) also support string interpolation.

Example:

```javascript
const name = "John";

console.log(`Hello ${name}`);
```

</details>

<details>
<summary><strong>What is the Boolean data type?</strong></summary>

A Boolean represents one of two values:

```javascript
true

false
```

Booleans are commonly used in:

- Conditions
- Loops
- Comparisons
- Feature flags

Example:

```javascript
const isLoggedIn = true;
```

</details>

<details>
<summary><strong>What is <code>undefined</code>?</strong></summary>

`undefined` means a variable has been declared but has not yet been assigned a value.

Example:

```javascript
let user;

console.log(user);
// undefined
```

JavaScript assigns `undefined` automatically in this situation.

</details>

<details>
<summary><strong>What is <code>null</code>?</strong></summary>

`null` represents the intentional absence of a value.

Unlike `undefined`, `null` is assigned explicitly by the developer.

Example:

```javascript
let user = null;
```

It is commonly used to indicate that an object or value currently does not exist.

</details>

<details>
<summary><strong>What is the difference between <code>null</code> and <code>undefined</code>?</strong></summary>

| null | undefined |
|------|-----------|
| Assigned intentionally | Assigned automatically |
| Represents no value | Represents value not assigned |
| Type is `"object"` (legacy behavior) | Type is `"undefined"` |

Example:

```javascript
let a;
console.log(a);
// undefined

let b = null;
console.log(b);
// null
```

</details>

<details>
<summary><strong>What is Symbol?</strong></summary>

`Symbol` is a primitive data type introduced in ES6.

Every Symbol value is unique.

Example:

```javascript
const id1 = Symbol("id");
const id2 = Symbol("id");

console.log(id1 === id2);
// false
```

Symbols are commonly used as unique object property keys.

</details>

<details>
<summary><strong>What is NaN?</strong></summary>

`NaN` stands for **Not a Number**.

It represents an invalid numeric result.

Example:

```javascript
Number("Hello");
// NaN
```

Although it means "Not a Number", its type is still:

```javascript
typeof NaN
// "number"
```

</details>

<details>
<summary><strong>Why is <code>NaN !== NaN</code>?</strong></summary>

According to the IEEE 754 floating-point standard, `NaN` is not equal to any value, including itself.

Example:

```javascript
NaN === NaN
// false

Object.is(NaN, NaN)
// true
```

Use `Number.isNaN()` or `Object.is()` when checking for `NaN`.

</details>

<details>
<summary><strong>What is Infinity?</strong></summary>

`Infinity` represents a value larger than any finite number.

Example:

```javascript
10 / 0
// Infinity

-10 / 0
// -Infinity
```

`Infinity` is a valid Number value in JavaScript.

</details>

<details>
<summary><strong>What is the difference between <code>isNaN()</code> and <code>Number.isNaN()</code>?</strong></summary>

`isNaN()` first performs type coercion before checking.

`Number.isNaN()` checks only whether the value is actually `NaN`.

Example:

```javascript
isNaN("Hello")
// true

Number.isNaN("Hello")
// false

Number.isNaN(NaN)
// true
```

`Number.isNaN()` is generally preferred because it avoids unexpected type coercion.

</details>

<details>
<summary><strong>What is <code>Number.MAX_SAFE_INTEGER</code>?</strong></summary>

It represents the largest integer that JavaScript can represent accurately using the `Number` type.

```javascript
Number.MAX_SAFE_INTEGER
// 9007199254740991
```

Numbers larger than this may lose precision, so `BigInt` should be used instead.

</details>

<details>
<summary><strong>What is the difference between Primitive and Object Wrapper types?</strong></summary>

Primitive values:

- string
- number
- boolean
- bigint
- symbol
- undefined
- null

Object wrapper types:

- String
- Number
- Boolean

Example:

```javascript
typeof "Hello"
// "string"

typeof new String("Hello")
// "object"
```

In practice, always prefer primitive values over object wrappers unless you have a specific need.

</details>

<details>
<summary><strong>Why does <code>typeof null</code> return <code>"object"</code>?</strong></summary>

This is a well-known historical bug in JavaScript.

When JavaScript was first implemented, values were represented internally using type tags. Due to an implementation mistake, `null` was assigned the same type tag as objects.

Example:

```javascript
typeof null
// "object"
```

Although this behavior is incorrect, it has been preserved for backward compatibility because changing it would break existing JavaScript code.

**Interview Tip:**

This is one of the most frequently asked JavaScript interview questions.

</details>

<details>
<summary><strong>What is the difference between <code>null</code>, <code>undefined</code>, and an undeclared variable?</strong></summary>

| null | undefined | Undeclared |
|------|-----------|------------|
| Assigned intentionally | Declared but not assigned | Variable does not exist |
| Type is `"object"` | Type is `"undefined"` | Accessing it throws `ReferenceError` |

Example:

```javascript
let a;

console.log(a);
// undefined

let b = null;

console.log(b);
// null

console.log(c);
// ReferenceError
```

</details>

<details>
<summary><strong>What is <code>Number.MIN_SAFE_INTEGER</code>?</strong></summary>

It represents the smallest integer that JavaScript can safely represent using the `Number` type.

```javascript
Number.MIN_SAFE_INTEGER
// -9007199254740991
```

Values smaller than this may lose precision.

For extremely large positive or negative integers, use `BigInt`.

</details>

---

## Navigation

⬅️ Previous: [01. Beginner](./01-beginner.md)

🏠 Home: [README](./README.md)

➡️ Next: [03. Advanced](./03-advanced.md)