

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

---

## Navigation

⬅️ Previous: [02. Intermediate](./02-intermediate.md)

🏠 Home: [Core Concepts](./README.md)

➡️ Next: [04. Senior](./04-senior.md)