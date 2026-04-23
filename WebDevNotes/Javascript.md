### **What is JavaScript?**

> JavaScript is a **high-level, interpreted programming language** used to add interactivity to websites, running in the browser and on servers via Node.js.

---
## ==JS Working-==
## Step 1: Call Stack (the only place code runs)

When you write:

```
console.log("A"); 
console.log("B");
```

JS does:

1. Put `console.log("A")` on the stack → run it → remove it
    
2. Put `console.log("B")` on the stack → run it → remove it
    

That’s it. Simple.

If the call stack is busy, **nothing else can run**.

---

## Step 2: The problem with slow things

Now imagine this:

```
fetch("data-from-internet"); 
console.log("Done");
```

Fetching data can take seconds.

If JavaScript waited for it:

- the page would freeze
    
- buttons wouldn’t click
    
- browser would look dead
    

So JavaScript says:

> “I refuse to wait. Someone else handle this.”

---

## Step 3: Enter Web APIs (helpers, not JS)

The **browser** provides helpers called **Web APIs**.

Web APIs handle:

- timers
    
- network
    
- events
    

Examples:

- `setTimeout`
    
- `fetch`
    
- click events
    

Important:  
👉 **Web APIs do NOT run your JavaScript code**  
👉 They only _wait_ and _notify_

---

## Step 4: What happens when JS sees async code

Example:

```
setTimeout(() => {   
console.log("Hello"); }, 1000);  
console.log("World");
```

What JS does:

1. Sees `setTimeout`
    
2. Hands timer to **Web API**
    
3. Immediately continues
    
4. Prints `"World"`
    

So output so far:

`World`

The callback is **NOT executed yet**.

---

## Step 5: Where does the callback go after waiting?

After 1 second, Web API finishes waiting.

Now it asks:

> “Where do I put this callback?”

Answer: **a queue**.

But there are **two different queues**.

---

## Step 6: Two queues (this is the core confusion)

### Queue 1: Microtask Queue (HIGH priority)

This queue is for:

- Promise callbacks
    
- `then`
    
- `catch`
    
- `async/await`
    

Example:

`Promise.resolve().then(() => console.log("Promise"));`

---

### Queue 2: Macrotask Queue (LOW priority)

This queue is for:

- `setTimeout`
    
- `setInterval`
    
- DOM events
    

Example:

`setTimeout(() => console.log("Timeout"), 0);`

---

## Step 7: Important rule (memorize this)

**Async does NOT decide the queue.  
The API decides the queue.**

- Promise → **Microtask queue**
    
- Timer / event → **Macrotask queue**
    

---
## Step 8: Event Loop (the traffic policeman)

The **event loop** constantly asks one question:

> “Is the call stack empty?”

If **NO** → wait  
If **YES** → do this:

1. Run **ALL microtasks**
    
2. Then run **ONE macrotask**
    
3. Repeat forever
    

---

## Step 9: Let’s see everything together (slow)

```
console.log("Start");  
setTimeout(() => console.log("Timeout"), 0);  
Promise.resolve().then(() => console.log("Promise"));  
console.log("End");`
```

### Step-by-step:

### 1️⃣ Call stack runs sync code

`Start End`

### 2️⃣ Web APIs finish

- Promise callback → microtask queue
    
- setTimeout callback → macrotask queue
    

### 3️⃣ Call stack is empty → event loop starts

Event loop rule:

- Microtasks first
    
- Then macrotasks
    

So output:

```
Promise
Timeout
```

### Final output:

```
Start 
End 
Promise 
Timeout
```

Always. No exception.

---

Your Code
   ↓
[ Call Stack ] ← runs one thing at a time

If async → send to:
  → [ Web APIs ] → when done → push to:
    → Microtask Queue (for Promises)
    → Macrotask Queue (for timeouts, events)

[ Event Loop ]
  → Is Call Stack empty?
      → Run Microtask
      → Then Macrotask

> The event loop allows JavaScript to handle asynchronous operations in a single-threaded environment. It runs sync code first, and then processes callbacks from queues when the call stack is empty. Promises (microtasks) run before timeouts (macrotasks).

### ✅ **Q2: How does JavaScript execute code?**

> JavaScript uses a single-threaded **call stack** to execute synchronous code line-by-line.

---

### ✅ **Q3: How does JavaScript handle asynchronous tasks?**

> Asynchronous operations are handled by the **browser’s Web APIs**, and their callbacks are added to task queues once complete.

---

### ✅ **Q4: What is the Event Loop?**

> The **event loop** checks if the call stack is empty, and if so, moves tasks from **microtask** or **macrotask queues** into the stack for execution.

---

### ✅ **Q5: What’s the difference between microtask and macrotask queues?**

> **Microtasks** (like Promises) have higher priority and run before **macrotasks** (like setTimeout).

## ==Memory Management of JS-==

JavaScript handles memory automatically using garbage collection, primarily with the mark-and-sweep algorithm.  
Closures can cause memory leaks if they unintentionally hold references to unused variables — especially in long-lived functions like event handlers.
## ==DataType==
### ==**1. Global Scope**==

> Any variable declared **outside of all functions and blocks** is in the global scope.

✅ Accessible **anywhere** in your script.

```
const name = "Ali";  
function greet() {   
console.log(name); // ✅ can access global variable }  greet(); console.log(name); // ✅ works here too
```

---

### ==🔧 **2. Function Scope**==

> A variable declared **inside a function** is only accessible **inside that function**.

✅ Applies to `var`, `let`, and `const`.


```
function test() {
let age = 30;   
console.log(age); // ✅ 30 }
test(); 
console.log(age); // ❌ Error: age is not defined
```

🟡 `var` is also **function scoped**, not block scoped!

```
	function demo() {
	if (true) {
	var x = 10;   }   
	console.log(x); // ✅ 10: var ignores blocks, but still inside function 
	}
```

---

### ==🧱 **3. Block Scope**==

> A variable declared with `let` or `const` inside **any `{}` block** exists **only inside that block**.

✅ Blocks: `if`, `for`, `{}` — anything with `{}`


```
if (true) {   
let x = 1;   
const y = 2;   
console.log(x, y); // ✅ inside block }  
console.log(x); // ❌ Error 
console.log(y); // ❌ Error
```

🛑 But `var` doesn’t respect block scope:

```
if (true) {   
var z = 3; } 
console.log(z); // ✅ 3 — var leaked out
```

---

## 🎯 Scope Summary Table

|Feature|Global Scope|Function Scope|Block Scope|
|---|---|---|---|
|`var`|✅ Yes|✅ Yes|❌ No|
|`let` / `const`|✅ Yes|✅ Yes|✅ Yes|
|Accessible everywhere?|✅|❌ Only inside function|❌ Only inside block|

---

## 💬 Interview Line:

> Global scope variables are available everywhere.  
> Function scope variables are limited to the function.  
> Block scope variables (`let`, `const`) are only accessible inside `{}` where they’re declared.  
> `var` ignores blocks and only respects function scope.

## ==LET & VAR==
## 1. **Scope Difference**

|Keyword|Scope Type|Example|
|---|---|---|
|`var`|❌ Function-scoped only|Ignored `{}` blocks|
|`let`|✅ Block-scoped|Respects `{}` blocks|

```
if (true) {   
var a = 10;   
let b = 20; }  
console.log(a); // ✅ 10 
console.log(b); // ❌ Error (block scoped)
```

---
## ==What is **Hoisting**?==
	Hoisting means variable and function declarations are moved to the top of their scope during compilation.  
	`var` is hoisted and initialized with `undefined`, so it can be accessed before its declar ation.  
	`let` and `const` are also hoisted, but not initialized — accessing them before the line causes a ReferenceError

- **Both `var` and `let` are hoisted**, but they behave **very differently**.

| Keyword | Hoisted? | Initialized?                 | Can Use Before Declared? |
| ------- | -------- | ---------------------------- | ------------------------ |
| `var`   | ✅ Yes    | ✅ (as `undefined`)           | ✅ Allowed (but bad)      |
| `let`   | ✅ Yes    | ❌ No (in temporal dead zone) | ❌ Error                  |

### 🧪 Example:

```
console.log(x); // undefined 
var x = 5;  
console.log(y); // ❌ ReferenceError 
let y = 10;
```

---
## 🔸 3. **Re-declaration**

|Keyword|Re-declaration in same scope?|
|---|---|
|`var`|✅ Allowed|
|`let`|❌ Not allowed|

| Feature                  | `var`                            | `let`             | const             |
| ------------------------ | -------------------------------- | ----------------- | ----------------- |
| Scope                    | Function                         | Block             |                   |
| Hoisting                 | Yes (initialized to `undefined`) | Yes (TDZ applies) | Yes (TDZ applies) |
| Can re-declare           | ✅ Yes                            | ❌ No              | No                |
| Global object (`window`) | ✅ Yes                            | ❌ No              |                   |
| Safe to use?             | ❌ No (avoid)                     | ✅ Yes             | Yes               |
| Feature                  | var                              | let               | const             |
| Scope                    | Function                         | Block             | Block             |
| Hoisted                  | Yes                              | Yes               | Yes               |
| Initialized on hoist     | Yes (`undefined`)                | No (TDZ)          | No (TDZ)          |
| Re-declaration           | Yes                              | No                | No                |
| Reassignment             | Yes                              | Yes               | No                |
| Global object binding    | Yes                              | No                | No                |
| Recommended              | Never                            | Sometimes         | Default           |
### What's the difference between `null` and `undefined`?

> `undefined` means a variable has been declared but not assigned a value — it's the default.  
> `null` is an assignment value that represents "no value" or "empty" — and is set **intentionally**.

# ==Operators==
## ==**Optional Chaining `?.`== 

Optional chaining (`?.`) allows safe access to deeply nested object properties without causing runtime errors if a property doesn't exist.

```
let user = {}; 
console.log(user?.name); // undefined, no error
```

## ==**Ternary Operator**==

Shorthand for if-else.

`condition ? valueIfTrue : valueIfFalse`
### 🔸 Example:

`let age = 18; let result = age >= 18 ? "Adult" : "Minor"; // "Adult"`

## **Nullish Coalescing (`??`)**

> Returns right side only if left is `null` or `undefined`.

`let a = null ?? "Default";    // "Default" let b = 0 ?? "Fallback";     
 // 0 (✅ because it's not null or undefined)
 `
 
# Functions
## **Rest Parameters (`...`)**

> To handle multiple arguments

```
function sum(...numbers) {   
return numbers.reduce((a, b) => a + b); }  
sum(1, 2, 3, 4); // 10
```

## **Arrow Functions (ES6)**


`const greet = () => {   console.log("Hello"); };  const add = (a, b) => a + b;`

## ==What Is a Callback Function?==

> A **callback** is a function **passed as an argument** to another function, so it can be **called later**.


```
function greet(name, callback) {
  console.log("Hello " + name);
  callback();
}
```

```
function sayBye() {`
  console.log("Goodbye");
}
```
```
greet("Ali", sayBye);
```


## ==`.map()` — Transform Items==

> Used to create a **new array** by applying a **transformation** to each element.

### 🔧 Syntax:


```const newArray = array.map((value, index, array) => {   return transformedValue; });```

### ✅ Key Facts:

- Returns a **new array**
    
- Same length as original
    
- Doesn’t modify original
    
- Return value becomes the new item
    

## ==🔍 `.filter()` — Select Items==

> Used to create a **new array** by keeping only the elements that match a **condition**.

### 🔧 Syntax:

```
const filteredArray = array.filter((value, index, array) => { 
return condition; // true to keep, false to discard });
```
### ✅ Key Facts:

- Returns a **subset** of the original
    
- Only items that return `true` or `false`
    
- Doesn’t modify original
    
- Often used for search, selection, cleanup
---

## 🧠 `.map()` vs `.filter()` – Comparison Table

|Feature|`.map()`|`.filter()`|
|---|---|---|
|Purpose|Transform every item|Keep items that pass a condition|
|Return|New array (same length)|New array (possibly shorter)|
|Callback Must|Return new value|Return `true` or `false`|
|Modifies?|❌ No (pure function)|❌ No|
|Real Use|Extract keys, reshape data|Search, exclude, clean lists|
## ==`reduce()`==
### Purpose

Combine all elements into **one value**.
### Rule

- Result can be any type
    
- Uses an accumulator (`acc`)
    
- Requires an initial value for safety
### Syntax

```
array.reduce((acc, curr, index, array) => newAcc, initialValue)
```
### Example: sum

```
const nums = [1, 2, 3]; 
const sum = nums.reduce((acc, curr) => acc + curr, 0); // 6
```
# ==What Is **Lexical Scope**?==

> **Lexical** means: "Based on the location in the source code."

### ✅ Lexical Scope =

> **Lexical scope** means **scope is determined by where the code is written**, not by how or where it is called.

```
function outer() {
  const msg = "I'm in outer";

  function inner() {
    console.log(msg);
  }

  return inner;
}

const fn = outer(); // fn = inner, defined inside outer
fn(); // ✅ Prints: "I'm in outer"
```

## ==What Is a Closure?==

> A **closure** is a function that ==**remembers** the variables== from its **lexical scope**, even after the outer function has finished.

### 🔧 Closure Example:

```
function outer() {
  let count = 0;

  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer(); // outer() runs and returns inner()
counter(); // 1
counter(); // 2
counter(); // 3
```

# Asynchronous JavaScript (Async JS)

1. ✅ **Synchronous vs Asynchronous** — what’s the difference?
    
2. ✅ **`setTimeout` / `setInterval`**
    
3. ✅ **The Event Loop** (already touched, we’ll connect it)
    
4. ✅ **Callback Hell**
    
5. ✅ **Promises**
    
6. ✅ **Async / Await**
    
7. ✅ **Error Handling in async**
   
### ==What is Asynchronous JS==

Asynchronous JavaScript allows your program to start a task that might take a long time (like fetching data from the internet) and continue running other parts of your code **without waiting** for that long task to complete.

## 🔁 1. `setTimeout(callback, delay)`

> Executes the `callback` function **once**, after the specified `delay` (in milliseconds).
### 🔧 Syntax:

`setTimeout(() => {   console.log("Hello after 2 seconds"); }, 2000);`
### ✅ Output:

`Hello after 2 seconds`

---

## 🛑 Important:

- The delay is **non-blocking** — JS doesn't stop or wait.
    
- It **schedules** the task and moves on.
---

## 🔁 2. `setInterval(callback, delay)`

> Executes the `callback` **repeatedly** every `delay` ms.

### 🔧 Example:


```
let count = 0;  
const intervalId = setInterval(() => {
count++;   
console.log("Count:", count);    
if (count === 5) {     
clearInterval(intervalId); // stop after 5 runs   } }, 1000);
```

🟢 Prints:

`Count: 1  Count: 2  Count: 3  Count: 4  Count: 5`

## ==What Is a Promise?==

A **Promise** is a JavaScript object that represents a value that may **not be available yet**, but will be resolved **in the future** (or fail).

```
function downloadFile(fileName) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (fileName) {
        resolve(`✅ Downloaded: ${fileName}`);
      } else {
        reject("❌ No file provided.");
      }
    }, 1500);
  });
}

downloadFile("resume.pdf")
  .then(result => console.log(result))
  .catch(err => console.log(err));
```

## Creating a Promise

### Syntax

```
new Promise((resolve, reject) => {
  // async work
});

```

### Example

```
function getNumber() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(10);
    }, 1000);
  });
}

```

---

## 3. Consuming a Promise (`then`, `catch`, `finally`)

### `then` – success handler

```
getNumber().then(result => {
  console.log(result); // 10
});
```

### `catch` – error handler

```
getNumber().catch(err => {
  console.log(err);
});

```

### `finally` – always runs

```
getNumber().finally(() => {
  console.log("Done");
});

```

---

## 4. Promise Chaining (most important concept)

### Rule

> The value returned from `then()` goes to the next `then()`.

### Example

```
getNumber()
  .then(num => {
    return num * 2;
  })
  .then(result => {
    console.log(result); // 20
  });

```

---

## 5. Error Propagation

### Example

```
getNumber()
  .then(num => {
    throw "Something went wrong";
  })
  .then(() => {
    console.log("Will not run");
  })
  .catch(err => {
    console.log(err); // Something went wrong
  });

```

Errors move down the chain until caught.

---

## 6. Promise Always Runs Asynchronously

### Example

```
console.log("Start");

Promise.resolve("Done").then(res => {
  console.log(res);
});

console.log("End");

```

### Output

`Start End Done`

---

## 7. `Promise.all()`

### Purpose

Run multiple promises in parallel. All must succeed.

### Example

```
Promise.all([
  Promise.resolve(1),
  Promise.resolve(2),
  Promise.resolve(3)
])
.then(results => {
  console.log(results); // [1, 2, 3]
})
.catch(err => {
  console.log(err);
});
```
### Failure case

```
Promise.all([
  Promise.resolve(1),
  Promise.reject("Error"),
  Promise.resolve(3)
])
.catch(err => {
  console.log(err); // Error
});

```

---

## 8. `Promise.allSettled()`

### Purpose

Get result of all promises, success or failure.

### Example

```
Promise.allSettled([
  Promise.resolve("A"),
  Promise.reject("B"),
  Promise.resolve("C")
])
.then(results => {
  console.log(results);
});

```

Output:

```
[
  { status: "fulfilled", value: "A" },
  { status: "rejected", reason: "B" },
  { status: "fulfilled", value: "C" }
]

```

---

## 9. `Promise.race()`

### Purpose

First promise to settle wins (success or failure).

### Example

```
Promise.race([
  new Promise(res => setTimeout(() => res("Fast"), 500)),
  new Promise(res => setTimeout(() => res("Slow"), 2000))
])
.then(result => {
  console.log(result); // Fast
});

```

---

## 10. `Promise.any()`

### Purpose

First successful promise wins.

### Example
```
Promise.race([
  new Promise(res => setTimeout(() => res("Fast"), 500)),
  new Promise(res => setTimeout(() => res("Slow"), 2000))
])
.then(result => {
  console.log(result); // Fast
});

```

---

## 11. Common Mistakes

### Forgetting to return

`.then(() => {   fetchData(); // WRONG });`

Correct:

`.then(() => {   return fetchData(); });`

## Eg

```
// Fake async task
function task(name, time, shouldFail = false) {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      if (shouldFail) {
        reject(name + " failed");
      } else {
        resolve(name + " success");
      }
    }, time);
  });
}

console.log("START");

// ----------------------------------
// 1. Basic Promise + then + catch + finally
// ----------------------------------

task("Task1", 1000)
  .then(result => {
    console.log(result);          // Task1 success
    return "Next value";          // chaining
  })
  .then(value => {
    console.log(value);           // Next value
    throw "Manual error";         // error propagation
  })
  .catch(err => {
    console.log("Caught:", err);  // Manual error
  })
  .finally(() => {
    console.log("Task1 finished");
  });

// ----------------------------------
// 2. Promise.all (all must succeed)
// ----------------------------------

Promise.all([
  task("A", 1000),
  task("B", 1500),
  task("C", 500)
])
.then(results => {
  console.log("ALL:", results);
})
.catch(err => {
  console.log("ALL failed:", err);
});

// ----------------------------------
// 3. Promise.allSettled (report all)
// ----------------------------------

Promise.allSettled([
  task("D", 500),
  task("E", 800, true),
  task("F", 300)
])
.then(results => {
  console.log("ALL SETTLED:", results);
});

// ----------------------------------
// 4. Promise.race (first settled)
// ----------------------------------

Promise.race([
  task("Fast", 400),
  task("Slow", 2000)
])
.then(result => {
  console.log("RACE winner:", result);
})
.catch(err => {
  console.log("RACE error:", err);
});

// ----------------------------------
// 5. Promise.any (first success)
// ----------------------------------

Promise.any([
  task("X", 300, true),
  task("Y", 600, true),
  task("Z", 900)
])
.then(result => {
  console.log("ANY success:", result);
})
.catch(err => {
  console.log("ANY failed:", err.errors);
});

console.log("END");

```

---

# ==Async Await-==

 ### What Does `async` Do?

- Declares a function as **asynchronous**.
    
- Automatically returns a **Promise**.


```
async function f() {   
return 10; } 
// Equivalent to: 
function f() {
   return Promise.resolve(10); 
   }
```

---
### 🔹 What Does `await` Do?

- Pauses the `async` function until the **Promise resolves**.
    
- Can only be used **inside `async` functions** (except top-level `await` in modules or Node 14+).

```
async function getData() {   
const res = await fetch('https://api.com');   
const data = await res.json(); }
```


## **Immutability & Pure Functions**

### 🔹 What is Immutability?

> Data **cannot be changed** after creation.


```
const arr = [1, 2]; 
const newArr = [...arr, 3]; // ✅ Immutable approach
```


```
arr.push(3); // ❌ Mutates original
```

### 🔹 Why It Matters:

- Avoids side effects
    
- Easier to debug and test
    
- Crucial in **React/Redux** state updates
  
## What is a Pure Function?

> A **pure function** is a function that:

1. **Always returns the same output** for the same input
    
2. **Has no side effects**

---
## 📌 Characteristics of Pure Functions

|Property|Pure Function|
|---|---|
|Same output for same input|✅ Always|
|Depends only on input values|✅ Yes|
|Modifies global state|❌ Never|
|Reads/modifies external vars|❌ No|
|Has side effects (e.g., console, DOM, API)|❌ No|
|Easy to test/debug|✅ Very easy|

---

## 🧪 Examples

### ✅ Pure Function


```
function add(a, b) {
   return a + b; 
   }
```

- Input: `add(2, 3)` → Output: `5`
    
- Always gives same result
    
- Doesn’t touch outside world
  
## ==What is **Coupling**?==

> Coupling describes **how connected or dependent** one piece of code is on another.

There are two types:

- 🔴 **Tightly Coupled** – pieces of code depend **directly** on each other
    
- 🟢 **Loosely Coupled** – code pieces are **independent** and interact via **interfaces or contracts**
  

## ✅ What is Debouching?

> **Debounce** limits how often a function is called by waiting until **after** a series of rapid events has stopped.

- It waits for **inactivity**.
- Useful for **typing**, **resizing**, **search**, etc.

### 🔧 How it Works

- You keep resetting the timer each time the function is triggered.
- The function only executes **once**, after no calls have been made for the delay time.

---

### 🧪 Debounce Code Example

```js
function debounce(fn, delay) {
  let timer;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn(...args), delay);
  };
}
```
## ==What is Throttling?==

> **Throttle** limits a function to run at most **once every X milliseconds**, even if it’s triggered many times.

- It **doesn't wait** for inactivity.
    
- Useful for **scroll**, **mousemove**, **resize**, etc.
  
## **==Currying
==**
==Currying means breaking a function that takes many arguments into multiple functions that take one argument at a time.==
## Start from normal functions (baseline)

```
function add(a, b) {   
return a + b; }  
add(2, 3); // 5
```

Two arguments. One call. Boring. Predictable.

---
## Curried version

```
function add(a) {   
return function (b) {     
return a + b;   }; }  
add(2)(3); // 5
```

Same result. Different structure.

What changed?

- Instead of **one function with two args**
    
- You now have **two functions with one arg each**
    

That transformation is **currying**.

---
## ==CALL BIND APPLY==

Functions in JavaScript do **not** have a fixed `this`.  
`call`, `apply`, and `bind` exist to **explicitly control what `this` refers to at execution time**.

---
## `call()`

Invokes a function **immediately**, explicitly setting `this`.
### Syntax

`fn.call(thisArg, arg1, arg2, ...)`
### Key points

- Executes immediately
    
- `thisArg` becomes `this`
    
- Arguments passed individually
    
- Temporary binding
### Example

```
function greet(city) {   
console.log(this.name, city); }  
const user = { name: "Pratik" };  
greet.call(user, "Pune");
```
### Use case

- Borrow methods
    
- One-time execution with controlled `this`
    

---
## ==`apply()`==

### Definition

Same as `call`, but arguments are passed as an array.

### Syntax

`fn.apply(thisArg, [arg1, arg2, ...])`

### Key points

- Executes immediately
    
- `thisArg` becomes `this`
    
- Arguments passed as array
    
- Useful when arguments are already in array form
    

### Example

`greet.apply(user, ["Pune"]);`

### Use case

- Dynamic argument lists
    
- Legacy code patterns
    
---
## ==`bind()`==

### Definition

Returns a **new function** with `this` permanently bound.

### Syntax

`const newFn = fn.bind(thisArg, arg1, arg2, ...)`

### Key points

- Does **not** execute immediately
    
- Returns a new function
    
- `this` is fixed forever
    
- Supports partial arguments (currying)
    

### Example

`const boundGreet = greet.bind(user); boundGreet("Pune");`

### Use case

- Passing methods as callbacks
    
- Event handlers
    
- Preserving context in async code
    

---
## Side-by-side comparison

|Feature|call|apply|bind|
|---|---|---|---|
|Executes immediately|Yes|Yes|No|
|Returns function|No|No|Yes|
|`this` binding|Temporary|Temporary|Permanent|
|Argument style|Individual|Array|Individual|
|Rebind possible|Yes|Yes|No|

---
## Important facts

- `this` is **not** a function parameter
    
- `this` is injected into the execution context
    
- Arrow functions ignore `call`, `apply`, and `bind`
    
- `bind` cannot be overridden

---
## Common interview traps

- `bind` does not execute
    
- `call` and `apply` differ only in argument format
    
- Losing `this` happens when methods are detached
    
- `this` depends on how a function is called, not where it is defined


