# 💻 Coding Questions

> **Module:** JavaScript
>
> **Topic:** Scope
>
> **Level:** Beginner → FAANG
>
> **Interview Frequency:** ⭐⭐⭐⭐⭐
>
> **Estimated Reading Time:** 2–3 Hours

---

# Overview

This chapter focuses entirely on interview coding questions.

Unlike previous chapters, this file contains practical coding problems frequently asked in Frontend and JavaScript interviews.

Do **not** immediately open the answer.

Spend at least **5–10 minutes** solving each problem before revealing the solution.

---

# Difficulty

🟢 Easy (1–5)

🟡 Medium (6–10)

🟠 Hard (11–15)

🔴 Senior (16–20)

⚫ FAANG (21–25)

---

# Questions

<details>
<summary><strong>Q1. Predict the Output</strong></summary>

## Problem

```javascript
let message = "Hello";

function greet() {

    console.log(message);

}

greet();
```

---

## Expected Output

```text
Hello
```

---

## Explanation

`message` belongs to the Global Scope.

When `greet()` executes, JavaScript cannot find `message` inside the function, so it follows the Scope Chain to the Global Scope.

---

## Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Q2. Function Scope</strong></summary>

## Problem

Predict the output.

```javascript
function test() {

    let score = 95;

}

console.log(score);
```

---

## Expected Output

```text
ReferenceError: score is not defined
```

---

## Explanation

`score` exists only inside the Function Scope created by `test()`.

Outside the function, the variable is inaccessible.

---

## Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Q3. Block Scope</strong></summary>

## Problem

```javascript
if (true) {

    let city = "Delhi";

}

console.log(city);
```

---

## Expected Output

```text
ReferenceError
```

---

## Explanation

`let` is Block Scoped.

The variable exists only inside the `if` block.

---

## Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Q4. Variable Shadowing</strong></summary>

## Problem

Predict the output.

```javascript
let language = "JavaScript";

function interview() {

    let language = "TypeScript";

    console.log(language);

}

interview();

console.log(language);
```

---

## Expected Output

```text
TypeScript

JavaScript
```

---

## Explanation

The inner variable shadows the outer variable inside the function.

Outside the function, the original variable remains unchanged.

---

## Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Q5. <code>var</code> vs <code>let</code></strong></summary>

## Problem

Predict the output.

```javascript
if (true) {

    var age = 30;

    let salary = 50000;

}

console.log(age);

console.log(salary);
```

---

## Expected Output

```text
30

ReferenceError
```

---

## Explanation

`var` is Function Scoped.

`let` is Block Scoped.

---

## Difficulty

🟢 Easy

</details>

<details>
<summary><strong>Q6. Nested Scope Lookup</strong></summary>

## Problem

Predict the output.

```javascript
const company = "OpenAI";

function department() {

    const team = "Frontend";

    function developer() {

        console.log(company);

        console.log(team);

    }

    developer();

}

department();
```

---

## Your Task

Explain the Scope Chain used for both variables before checking the answer.

---

## Expected Output

```text
OpenAI

Frontend
```

---

## Explanation

`developer()` first searches its own Scope.

- `company` → not found → Global Scope.
- `team` → found in the parent Function Scope.

JavaScript resolves variables using lexical Scope.

---

## Difficulty

🟡 Medium

</details>

<details>
<summary><strong>Q7. Closure Counter</strong></summary>

## Problem

Complete the function so each call increments the counter.

```javascript
function createCounter() {

    // Your code

}

const counter = createCounter();

console.log(counter());

console.log(counter());

console.log(counter());
```

---

## Expected Output

```text
1

2

3
```

---

## One Possible Solution

```javascript
function createCounter() {

    let count = 0;

    return function () {

        return ++count;

    };

}
```

---

## Explanation

The returned function forms a Closure over `count`, allowing it to persist between calls.

---

## Difficulty

🟡 Medium

</details>

<details>
<summary><strong>Q8. Loop with <code>setTimeout()</code></strong></summary>

## Problem

Predict the output.

```javascript
for (var i = 1; i <= 3; i++) {

    setTimeout(() => {

        console.log(i);

    }, 100);

}
```

---

## Your Task

1. Predict the output.
2. Explain why it happens.
3. Modify the code so the output becomes:

```text
1
2
3
```

---

## Hint

Think about:

- Function Scope
- Block Scope
- Closures

---

## Expected Output

```text
4
4
4
```

---

## One Possible Solution

```javascript
for (let i = 1; i <= 3; i++) {

    setTimeout(() => {

        console.log(i);

    }, 100);

}
```

---

## Output

```text
1
2
3
```

---

## Explanation

`var` creates one shared variable for the entire loop.

All callbacks capture the same variable.

By the time the callbacks execute, the loop has completed and `i` equals `4`.

Using `let` creates a new Block Scope for each iteration, so every callback captures its own value.

---

## Follow-up Questions

- Can you solve this without using `let`?
- How would an IIFE solve this?
- Why was Block Scope introduced in ES6?

---

## Difficulty

🟡 Medium

</details>

<details>
<summary><strong>Q9. Module Scope</strong></summary>

## Problem

You have two files.

### user.js

```javascript
const username = "Anmol";

export function getUser() {

    return username;

}
```

---

### app.js

```javascript
import { getUser } from "./user.js";

console.log(username);

console.log(getUser());
```

---

## Your Task

Predict the output.

Explain why one statement succeeds while the other fails.

---

## Hint

Think about:

- Module Scope
- Export
- Import

---

## Expected Output

```text
ReferenceError

Anmol
```

---

## Explanation

`username` belongs to the Module Scope of `user.js`.

Only exported members are accessible from other modules.

`getUser()` is exported, so it can access `username` internally and return its value.

---

## Follow-up Questions

- Why are ES Modules safer than global variables?
- Can another module access `username` directly?
- How does Module Scope improve maintainability?

---

## Difficulty

🟡 Medium

</details>

<details>
<summary><strong>Q10. Scope Chain Debugging</strong></summary>

## Problem

Predict the output.

```javascript
const company = "OpenAI";

function engineering() {

    const team = "Frontend";

    function developer() {

        const role = "Senior Engineer";

        console.log(company);

        console.log(team);

        console.log(role);

    }

    developer();

}

engineering();
```

---

## Your Task

Before checking the answer, explain exactly how JavaScript resolves each variable.

Draw the Scope Chain.

---

## Expected Output

```text
OpenAI

Frontend

Senior Engineer
```

---

## Scope Chain

```text
developer()

↓

engineering()

↓

Global Scope
```

---

## Variable Resolution

| Variable | Found In |
|----------|----------|
| `role` | developer() |
| `team` | engineering() |
| `company` | Global Scope |

---

## Explanation

JavaScript starts searching in the current lexical Scope.

If a variable is not found, it moves to the parent Scope.

This continues until:

- The variable is found, or
- The Global Scope is reached.

If the variable is still not found, a `ReferenceError` is thrown.

---

## Follow-up Questions

- Does JavaScript ever search sibling Scopes?
- When is the Scope Chain created?
- Does execution order affect the Scope Chain?

---

## Difficulty

🟡 Medium

</details>

<details>
<summary><strong>Q11. Build a Private Counter using Closures</strong></summary>

## Problem

Implement a function called `createCounter()`.

Requirements:

- The counter starts from `0`.
- Each call to `increment()` increases the count by `1`.
- Each call to `decrement()` decreases the count by `1`.
- `count` must be private.
- It should not be directly accessible.

---

## Example

```javascript
const counter = createCounter();

console.log(counter.increment());

console.log(counter.increment());

console.log(counter.decrement());

console.log(counter.count);
```

---

## Expected Output

```text
1

2

1

undefined
```

---

## Hint

Use a Closure to preserve state.

---

## One Possible Solution

```javascript
function createCounter() {

    let count = 0;

    return {

        increment() {
            return ++count;
        },

        decrement() {
            return --count;
        }

    };

}
```

---

## Explanation

The variable `count` exists inside the lexical scope of `createCounter()`.

The returned object methods form Closures over that Scope.

External code cannot access `count` directly.

---

## Follow-up Questions

- How would you add a `reset()` method?
- Can this be implemented using a class?
- Which approach provides better encapsulation?

---

## Difficulty

🟠 Hard

</details>

<details>
<summary><strong>Q12. Implement Function Memoization</strong></summary>

## Problem

Implement a generic `memoize()` function.

Requirements:

- Cache function results.
- Return cached values for repeated inputs.
- Use Closures to preserve the cache.

---

## Example

```javascript
function square(n) {

    console.log("Calculating...");

    return n * n;

}

const memoizedSquare = memoize(square);

console.log(memoizedSquare(5));

console.log(memoizedSquare(5));

console.log(memoizedSquare(10));
```

---

## Expected Output

```text
Calculating...

25

25

Calculating...

100
```

---

## Hint

Store results in an object or `Map`.

---

## One Possible Solution

```javascript
function memoize(fn) {

    const cache = new Map();

    return function (...args) {

        const key = JSON.stringify(args);

        if (cache.has(key)) {
            return cache.get(key);
        }

        const result = fn(...args);

        cache.set(key, result);

        return result;

    };

}
```

---

## Explanation

The returned function keeps the cache alive using a Closure.

Repeated calls avoid unnecessary computation.

---

## Follow-up Questions

- Why is `Map` preferred over an object?
- What are the limitations of `JSON.stringify()`?
- How would you implement cache expiration?

---

## Difficulty

🟠 Hard

</details>

<details>
<summary><strong>Q13. Identify and Fix the Memory Leak</strong></summary>

## Problem

Review the following code.

```javascript
function loadUsers() {

    const users = fetchHugeDataset();

    document
        .getElementById("btn")
        .addEventListener("click", function () {

            console.log("Users Loaded");

        });

}
```

---

## Your Task

1. Identify the potential memory issue.
2. Explain why it happens.
3. Refactor the code.

---

## Hint

Think about:

- Closures
- Event listeners
- Garbage Collection

---

## One Possible Solution

```javascript
function loadUsers() {

    fetchHugeDataset();

    const button = document.getElementById("btn");

    function handleClick() {

        console.log("Users Loaded");

    }

    button.addEventListener("click", handleClick);

}
```

---

## Explanation

If the event listener unnecessarily captures large objects, those objects remain reachable and cannot be garbage collected.

Closures should capture only the data they actually need.

---

## Follow-up Questions

- How would you verify this using Chrome DevTools?
- When should event listeners be removed?
- How would this issue appear in React?

---

## Difficulty

🟠 Hard

</details>

<details>
<summary><strong>Q14. Refactor Nested Scope into Cleaner Code</strong></summary>

## Problem

Refactor the following implementation.

```javascript
function app() {

    function dashboard() {

        function reports() {

            function analytics() {

                console.log("Loading...");

            }

            analytics();

        }

        reports();

    }

    dashboard();

}

app();
```

---

## Your Task

Improve readability without changing behavior.

---

## One Possible Solution

```javascript
function analytics() {

    console.log("Loading...");

}

function reports() {

    analytics();

}

function dashboard() {

    reports();

}

function app() {

    dashboard();

}

app();
```

---

## Explanation

The original code works correctly, but unnecessary nesting makes it harder to:

- Read
- Debug
- Test
- Reuse

Flattening the structure improves maintainability while preserving behavior.

---

## Follow-up Questions

- Is deep nesting always bad?
- When should nested functions be kept?
- What trade-offs are involved?

---

## Difficulty

🟠 Hard

</details>

<details>
<summary><strong>Q15. Build a Module Pattern (Without ES Modules)</strong></summary>

## Problem

Before ES Modules existed, developers used the Module Pattern.

Implement a `UserModule` that:

- Keeps `users` private.
- Exposes:
  - `addUser()`
  - `getUsers()`

---

## Example

```javascript
UserModule.addUser("Anmol");

UserModule.addUser("John");

console.log(UserModule.getUsers());
```

---

## Expected Output

```text
["Anmol", "John"]
```

---

## Hint

Use an IIFE and Closures.

---

## One Possible Solution

```javascript
const UserModule = (function () {

    const users = [];

    return {

        addUser(name) {

            users.push(name);

        },

        getUsers() {

            return [...users];

        }

    };

})();
```

---

## Explanation

The IIFE executes once, creating a private Scope.

The returned methods form Closures over that Scope, allowing controlled access to private data.

---

## Follow-up Questions

- Why was this pattern popular before ES6?
- How do ES Modules improve this approach?
- What are the advantages of exposing behavior instead of data?

---

## Difficulty

🟠 Hard

</details>

<details>
<summary><strong>Q16. Debug a Production Scope Bug</strong></summary>

## Problem

A production bug has been reported.

Users click **Save**, but the console always logs the previous value instead of the latest one.

```javascript
let formData = {
    name: "John"
};

function registerSave() {

    document
        .getElementById("save")
        .addEventListener("click", () => {

            console.log(formData.name);

        });

}

registerSave();

formData = {
    name: "Alice"
};
```

---

## Requirements

Explain:

- Why this happens.
- Is this actually a Scope issue?
- Is it a Closure issue?
- How would you debug it?
- How would you fix it?

---

## Hint

Think about:

- Closures
- References
- Event Listeners

---

## One Possible Solution

The callback closes over the **variable**, not a snapshot of its value.

When the event fires, it reads the current object referenced by `formData`.

If the actual production bug involves logging stale values, inspect where and when the callback was created. In React, stale closures are a common cause.

---

## What Interviewers Expect

A strong candidate should discuss:

- Lexical Scope
- Closures
- Object references
- Event listeners
- Debugging strategy

---

## Follow-up Questions

- Would the behavior change if `formData` were declared with `const`?
- How would React behave differently?
- How would Chrome DevTools help?

---

## Difficulty

🔴 Senior

</details>

<details>
<summary><strong>Q17. Refactor a Legacy Module</strong></summary>

## Problem

Review the following legacy implementation.

```javascript
window.users = [];

window.addUser = function (user) {

    users.push(user);

};

window.removeUser = function (user) {

    users = users.filter(u => u !== user);

};
```

---

## Requirements

Refactor this implementation to:

- Eliminate Global Scope pollution.
- Hide internal implementation.
- Improve maintainability.
- Preserve functionality.

---

## Hint

Think about:

- Module Scope
- Closures
- Encapsulation

---

## One Possible Solution

```javascript
const UserService = (() => {

    const users = [];

    return {

        addUser(user) {

            users.push(user);

        },

        removeUser(user) {

            const index = users.indexOf(user);

            if (index !== -1) {
                users.splice(index, 1);
            }

        },

        getUsers() {

            return [...users];

        }

    };

})();
```

---

## Explanation

The module now owns its own state.

Consumers interact through a public API instead of modifying shared global variables.

---

## Follow-up Questions

- How would ES Modules improve this further?
- Should mutable arrays ever be returned directly?
- How would you unit test this module?

---

## Difficulty

🔴 Senior

</details>

<details>
<summary><strong>Q18. Optimize Closure Usage</strong></summary>

## Problem

Review the implementation.

```javascript
function createSearch(products) {

    return function (keyword) {

        return products.filter(product =>
            product.name.includes(keyword)
        );

    };

}
```

`products` contains over **500,000** records.

---

## Requirements

Explain:

- Is this implementation incorrect?
- Could it cause excessive memory usage?
- How would you improve it?

---

## Hint

Think about:

- Closure lifetime
- Memory usage
- Data ownership

---

## One Possible Solution

Possible improvements include:

- Load data lazily.
- Use pagination.
- Query the server instead of storing everything.
- Capture only the required data.
- Release references when no longer needed.

The Closure itself is not the problem.

Keeping a huge dataset alive unnecessarily is.

---

## What Interviewers Expect

Discussion around:

- Memory profiling
- Garbage Collection
- Chrome Heap Snapshots
- Trade-offs

---

## Follow-up Questions

- How would you profile memory?
- When is a Closure actually a memory leak?
- Would WeakMap help here?

---

## Difficulty

🔴 Senior

</details>

<details>
<summary><strong>Q19. Fix a React Stale Closure Bug</strong></summary>

## Problem

Users report that the application logs an old counter value.

```javascript
function Counter() {

    const [count, setCount] = useState(0);

    function handleClick() {

        setTimeout(() => {

            console.log(count);

        }, 3000);

    }

}
```

---

## Requirements

Explain:

- Why this bug occurs.
- Which Scope is captured?
- How would you fix it?

---

## Hint

Think about:

- React rendering
- Closures
- State updates

---

## One Possible Solution

Possible approaches include:

- Functional state updates.
- `useRef`.
- Appropriate Hook dependency management.

The callback captures the Scope of the render during which it was created.

---

## What Interviewers Expect

Discussion around:

- React rendering
- Lexical Scope
- Closures
- Hooks
- Async execution

---

## Follow-up Questions

- Why doesn't React update old Closures?
- How does `useRef` help?
- When should `useCallback` be used?

---

## Difficulty

🔴 Senior

</details>

<details>
<summary><strong>Q20. Design a Scoped Event Manager</strong></summary>

## Problem

Design an event manager.

Requirements:

- Register listeners.
- Remove listeners.
- Emit events.
- Keep listeners private.
- Prevent Global Scope pollution.

---

## Example

```javascript
const events = createEventManager();

events.on("login", callback);

events.emit("login");

events.off("login", callback);
```

---

## Requirements

Design the API.

Implement the solution.

Explain your design decisions.

Discuss trade-offs.

---

## Hint

Think about:

- Closures
- Module Pattern
- Encapsulation
- Memory management

---

## One Possible Solution

Use a Closure to keep the internal event registry private.

Expose only:

- on()
- off()
- emit()

The implementation details remain inaccessible to consumers.

---

## What Interviewers Expect

A strong candidate should discuss:

- Encapsulation
- API design
- Ownership
- Memory cleanup
- Listener lifecycle

---

## Follow-up Questions

- How would you prevent memory leaks?
- Would you use `Map`?
- How would you support `once()`?

---

## Difficulty

🔴 Senior

</details>

<details>
<summary><strong>Q21. Debug a Multi-Level Scope & Closure Bug</strong></summary>

## Problem

A production bug has been reported.

The expected output is:

```text
Admin
Dashboard
Settings
```

Actual output:

```text
Admin
Dashboard
Dashboard
```

Review the code.

```javascript
function createDashboard(role) {

    let currentPage = "Dashboard";

    function navigate(page) {

        currentPage = page;

    }

    function logger() {

        return function () {

            console.log(role);
            console.log(currentPage);

        };

    }

    const log = logger();

    navigate("Settings");

    return log;

}

const logDashboard = createDashboard("Admin");

logDashboard();
```

---

## Requirements

1. Explain why the output is different from the expectation.
2. Draw the Scope Chain.
3. Explain which variables are captured.
4. Is this a Closure issue or a Scope issue?
5. Modify the implementation so the logger prints the page when it was created.

---

## Hint

Think about:

- Lexical Scope
- Closures
- Variable references
- Captured values vs captured variables

---

## One Possible Solution

Capture the required value before returning the Closure.

```javascript
function logger() {

    const page = currentPage;

    return function () {

        console.log(role);
        console.log(page);

    };

}
```

---

## What Interviewers Expect

Candidates should explain:

- Closures capture variables, not snapshots.
- Variables remain shared unless copied.
- Lexical Scope determines lookup.
- Closures preserve the surrounding environment.

---

## Follow-up Questions

- How would React behave in a similar scenario?
- Would `const` change the behavior?
- How would you debug this in Chrome DevTools?

---

## Difficulty

⚫ FAANG

</details>

<details>
<summary><strong>Q22. Build a Dependency Injection Container using Closures</strong></summary>

## Problem

Implement a lightweight Dependency Injection (DI) container.

Requirements:

- Register services.
- Resolve services.
- Keep the registry private.
- Prevent direct modification of registered services.

Example:

```javascript
const container = createContainer();

container.register("logger", Logger);

container.register("api", ApiService);

const logger = container.resolve("logger");
```

---

## Requirements

Implement:

```javascript
register(name, dependency)

resolve(name)

has(name)

remove(name)
```

The internal registry must remain private.

---

## Hint

Think about:

- Closures
- Module Pattern
- Encapsulation

---

## One Possible Solution

```javascript
function createContainer() {

    const registry = new Map();

    return {

        register(name, dependency) {

            registry.set(name, dependency);

        },

        resolve(name) {

            return registry.get(name);

        },

        has(name) {

            return registry.has(name);

        },

        remove(name) {

            registry.delete(name);

        }

    };

}
```

---

## What Interviewers Expect

Discussion around:

- Encapsulation
- API design
- Module Scope
- Dependency Injection
- Private state

---

## Follow-up Questions

- How would singleton services work?
- How would you detect circular dependencies?
- How would Angular's DI container differ?

---

## Difficulty

⚫ FAANG

</details>

<details>
<summary><strong>Q23. Debug a Memory Leak in a Large SPA</strong></summary>

## Problem

A Single Page Application gradually consumes more memory after users navigate between pages for several hours.

The following pattern appears repeatedly:

```javascript
function initializeDashboard(data) {

    document
        .getElementById("refresh")
        .addEventListener("click", () => {

            console.log(data.length);

        });

}
```

`data` contains hundreds of thousands of records.

---

## Requirements

Explain:

- Why memory continues to grow.
- How Scope contributes.
- How Closures contribute.
- How you would investigate.
- How you would fix it.

---

## Hint

Think about:

- Heap Snapshots
- Event listeners
- Reachability
- Garbage Collection

---

## One Possible Solution

Possible improvements include:

- Remove event listeners during cleanup.
- Capture only required values.
- Avoid retaining the entire dataset.
- Recreate listeners only when necessary.
- Profile memory using Chrome DevTools.

---

## What Interviewers Expect

Candidates should discuss:

- Memory profiling
- Heap Snapshots
- Detached DOM nodes
- Closure lifetime
- Garbage Collection

---

## Follow-up Questions

- How would React cleanup this listener?
- How would WeakMap help?
- How would you confirm the leak is fixed?

---

## Difficulty

⚫ FAANG

</details>

<details>
<summary><strong>Q24. Design a Plugin System using Module Scope</strong></summary>

## Problem

Design a plugin architecture.

Requirements:

- Register plugins.
- Execute plugins.
- Prevent plugins from modifying internal framework state.
- Expose only a public API.

Example:

```javascript
framework.register(plugin);

framework.execute("beforeRender");
```

---

## Requirements

Design:

- Plugin registration
- Lifecycle hooks
- Public API
- Internal storage

Explain:

- Scope boundaries
- Ownership
- Encapsulation
- Security

---

## Hint

Think about:

- Module Scope
- Closures
- Public APIs
- Encapsulation

---

## One Possible Solution

Maintain the plugin registry inside Module Scope.

Expose only:

```javascript
register()

execute()

unregister()
```

Never expose the internal plugin collection.

---

## What Interviewers Expect

Discussion around:

- Module boundaries
- Encapsulation
- Extensibility
- Maintainability
- Team scalability

---

## Follow-up Questions

- How would you isolate third-party plugins?
- How would you support plugin priorities?
- How would you prevent duplicate registrations?

---

## Difficulty

⚫ FAANG

</details>

<details>
<summary><strong>Q25. Design a Secure Configuration Manager</strong></summary>

## Problem

Build a configuration manager.

Requirements:

- Configuration values must remain private.
- Consumers should not mutate internal state directly.
- Only approved APIs should expose configuration.

Example:

```javascript
const config = createConfigManager();

config.set("theme", "dark");

console.log(config.get("theme"));
```

---

## Requirements

Implement:

- get()
- set()
- has()
- remove()
- reset()

The internal configuration object must never be exposed directly.

---

## Hint

Think about:

- Closures
- Encapsulation
- Module Pattern
- Defensive copying

---

## One Possible Solution

```javascript
function createConfigManager() {

    const settings = new Map();

    return {

        get(key) {

            return settings.get(key);

        },

        set(key, value) {

            settings.set(key, value);

        },

        has(key) {

            return settings.has(key);

        },

        remove(key) {

            settings.delete(key);

        },

        reset() {

            settings.clear();

        }

    };

}
```

---

## What Interviewers Expect

Discussion around:

- Encapsulation
- Defensive design
- Private state
- Public APIs
- Module Scope

---

## Follow-up Questions

- Should `get()` return mutable objects?
- How would you make configuration read-only?
- How would you support environment-specific overrides?

---

## Difficulty

⚫ FAANG

</details>

---

# Coding Chapter Summary

After completing this chapter, you should be able to:

- Predict Scope-related outputs.
- Explain variable lookup and the Scope Chain.
- Build private state using Closures.
- Implement Module Pattern solutions.
- Debug Scope and Closure issues.
- Refactor legacy code to improve encapsulation.
- Optimize memory usage related to Closures.
- Design scalable APIs using Module Scope.
- Solve production-level Scope problems.

---

## Navigation

⬅️ Previous: [05. Architect](./05-architect.md)

🏠 Home: [Scope](./README.md)

➡️ Next: [07. Scenario](./07-scenario.md)