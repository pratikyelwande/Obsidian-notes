### **What is JavaScript?**

> JavaScript is a high-level, interpreted programming language used to add interactivity to websites, running in the browser and on servers via Node.js.

---

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

## ==JS Working-==

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
## ==Memory Management of JS-==

JavaScript handles memory automatically using garbage collection, primarily with the mark-and-sweep algorithm.  
Closures can cause memory leaks if they unintentionally hold references to unused variables — especially in long-lived functions like event handlers.
## ==DataType==
### **1. Global Scope**

> Any variable declared **outside of all functions and blocks** is in the global scope.

✅ Accessible **anywhere** in your script.

`const name = "Ali";  function greet() {   console.log(name); // ✅ can access global variable }  greet(); console.log(name); // ✅ works here too`

---

### 🔧 **2. Function Scope**

> A variable declared **inside a function** is only accessible **inside that function**.

✅ Applies to `var`, `let`, and `const`.


`function test() {   let age = 30;   console.log(age); // ✅ 30 }  test(); console.log(age); // ❌ Error: age is not defined`

🟡 `var` is also **function scoped**, not block scoped!

`function demo() {   if (true) {     var x = 10;   }   console.log(x); // ✅ 10: var ignores blocks, but still inside function }`

---

### 🧱 **3. Block Scope**

> A variable declared with `let` or `const` inside **any `{}` block** exists **only inside that block**.

✅ Blocks: `if`, `for`, `{}` — anything with `{}`


`if (true) {   let x = 1;   const y = 2;   console.log(x, y); // ✅ inside block }  console.log(x); // ❌ Error console.log(y); // ❌ Error`

🛑 But `var` doesn’t respect block scope:

`if (true) {   var z = 3; } console.log(z); // ✅ 3 — var leaked out`

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

## LET & VAR
## 1. **Scope Difference**

|Keyword|Scope Type|Example|
|---|---|---|
|`var`|❌ Function-scoped only|Ignored `{}` blocks|
|`let`|✅ Block-scoped|Respects `{}` blocks|

`if (true) {   var a = 10;   let b = 20; }  console.log(a); // ✅ 10 console.log(b); // ❌ Error (block scoped)`

---

## 🔸 2. **Hoisting Difference**

## What is **Hoisting**?
	Hoisting means variable and function declarations are moved to the top of their scope during compilation.  
	`var` is hoisted and initialized with `undefined`, so it can be accessed before its declaration.  
	`let` and `const` are also hoisted, but not initialized — accessing them before the line causes a ReferenceError

- **Both `var` and `let` are hoisted**, but they behave **very differently**.

| Keyword | Hoisted? | Initialized?                 | Can Use Before Declared? |
| ------- | -------- | ---------------------------- | ------------------------ |
| `var`   | ✅ Yes    | ✅ (as `undefined`)           | ✅ Allowed (but bad)      |
| `let`   | ✅ Yes    | ❌ No (in temporal dead zone) | ❌ Error                  |

### 🧪 Example:

`console.log(x); // undefined var x = 5;  console.log(y); // ❌ ReferenceError let y = 10;`

---

## 🔸 3. **Re-declaration**

|Keyword|Re-declaration in same scope?|
|---|---|
|`var`|✅ Allowed|
|`let`|❌ Not allowed|

|Feature|`var`|`let`|
|---|---|---|
|Scope|Function|Block|
|Hoisting|Yes (initialized to `undefined`)|Yes (TDZ applies)|
|Can re-declare|✅ Yes|❌ No|
|Global object (`window`)|✅ Yes|❌ No|
|Safe to use?|❌ No (avoid)|✅ Yes|

### What's the difference between `null` and `undefined`?

> `undefined` means a variable has been declared but not assigned a value — it's the default.  
> `null` is an assignment value that represents "no value" or "empty" — and is set **intentionally**.

# Operators
## **Optional Chaining `?.` 

Optional chaining (`?.`) allows safe access to deeply nested object properties without causing runtime errors if a property doesn't exist.

`let user = {}; console.log(user?.name); // undefined, no error`

## **Ternary Operator**

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

`function sum(...numbers) {   return numbers.reduce((a, b) => a + b); }  sum(1, 2, 3, 4); // 10`

## **Arrow Functions (ES6)**


`const greet = () => {   console.log("Hello"); };  const add = (a, b) => a + b;`

## What Is a Callback Function?

> A **callback** is a function **passed as an argument** to another function, so it can be **called later**.


`function greet(name, callback) {`
  `console.log("Hello " + name);`
  `callback();`
`}`

`function sayBye() {`
  `console.log("Goodbye");`
`}`

`greet("Ali", sayBye);`


## `.map()` — Transform Items

> Used to create a **new array** by applying a **transformation** to each element.

### 🔧 Syntax:


`const newArray = array.map((value, index, array) => {   return transformedValue; });`

### ✅ Key Facts:

- Returns a **new array**
    
- Same length as original
    
- Doesn’t modify original
    
- Return value becomes the new item
    

## 🔍 `.filter()` — Select Items

> Used to create a **new array** by keeping only the elements that match a **condition**.

### 🔧 Syntax:


`const filteredArray = array.filter((value, index, array) => {   return condition; // true to keep, false to discard });`

### ✅ Key Facts:

- Returns a **subset** of the original
    
- Only items that return `true` stay
    
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


# What Is **Lexical Scope**?

> **Lexical** means: "Based on the location in the source code."

### ✅ Lexical Scope =

> **Lexical scope** means **scope is determined by where the code is written**, not by how or where it is called.

`function outer() {
  const msg = "I'm in outer";

  function inner() {
    console.log(msg);
  }

  return inner;
}

const fn = outer(); // fn = inner, defined inside outer
fn(); // ✅ Prints: "I'm in outer"`

## What Is a Closure?

> A **closure** is a function that **remembers** the variables from its **lexical scope**, even after the outer function has finished.

### 🔧 Closure Example:

`function outer() {
  let count = 0;

  return function inner() {
    count++;
    console.log(count);
  };
}

const counter = outer(); // outer() runs and returns inner()
counter(); // 1
counter(); // 2
counter(); // 3`

# Asynchronous JavaScript (Async JS)

1. ✅ **Synchronous vs Asynchronous** — what’s the difference?
    
2. ✅ **`setTimeout` / `setInterval`**
    
3. ✅ **The Event Loop** (already touched, we’ll connect it)
    
4. ✅ **Callback Hell**
    
5. ✅ **Promises**
    
6. ✅ **Async / Await**
    
7. ✅ **Error Handling in async**
   
### What is Asynchronous JS
Asynchronous JavaScript allows your program to start a task that might take a long time (like fetching data from the internet) and continue running other parts of your code **without waiting** for that long task to complete.

## `setTimeout(callback, delay)`

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


`let count = 0;  const intervalId = setInterval(() => {   count++;   console.log("Count:", count);    if (count === 5) {     clearInterval(intervalId); // stop after 5 runs   } }, 1000);`

🟢 Prints:

`Count: 1  Count: 2  Count: 3  Count: 4  Count: 5`

## What Is a Promise?

A **Promise** is a JavaScript object that represents a value that may **not be available yet**, but will be resolved **in the future** (or fail).

`function downloadFile(fileName) {
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
  .catch(err => console.log(err));`

# Async Await-

 ### What Does `async` Do?

- Declares a function as **asynchronous**.
    
- Automatically returns a **Promise**.


`async function f() {   return 10; } // Equivalent to: function f() {   return Promise.resolve(10); }`

---

### 🔹 What Does `await` Do?

- Pauses the `async` function until the **Promise resolves**.
    
- Can only be used **inside `async` functions** (except top-level `await` in modules or Node 14+).

`async function getData() {   const res = await fetch('https://api.com');   const data = await res.json(); }`


## **Immutability & Pure Functions**

### 🔹 What is Immutability?

> Data **cannot be changed** after creation.


`const arr = [1, 2]; const newArr = [...arr, 3]; // ✅ Immutable approach`


`arr.push(3); // ❌ Mutates original`

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


`function add(a, b) {   return a + b; }`

- Input: `add(2, 3)` → Output: `5`
    
- Always gives same result
    
- Doesn’t touch outside world
  
## What is **Coupling**?

> Coupling describes **how connected or dependent** one piece of code is on another.

There are two types:

- 🔴 **Tightly Coupled** – pieces of code depend **directly** on each other
    
- 🟢 **Loosely Coupled** – code pieces are **independent** and interact via **interfaces or contracts**
  

## ✅ What is Debouncing?

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
## What is Throttling?

> **Throttle** limits a function to run at most **once every X milliseconds**, even if it’s triggered many times.

- It **doesn't wait** for inactivity.
    
- Useful for **scroll**, **mousemove**, **resize**, etc.
  




