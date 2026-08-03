### 🟢 Beginner

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

### 🟡 Intermediate

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

### 🟠 Advanced

### Memory Management

<details>
<summary><strong>What is Garbage Collection in JavaScript?</strong></summary>

Garbage Collection is JavaScript's automatic memory management mechanism.

When objects are no longer reachable by the application, the JavaScript engine automatically frees the memory occupied by those objects.

Developers do not manually allocate or free memory in JavaScript like they do in languages such as C or C++.

Example:

```javascript
let user = {
    name: "John"
};

user = null;
```

Since the original object is no longer reachable, it becomes eligible for garbage collection.

</details>

<details>
<summary><strong>How does Garbage Collection work?</strong></summary>

Modern JavaScript engines periodically identify objects that are no longer reachable from the application.

The process generally follows these steps:

1. Start from root objects (Global Object, Call Stack, etc.).
2. Mark every reachable object.
3. Unmarked objects are considered unused.
4. Free the memory occupied by unused objects.

This process happens automatically without developer intervention.

</details>

<details>
<summary><strong>What is the Mark-and-Sweep Algorithm?</strong></summary>

Mark-and-Sweep is the primary Garbage Collection algorithm used by modern JavaScript engines.

It works in two phases:

### Mark Phase

Starting from root objects, every reachable object is marked as "in use."

### Sweep Phase

Any object that is not marked is considered unreachable and its memory is reclaimed.

This algorithm helps prevent most memory leaks automatically.

</details>

<details>
<summary><strong>What is a Memory Leak?</strong></summary>

A Memory Leak occurs when memory that is no longer needed cannot be released because references to it still exist.

Over time, memory leaks can increase memory usage, slow down the application, and eventually cause crashes.

Memory leaks are especially problematic in long-running applications such as Single Page Applications (SPAs).

</details>

<details>
<summary><strong>What are common causes of Memory Leaks?</strong></summary>

Common causes include:

- Accidental global variables
- Unremoved event listeners
- Uncleared `setInterval()` timers
- Detached DOM elements
- Closures retaining unnecessary references
- Large caches that are never cleared

Identifying and removing unnecessary references helps prevent memory leaks.

</details>

<details>
<summary><strong>What are Detached DOM Elements?</strong></summary>

A Detached DOM Element is a DOM node that has been removed from the document but is still referenced by JavaScript.

Example:

```javascript
const element = document.getElementById("box");

document.body.removeChild(element);
```

If `element` is still referenced elsewhere, the browser cannot free its memory.

Detached DOM elements are a common source of memory leaks.

</details>

<details>
<summary><strong>What are Circular References?</strong></summary>

Circular references occur when two or more objects reference each other.

Example:

```javascript
const person = {};
const address = {};

person.address = address;
address.person = person;
```

Modern JavaScript engines using Mark-and-Sweep can correctly collect circular references when they become unreachable.

</details>

---

### Performance

<details>
<summary><strong>What are Hidden Classes?</strong></summary>

Hidden Classes are internal optimization structures used by JavaScript engines such as V8.

When multiple objects have the same structure, the engine creates a hidden class to optimize property access.

Objects with consistent property order generally perform better.

This is an internal engine optimization and is not part of the JavaScript language specification.

</details>

<details>
<summary><strong>What is an Inline Cache?</strong></summary>

An Inline Cache is an optimization technique used by JavaScript engines to speed up repeated property access and method calls.

Instead of performing the same lookup repeatedly, the engine caches the result for faster execution.

This improves application performance significantly.

</details>

<details>
<summary><strong>What is Deoptimization?</strong></summary>

JavaScript engines optimize frequently executed code.

If the assumptions used during optimization become invalid, the engine discards the optimized code and falls back to slower execution.

This process is called Deoptimization.

Frequent deoptimizations can negatively impact performance.

</details>

<details>
<summary><strong>How can JavaScript performance be improved?</strong></summary>

Common performance techniques include:

- Reduce unnecessary DOM operations.
- Avoid memory leaks.
- Use efficient algorithms and data structures.
- Minimize object creation in loops.
- Debounce and throttle expensive events.
- Lazy load resources.
- Cache repeated computations.
- Avoid unnecessary re-renders in UI frameworks.

Performance improvements should always be based on profiling rather than assumptions.

</details>

---

### Runtime Internals

<details>
<summary><strong>What is the Call Stack?</strong></summary>

The Call Stack is a data structure that keeps track of function execution.

Whenever a function is called, it is pushed onto the stack.

When the function finishes, it is removed from the stack.

Since JavaScript has a single Call Stack, only one function executes at a time.

</details>

<details>
<summary><strong>What is the Memory Heap?</strong></summary>

The Memory Heap is the region where JavaScript stores objects, arrays, functions, and other reference values.

Memory is allocated automatically, and unused memory is reclaimed by the Garbage Collector.

</details>

<details>
<summary><strong>Why is JavaScript called Single-Threaded?</strong></summary>

JavaScript has only one Call Stack.

This means only one piece of JavaScript code executes at any given time.

Long-running operations are delegated to the runtime, allowing JavaScript to remain responsive.

</details>

<details>
<summary><strong>Can JavaScript perform multiple tasks at the same time?</strong></summary>

Yes, but not by executing multiple JavaScript functions simultaneously.

Asynchronous operations such as:

- Timers
- Network requests
- File operations

are handled by the runtime.

Once completed, their callbacks are scheduled for execution.

This creates the appearance of concurrency while JavaScript itself remains single-threaded.

</details>

<details>
<summary><strong>What is the Event Loop? (High-Level Introduction)</strong></summary>

The Event Loop is responsible for coordinating asynchronous operations.

Its job is to continuously check whether the Call Stack is empty.

If the Call Stack is empty, it moves ready callbacks from the queues to the Call Stack for execution.

The Event Loop is one of the core concepts behind JavaScript's asynchronous behavior.

> **Note:** Event Loop is covered in detail in `16-event-loop.md`.

</details>

---

### Tricky Interview Questions

<details>
<summary><strong>Why does <code>[] == false</code> return <code>true</code>?</strong></summary>

The `==` operator performs type coercion.

During comparison:

```javascript
[] == false

↓

"" == false

↓

0 == 0

↓

true
```

This is why using `===` is generally recommended.

</details>

<details>
<summary><strong>Why does <code>{} + []</code> produce unexpected results?</strong></summary>

Depending on the context, JavaScript may interpret `{}` as either:

- An object literal
- An empty block

This can lead to unexpected behavior during evaluation.

These parsing rules are part of JavaScript's grammar and are a common interview topic.

</details>

<details>
<summary><strong>Why is floating-point arithmetic sometimes inaccurate?</strong></summary>

JavaScript uses the IEEE 754 floating-point standard.

Some decimal numbers cannot be represented exactly in binary.

Example:

```javascript
0.1 + 0.2
// 0.30000000000000004
```

This is a limitation of floating-point representation, not a JavaScript bug.

</details>

<details>
<summary><strong>What are the limitations of BigInt?</strong></summary>

Some limitations include:

- Cannot be mixed directly with `Number` in arithmetic operations.
- Does not support decimal values.
- Not compatible with some built-in APIs expecting `Number`.

Example:

```javascript
10n + 5;
// TypeError
```

Both operands must be `BigInt`.

</details>

### 🔴 Senior

<details>
<summary><strong>How would you explain JavaScript to a beginner?</strong></summary>

JavaScript is a programming language that adds behavior and interactivity to applications.

Initially, it was created for web browsers, but today it is used for:

- Frontend Development
- Backend Development
- Mobile Applications
- Desktop Applications
- Serverless Computing
- IoT

It is one of the most versatile programming languages available today.

</details>

<details>
<summary><strong>Why has JavaScript become one of the most popular programming languages?</strong></summary>

JavaScript has become popular because:

- It runs in every modern browser.
- One language can be used across the entire stack.
- It has a massive ecosystem (NPM).
- Strong community support.
- Excellent frameworks and libraries.
- Continuous improvements through ECMAScript.
- Huge industry adoption.

These factors make JavaScript a practical choice for startups and enterprises alike.

</details>

<details>
<summary><strong>What are the most common mistakes developers make in JavaScript?</strong></summary>

Some common mistakes include:

- Using `==` instead of `===`
- Accidentally creating global variables
- Not understanding `this`
- Ignoring asynchronous behavior
- Mutating objects unintentionally
- Misunderstanding closures
- Forgetting to remove event listeners
- Not handling errors properly

Understanding JavaScript fundamentals helps avoid these issues.

</details>

<details>
<summary><strong>What JavaScript concepts should every senior developer master?</strong></summary>

A senior JavaScript developer should have a solid understanding of:

- Execution Context
- Scope
- Closures
- Hoisting
- `this`
- Prototypes
- Event Loop
- Promises
- Async/Await
- Modules
- Memory Management
- Performance Optimization
- Error Handling

Knowing the syntax is not enough; understanding how JavaScript works internally is essential.

</details>

<details>
<summary><strong>How do you write maintainable JavaScript code?</strong></summary>

Some best practices include:

- Use meaningful variable and function names.
- Write small, focused functions.
- Prefer `const` over `let` where possible.
- Avoid global variables.
- Follow a consistent coding style.
- Handle errors properly.
- Keep business logic separate from UI logic.
- Write reusable and testable code.

Readable code is easier to debug, review, and maintain.

</details>

<details>
<summary><strong>How do you optimize JavaScript applications?</strong></summary>

Optimization should start with measurement rather than assumptions.

Common techniques include:

- Minimize DOM manipulation.
- Reduce unnecessary re-renders.
- Avoid memory leaks.
- Lazy load resources.
- Debounce and throttle expensive events.
- Optimize loops and algorithms.
- Cache repeated computations.
- Split large bundles.

Use browser developer tools and performance profilers to identify bottlenecks before optimizing.

</details>

<details>
<summary><strong>How do you debug JavaScript applications effectively?</strong></summary>

A structured debugging approach includes:

- Reproduce the issue consistently.
- Check browser console errors.
- Use breakpoints in DevTools.
- Inspect variables and call stack.
- Verify network requests.
- Check asynchronous code execution.
- Review recent code changes.
- Use logging only when necessary.

Avoid guessing the cause of a bug—use debugging tools to gather evidence.

</details>

<details>
<summary><strong>What security practices should JavaScript developers follow?</strong></summary>

Some important practices are:

- Validate user input.
- Sanitize untrusted data.
- Prevent Cross-Site Scripting (XSS).
- Avoid using `eval()`.
- Store sensitive data securely.
- Use HTTPS.
- Keep dependencies updated.
- Follow the Principle of Least Privilege.

Security should be considered throughout the development lifecycle.

</details>

<details>
<summary><strong>How do you stay updated with modern JavaScript?</strong></summary>

A good approach is to:

- Read the ECMAScript release notes.
- Follow MDN documentation.
- Track TC39 proposals.
- Explore high-quality technical blogs.
- Build real-world projects.
- Read well-maintained open-source code.

Continuous learning is important because JavaScript evolves every year.

</details>

<details>
<summary><strong>If you were mentoring a junior developer, what JavaScript topics would you teach first?</strong></summary>

A recommended learning path is:

1. Variables and Data Types
2. Operators
3. Control Flow
4. Functions
5. Objects and Arrays
6. Scope
7. Execution Context
8. Closures
9. `this`
10. Asynchronous JavaScript
11. Modules
12. Error Handling

Building a strong foundation makes advanced concepts much easier to understand.

</details>

### ⚫ Architect

<details>
<summary><strong>Why would you choose JavaScript for a large-scale enterprise application?</strong></summary>

JavaScript is a strong choice for enterprise applications because it enables full-stack development using a single language.

Advantages include:

- Shared code between frontend and backend
- Large ecosystem (NPM)
- Strong community support
- Excellent framework support
- Rapid development
- Easy hiring due to its popularity

However, the decision should also consider team expertise, performance requirements, maintainability, and business goals.

</details>

<details>
<summary><strong>What factors would you consider before selecting JavaScript for a new project?</strong></summary>

Some important considerations include:

- Project requirements
- Team expertise
- Scalability needs
- Performance requirements
- Security requirements
- Community support
- Long-term maintainability
- Availability of libraries and tooling

Technology should always be selected based on project requirements rather than popularity.

</details>

<details>
<summary><strong>How would you maintain code quality in a large JavaScript codebase?</strong></summary>

A combination of engineering practices helps maintain quality:

- Coding standards
- ESLint
- Prettier
- Code reviews
- Unit testing
- Integration testing
- CI/CD pipelines
- Modular architecture
- Documentation

Consistency is more important than individual coding preferences.

</details>

<details>
<summary><strong>How would you improve the performance of a large JavaScript application?</strong></summary>

A structured approach includes:

- Profile before optimizing
- Reduce unnecessary rendering
- Lazy load modules
- Code splitting
- Tree shaking
- Optimize API calls
- Cache frequently used data
- Remove unused dependencies
- Monitor performance continuously

Performance optimization should always be data-driven rather than assumption-driven.

</details>

<details>
<summary><strong>How do you decide when to introduce TypeScript into a JavaScript project?</strong></summary>

TypeScript is beneficial when:

- The project is large
- Multiple developers collaborate
- Long-term maintenance is expected
- Strong type safety is required
- Better IDE support is desired

For small prototypes or short-lived projects, plain JavaScript may be sufficient.

</details>

<details>
<summary><strong>What are the biggest challenges of maintaining a large JavaScript application?</strong></summary>

Common challenges include:

- Technical debt
- Inconsistent coding styles
- Dependency management
- Performance issues
- Large bundle sizes
- Poor documentation
- Complex state management
- Legacy code

Regular refactoring and engineering standards help address these challenges.

</details>

<details>
<summary><strong>How do you evaluate a new JavaScript framework or library before adopting it?</strong></summary>

Key evaluation criteria include:

- Community adoption
- Documentation quality
- Maintenance activity
- Performance
- Learning curve
- Compatibility with existing systems
- Long-term support
- Ecosystem maturity

Avoid adopting a technology solely because it is trending.

</details>

<details>
<summary><strong>What advice would you give a developer who wants to become an expert in JavaScript?</strong></summary>

Focus on mastering the fundamentals before learning frameworks.

Recommended progression:

1. Core JavaScript
2. Execution Context
3. Scope
4. Closures
5. `this`
6. Prototypes
7. Asynchronous JavaScript
8. Browser APIs
9. Design Patterns
10. Build real-world projects
11. Read production code
12. Mentor others

Strong fundamentals remain valuable regardless of framework changes.

</details>

---

# Coding Questions

## Easy

<details>
<summary><strong>Write a program to swap two variables.</strong></summary>

Expected Topics:

- Variable assignment
- Destructuring assignment
- Temporary variable approach

</details>

<details>
<summary><strong>Check whether a value is a primitive or reference type.</strong></summary>

Expected Topics:

- `typeof`
- Primitive types
- Objects and functions

</details>

<details>
<summary><strong>Convert a string to a number using different approaches.</strong></summary>

Expected Topics:

- `Number()`
- `parseInt()`
- `parseFloat()`
- Unary `+`

</details>

<details>
<summary><strong>Demonstrate the difference between <code>==</code> and <code>===</code>.</strong></summary>

Expected Topics:

- Type coercion
- Strict equality
- Best practices

</details>

<details>
<summary><strong>Demonstrate Copy by Value vs Copy by Reference.</strong></summary>

Expected Topics:

- Primitive values
- Objects
- Arrays

</details>

---

## Medium

<details>
<summary><strong>Implement a deep clone function without using external libraries.</strong></summary>

Expected Topics:

- Objects
- Arrays
- Recursion
- Structured cloning limitations

</details>

<details>
<summary><strong>Explain the output of tricky JavaScript equality comparisons.</strong></summary>

Examples:

```javascript
[] == false

{} == {}

NaN == NaN

null == undefined
```

Expected Topics:

- Type coercion
- Reference comparison
- Special values

</details>

<details>
<summary><strong>Write examples demonstrating Truthy and Falsy values.</strong></summary>

Expected Topics:

- Boolean conversion
- Conditional statements

</details>

<details>
<summary><strong>Create your own implementation of <code>Object.is()</code>.</strong></summary>

Expected Topics:

- Equality comparison
- Edge cases
- `NaN`
- `+0` vs `-0`

</details>

---

## Hard

<details>
<summary><strong>Explain why <code>0.1 + 0.2 !== 0.3</code> and demonstrate how to handle it.</strong></summary>

Expected Topics:

- IEEE 754
- Floating-point precision
- Rounding techniques

</details>

<details>
<summary><strong>Find and fix a memory leak in the given JavaScript code.</strong></summary>

Expected Topics:

- Garbage Collection
- Detached DOM
- Event listeners
- Timers

</details>

<details>
<summary><strong>Explain the execution flow of a JavaScript program from source code to machine code.</strong></summary>

Expected Topics:

- Parser
- AST
- Bytecode
- JIT
- Machine code

</details>

# Scenario-Based Questions

<details>
<summary><strong>You join a project where developers frequently use <code>==</code> instead of <code>===</code>. How would you handle it?</strong></summary>

I would first understand why the team is using `==`.

If there is no specific requirement for type coercion, I would recommend using `===` because it provides predictable comparisons and avoids bugs caused by implicit type conversion.

I would also suggest enabling ESLint rules such as `eqeqeq` to enforce consistency.

</details>

<details>
<summary><strong>Your application is consuming more memory over time. How would you investigate the issue?</strong></summary>

I would:

1. Reproduce the issue.
2. Use Chrome DevTools Memory tab.
3. Take Heap Snapshots.
4. Compare memory usage over time.
5. Look for detached DOM elements.
6. Check event listeners.
7. Check timers (`setInterval`).
8. Review closures retaining large objects.
9. Remove unnecessary references.

</details>

<details>
<summary><strong>Your teammate says JavaScript is only a frontend language. How would you respond?</strong></summary>

I would explain that JavaScript has evolved into a full-stack programming language.

Today it is used for:

- Frontend Development
- Backend APIs (Node.js)
- Mobile Apps (React Native)
- Desktop Apps (Electron)
- Cloud Functions
- Browser Extensions
- IoT

Modern JavaScript is no longer limited to browsers.

</details>

<details>
<summary><strong>You need to build a real-time dashboard. Why would JavaScript be a good choice?</strong></summary>

JavaScript is well suited because it supports:

- Event-driven programming
- Asynchronous operations
- WebSockets
- Fast UI updates
- Large ecosystem
- Excellent frontend framework support

Combined with technologies like Node.js and React, it is an excellent choice for real-time applications.

</details>

<details>
<summary><strong>A junior developer asks why JavaScript is dynamically typed. How would you explain it?</strong></summary>

I would explain that variables in JavaScript do not have fixed data types.

Instead, values have types.

Example:

```javascript
let value = 10;

value = "Hello";

value = true;
```

The same variable stores different types during execution.

This flexibility increases developer productivity but requires careful coding to avoid runtime errors.

</details>

<details>
<summary><strong>Your team is considering migrating from JavaScript to TypeScript. What factors would you evaluate?</strong></summary>

I would evaluate:

- Project size
- Team experience
- Existing codebase
- Development timeline
- Long-term maintenance
- Type safety requirements
- Tooling support
- Third-party library compatibility

For large and long-lived applications, TypeScript often improves maintainability.

</details>

<details>
<summary><strong>During a code review, you notice excessive object mutation. What would you recommend?</strong></summary>

I would recommend reducing unnecessary mutations because they can make applications harder to debug and maintain.

Where appropriate, prefer immutable update patterns, especially in modern frontend frameworks such as React.

</details>

<details>
<summary><strong>You observe frequent performance issues in a JavaScript application. What would be your approach?</strong></summary>

Rather than optimizing blindly, I would:

- Measure performance first.
- Use browser profiling tools.
- Identify bottlenecks.
- Optimize only the slowest parts.
- Re-measure after changes.

Performance optimization should always be evidence-based.

</details>

<details>
<summary><strong>Your interviewer asks, "What is the biggest misconception about JavaScript?" How would you answer?</strong></summary>

One of the biggest misconceptions is that JavaScript is only a browser scripting language.

Modern JavaScript powers:

- Backend services
- Mobile apps
- Desktop applications
- Cloud platforms
- IoT devices

Another misconception is that JavaScript is "just interpreted." Modern engines use sophisticated JIT compilation and runtime optimizations.

</details>

<details>
<summary><strong>If you had only one week to prepare someone for a JavaScript interview, what topics would you prioritize?</strong></summary>

I would focus on:

1. Core Concepts
2. Execution Context
3. Scope
4. Hoisting
5. Closures
6. `this`
7. Objects & Prototypes
8. Event Loop
9. Promises
10. Async/Await

These topics form the foundation of most JavaScript interviews.

</details>

---

# Navigation

⬅️ **Previous:** [Learning Roadmap](./00-learning-roadmap.md)

🏠 **JavaScript Home:** [README.md](./README.md)

➡️ **Next:** [Execution Context](./02-execution-context.md)