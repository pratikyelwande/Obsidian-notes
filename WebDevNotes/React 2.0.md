## What is React?

**React** is a **JavaScript library for building user interfaces**, mainly for ==single-page applications== (SPAs). It lets you build web apps by **breaking the UI into reusable components**.

### ✅ Quick Facts:

- Created by **Facebook** in 2013
    
- Focused only on the **View** layer (MVC)
    
- Allows **component-based architecture**
    
- Enables **declarative UI development**

==JSX stands for **JavaScript XML**. It’s a **syntax extension** that allows us to write **HTML directly inside JavaScript==
## What is State in React?

==**State** is an object that holds **data** about the component== that can **change over time**.

Whenever state **changes**, the component **re-renders**, and the UI updates automatically.

## **What is a Component in React?**

A **component** is a **reusable building block** of a React application.  
It’s a JavaScript **function** (or class) that returns **JSX**, which tells React **what to render** on the screen.

## ==**What is a Lifecycle?**==

## 🔄 3 Main Lifecycle Phases

1. **Mounting** – Component is created and added to the DOM
    
2. **Updating** – Component re-renders due to state/props change
    
3. **Unmounting** – Component is removed from the DOM

---

## ✅ Functional Components (Using Hooks)

React uses the `useEffect` hook to mimic lifecycle behavior.

### 🔹 Mount (componentDidMount)

`useEffect(() => {   // Runs once after first render }, []);`
### 🔹 Update (componentDidUpdate)

`useEffect(() => {   // Runs when 'count' changes }, [count]);`
### 🔹 Unmount (componentWillUnmount)

`useEffect(() => {   return () => {     // Cleanup logic   }; }, []);`


## ==🔍 React Under the Hood – How It Really Works==

### 1. JSX ➡️ React.createElement ➡️ React Element

When you write this:

`const element = <h1>Hello</h1>;`

React **compiles** it (via Babel)to

==Babel is a transpiler==(combination of compile and transform)
**You write code in JSX + modern JS**  
⬇️  
🛠 **Babel translates it to plain JS**  
⬇️  
⚙️ **V8 executes the plain JS**

`const element = React.createElement('h1', null, 'Hello');`

This returns a **plain JavaScript object** like:

`{   type: 'h1',   props: {     children: 'Hello'   } }`

## 2.What is the Virtual DOM?

The **Virtual DOM (VDOM)** is a **lightweight JavaScript object-based copy** of the real DOM.

- It's **not shown in the browser**
    
- It's stored **in memory**
    
- It mirrors the actual DOM structure using **React Elements**

### 3. Reconciliation: React's Diffing Algorithm

When state or props change:

1. The component **re-runs** (re-render)
    
2. React builds a new **Virtual DOM tree**
    
3. It compares (diffs) the **new tree** with the **previous one**
    
4. Calculates the **minimal set of changes**-
		==**Fiber is React's new rendering engine**== that powers how React renders and updates the DOM.
		- Fiber breaks the rendering work into **chunks** and processes it **asynchronously**
		
		- Input typing: 🔥 High priority
		    
		- Animation: 🔁 Medium
		    
		- Analytics logging: 🐢 Low
		Fiber schedules high-priority tasks first and **splits work into chunks**,    preventing UI freezes.
    
5. Updates only the changed parts in the **real DOM**
    

> 💡 This process is called **Reconciliation**

### 4. Commit Phase: Real DOM Update

Once the diff is calculated, React:

- **Commits** the changes
    
- Applies them to the real DOM
    
- Calls lifecycle functions (e.g., `useEffect`, `componentDidupdate`)

## ==🧩 What are Props?==

**Props** (short for **properties**) are the way to **pass data** from a **parent component** to a **child component**.

Think of props like **function arguments**, but for components.
## 💡 Props are:

- **Read-only** (cannot be changed inside child)
    
- **Passed from parent → child**
    
- **Used to customize components**


## 1. **Passing Strings, Numbers, Booleans**

### 🧩 `MovieCard.jsx`


```
const MovieCard = ({ title, rating, isAvailable }) => (
   <div style={{ border: '1px solid #ccc', padding: '12px', margin: '10px' }}>     <h2>{title}</h2>     <p>Rating: {rating}/10</p>  
  <p style={{ color: isAvailable ? 'green' : 'red' }}>  
       {isAvailable ? 'Now Showing' : 'Coming Soon'}    
   </p>   </div> ); 
   export default MovieCard;
```

### 🧩 `App.jsx`


`import MovieCard from './MovieCard';  const App = () => (   <div>     <MovieCard title="Inception" rating={8.8} isAvailable={true} />     <MovieCard title="Interstellar" rating={8.6} isAvailable={false} />   </div> );  export default App;`

---

## ✅ 2. **Passing Arrays**

### 🧩 `HobbyList.jsx`


`const HobbyList = ({ hobbies }) => (   <ul>     {hobbies.map((hobby, i) => (       <li key={i}>{hobby}</li>     ))}   </ul> );  export default HobbyList;`

### 🧩 `App.jsx`


`import HobbyList from './HobbyList';  const App = () => {   const userHobbies = ['Reading', 'Cycling', 'Gaming'];    return (     <div>       <h2>My Hobbies</h2>       <HobbyList hobbies={userHobbies} />     </div>   ); };  export default App;`

---

## ✅ 3. **Passing Objects**

### 🧩 `UserInfo.jsx`


`const UserInfo = ({ user }) => (   <div>     <h3>{user.name}</h3>     <p>Email: {user.email}</p>     <p>Age: {user.age}</p>   </div> );  export default UserInfo;`

### 🧩 `App.jsx`


`import UserInfo from './UserInfo';  const App = () => {   const user = {     name: 'Alice',     email: 'alice@example.com',     age: 27,   };    return (     <div>       <UserInfo user={user} />     </div>   ); };  export default App;`

## What are Default Props? ⚙️

**Default props** are fallback values a component uses for its properties (props) if the parent component **doesn't explicitly provide those props**. They ensure your component always has certain values to work with, even if a parent forgets to pass them, making the component more robust and easier to use.

```
import React from 'react';
import ReactDOM from 'react-dom/client';

// --- Child Component: WelcomeMessage ---
// This is your component, using an arrow function.
// It destructures 'name' from props and sets a default value of "Stranger".
const WelcomeMessage = ({ name = "Stranger" }) => {
  return (
    <p>Hello, {name}!</p>
  );
};

// --- Parent Component: App ---
const App = () => {
  return (
    <div>

      {/* Result: "Hello, Alice!" */}
      <WelcomeMessage name="Alice" />

      {/* Result: "Hello, Stranger!" (because no 'name' prop was given) */}
      <WelcomeMessage />

      {/* Result: "Hello, Bob!" */}
      <WelcomeMessage name="Bob" />
    </div>
  );
};
```


## **Callback Props (Function Props)**

This is how **child components send data or events** **back up** to the **parent component** — crucial for communication 🔝🔄

---

## 🧠 Why Use Callback Props?

- Props go **from parent to child**
    
- But when child needs to **notify the parent** (e.g., button clicked, input changed), you pass a **function as a prop**
    
- The **child calls it**, and the parent responds 💬
    

---

## ✅ Real-World Example: Child Button Notifying Parent

### 🧩 `ChildButton.jsx`


`const ChildButton = ({ onClickHandler }) => (   <button onClick={onClickHandler}>Click Me</button> );  export default ChildButton;`

---
### 🧩 `App.jsx`

`import { useState } from 'react'; import ChildButton from './ChildButton';  const App = () => {   const [count, setCount] = useState(0);    const handleChildClick = () => {     setCount((prev) => prev + 1);   };    return (     <div>       <h2>Button clicked {count} times</h2>       <ChildButton onClickHandler={handleChildClick} />     </div>   ); };  export default App;`

## 🧸 What is the `children` Prop?

The `children` prop allows you to **pass nested JSX** (elements, text, or even other components) **inside a component’s opening and closing tags**.

### 🧩 `Box.jsx`
Child

`const Box = ({ children }) => (   <div style={{ border: '1px solid black', margin: '10px', padding: '10px' }}>     {children}   </div> );  export default Box;`

---
Parent 
### 🧩 `App.jsx`

`import Box from './Box';  const App = () => (   <div>     <Box>       <h3>This is inside Box 1</h3>       <p>Paragraph goes here.</p>     </Box>      <Box>       <button>Click Me</button>     </Box>      <Box>       <ul>         <li>List item 1</li>         <li>List item 2</li>       </ul>     </Box>   </div> );  export default App;`

## 🪓 What is Prop Drilling?

**Prop Drilling** is when you pass props through **multiple layers** of components.

## 🔍 State vs Props in React

|Feature|**Props**|**State**|
|---|---|---|
|📦 Source|Passed **from parent** component|Stored **inside** the component itself|
|✏️ Mutability|**Read-only**|**Mutable** (via `setState` or `useState`)|
|🔁 Usage|Used to **configure** or customize child|Used to **track local changes** in a component|
|🔄 Updates UI?|✅ Yes — when props or state changes, React re-renders||
|🔁 How to change|Parent must pass new props|Use `useState` or `this.setState()`|
|💬 Analogy|Like **function arguments**|Like **variables inside a component**|

## 🧠 What Are React Hooks?

**Hooks** are **functions** that let you **"hook into" React features** (like state, lifecycle, and context)

## ==✅ What is `useState`?==

`useState` is a **React Hook** that lets you **add state** to **functional components**.

> 📦 It returns a pair:  
> `[currentState, setStateFunction]`

---
## 🧠 Syntax


`const [state, setState] = useState(initialValue);`

- `state` → Current state value
    
- `setState` → Function to update the state
    
- `initialValue` → Starting value (used only once)
    

---
## 🧪 Example

```
import React, { useState } from 'react';  
function Counter() {
   const [count, setCount] = useState(0); // initialValue = 0    
   return (     
   <div> 
   <p>Count: {count}</p>       
   <button onClick={() => setCount(count + 1)}>Increment</button>    
    </div>); 
   }
```

---
## 🛠️ State Update Flow

1. `useState(initialValue)` runs → sets the initial state
    
2. Component renders
    
3. User triggers `setState(newValue)`
    
4. React:
    
    - Updates the internal state
        
    - Triggers a re-render
        
5. New state is passed to the next render


## ==🧠 What is `useEffect`?==

> `useEffect` allows you to perform **side effects** in functional components.

### 🔧 Side effects include:

- Fetching data from an API 🌐
    
- Setting up subscriptions or timers ⏰
    
- Updating the DOM manually 🧱
    
- Working with browser APIs like `localStorage` 🗃️
    

---

## 🧪 Syntax


```
useEffect(() => {   // Side-effect logic here   
return () => {
// Cleanup (optional)   }; }, [dependencies]);
```

---

## 🔄 Lifecycle Comparison (for class components)

|Lifecycle Method|`useEffect` Equivalent|
|---|---|
|`componentDidMount`|`useEffect(() => { ... }, [])`|
|`componentDidUpdate`|`useEffect(() => { ... }, [dep])`|
|`componentWillUnmount`|`return () => { ... }` inside `useEffect`|

---
## 🧪 Example 1: API Call on Mount

```
import { useEffect, useState } from 'react';  
function UserProfile() {   
const [user, setUser] = useState(null);    
useEffect(() => {     fetch('https://jsonplaceholder.typicode.com/users/1')       .then(res => res.json()).then(data => setUser(data));   }, []); // run only once when component mounts    
return user ? <h1>{user.name}</h1> : <p>Loading...</p>; }
```

### 📌 Why `[]`?

- An empty dependency array (`[]`) makes it run **only once** (on mount), like `componentDidMount`

## ✅ `useEffect` Dependency Array Cheat Sheet

|Dependency Array|When to Use It|Behaves Like|Runs On|
|---|---|---|---|
|`[]` _(empty array)_|Run once on mount (e.g., fetch on first load)|`componentDidMount`|✅ First render only|
|`[dep1, dep2]`|Run when **any** dependency changes|`componentDidUpdate` for those values|✅ First render + whenever `dep1` or `dep2` changes|
|_(no array at all)_|Run after **every render**|Like `componentDidUpdate` _every time_|✅ Every render (⚠️ usually not recommended)|
|`return () => {}`|Cleanup function (optional)|`componentWillUnmount`|When component unmounts or before effect re-runs|

---

## 🔍 Examples for Each Case

---
### 🎯 1. Empty `[]` → Run **once** on mount

`useEffect(() => {   console.log('✅ Runs only once on mount'); }, []);`

💡 Use when: fetching initial data, setting up once-only listeners, initializing.

---
### 🔁 2. `[count]` → Run when `count` changes

``useEffect(() => {   console.log(`🟡 Count changed to: ${count}`); }, [count]);``

💡 Use when: syncing state, updating based on props/state, watching inputs.

---
### ⚠️ 3. No dependency array → Run on **every render**

`useEffect(() => {   console.log('⚠️ Runs after every render'); });`

🚫 Use only if you **intentionally** want this (rare). Can lead to infinite loops or performance issues.

---
### 🧹 4. Cleanup (unsubscribe, clear interval, etc.)

`useEffect(() => {   const timer = setInterval(() => {     console.log('⏰ ticking...');   }, 1000);    return () => {     clearInterval(timer); // ✅ cleanup     console.log('🧹 timer cleared');   }; }, []);`

💡 Use when: setting intervals, event listeners, WebSockets, etc.

## ==🔹 What is `useRef`?==

`useRef()` is a React Hook that returns a **mutable object** that:

- **Does not cause re-renders** when changed
    
- **Persists** across component re-renders
    
- Can be used to **access DOM elements** or **store any value** (like a timer, flag, or previous state)

---
## 🔹 Syntax

`const myRef = useRef(initialValue);`

- `myRef.current` → The actual value or reference (you can read/write this)

---
## 🔹 Main Use Cases

|🔧 Purpose|✅ Example|
|---|---|
|Access DOM elements|Focus input, scroll, animations|
|Store timers/intervals|Background alarms, API polling|
|Store previous values|Compare current vs previous state|
|Keep mutable values across renders|Flags, counters, render count|
|Avoid re-renders|Store data without causing UI updates|

---
## 🔹 Real Examples

### 1. Accessing DOM Element

`const inputRef = useRef();  <input ref={inputRef} /> <button onClick={() => inputRef.current.focus()}>Focus</button>`

### 2. Store Previous State Value

`const prevValue = useRef();  useEffect(() => {   prevValue.current = currentValue; }, [currentValue]);`

### 3. Timer or Background Process

`const timerRef = useRef();  timerRef.current = setInterval(() => {   // do something every second }, 1000);  // To stop it later: clearInterval(timerRef.current);`

---
## 🔹 `useRef` vs `useState`

| `useState`                   | `useRef`                              |
| ---------------------------- | ------------------------------------- |
| Triggers re-render on update | ❌ No re-render                        |
| Used for UI-related state    | Used for storing values or references |
| React watches for changes    | React ignores `.current` changes      |
| Shows updates on screen      | Hidden from UI                        |
## ==🔍 What is Context?==

React **Context** is a way to **share values (data/state)** between components **without passing props manually at every level**.

---
## 🧠 Why Use It?

To avoid **prop drilling** — when you pass data through many intermediate components just to reach a deeply nested child.

---
## 🧩 Core APIs

|API|Purpose|
|---|---|
|`createContext()`|Creates a Context object|
|`Context.Provider`|Provides the context value to its children|
|`useContext(Context)`|Hook to consume context in any child component|

---
## 🛠️ Step-by-Step Usage

### 1. **Create a Context**

```
import { createContext } from 'react'; 
export const MyContext = createContext();
```

---
### 2. **Provide the Context (at top level)**

`<MyContext.Provider value={someData}>   <YourComponentTree /> </MyContext.Provider>`

---
### 3. **Consume the Context (anywhere)**

`import { useContext } from 'react'; import { MyContext } from './MyContextFile';  const value = useContext(MyContext);`


# 📒 React `useReducer` – 

### ==🔧 What is a Reducer?==

- A **function** that decides how to change the state.
    
- Takes **2 things**:
    
    1. `state` → current value
        
    2. `action` → what you want to do
        
- Returns a **new state**.
    

---

### 🧠 Reducer Syntax


`function reducer(state, action) {   if (action.type === 'INCREMENT') {     return state + 1;   }   if (action.type === 'DECREMENT') {     return state - 1;   }   return state; }`

---

### ✅ Basic `useReducer` Setup


`const [state, dispatch] = useReducer(reducer, initialState);`

- `state`: current value (like count)
    
- `dispatch(action)`: send an action (like a command)
    
- `reducer`: decides what to do
    

---

### 🚀 How It Works (Step-by-step)

1. You call:

    `dispatch({ type: 'INCREMENT' });`
    
2. React runs your `reducer` function:
    
    `reducer(state, { type: 'INCREMENT' })`
    
3. Reducer returns the new state.
    
4. React re-renders the component with the new state.

---
### 🔁 Example: Counter

`function reducer(state, action) {   if (action.type === 'INCREMENT') return state + 1;   if (action.type === 'DECREMENT') return state - 1;   return state; }  function Counter() {   const [count, dispatch] = useReducer(reducer, 0);    return (     <div>       <h2>Count: {count}</h2>       <button onClick={() => dispatch({ type: 'INCREMENT' })}>+</button>       <button onClick={() => dispatch({ type: 'DECREMENT' })}>-</button>     </div>   ); }`

## ==✅ What is `useMemo`?==

`useMemo` is a React hook that **memoizes the result of a function**, so the function **only re-runs when its dependencies change.**

---
## 📦 Syntax

`const memoizedValue = useMemo(() => {   // 💡 expensive calculation here   return computeSomething(a, b); }, [a, b]); // 👈 dependencies`

- `() => {}`: A function that returns the value to cache
    
- `[a, b]`: Dependency array — recompute only when any dependency changes

---
## 🚀 Purpose

- Avoid **recalculating expensive functions** on every render.
    
- Improve **performance** by caching previously computed values.

---
## 🛠️ When to Use

✅ Use `useMemo` when:

- You have **heavy calculations** (loop, sort, filter, etc.)
    
- You want to **optimize performance**
    
- The value **depends on props or state**
---
## ⚠️ When NOT to Use

❌ Don’t use when:

- The calculation is **very cheap/simple**
    
- The value doesn’t need caching
    
- Overusing may cause **performance loss** and code complexity

---
## 🔁 Example: Expensive Function

`const expensiveResult = useMemo(() => {   console.log("Calculating...");   let total = 0;   for (let i = 0; i < 10000000; i++) {     total += i;   }   return total * number; }, [number]);`

- Caches result unless `number` changes
    
- Saves time during re-renders

## ==🔹 What is `useCallback`?==

- `useCallback` is a **React Hook** that **memoizes a function**.
    
- It returns the **same function reference** between renders unless **dependencies change** which helps to prevent re-renders.


`const memoizedFn = useCallback(() => {   // your logic here }, [dependencies]);`

---

## 🎯 Why Use It?

- In React, **functions are re-created** on every render.
    
- If you pass a function to a **child component**, it can cause **unnecessary re-renders**.
    
- `useCallback` prevents this by returning the **same function instance**.

---

## 🧠 What It Does

|Feature|useCallback|
|---|---|
|Memoizes|A function|
|Remembers output?|❌ No (it does NOT cache result)|
|Recreates function?|Only if dependencies change|
|Usage|Optimize performance|

---
## 🛠 Syntax


`const handleClick = useCallback(() => {   console.log("Clicked!"); }, [dependency1, dependency2]);`

- If `dependency1` and `dependency2` do **not change**, `handleClick` will **not be recreated**.

---

## ✅ Example Use Case


```
import React, { useState, useCallback } from "react";

const Child = React.memo(({ onClick }) => {
  console.log("👶 Child rendered");
  return <button onClick={onClick}>Click Child</button>;
});

function Parent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    console.log("Clicked!");
  }, []);

  return (
    <>
      <p>Parent count: {count}</p>

      <Child onClick={handleClick} />

      <button onClick={() => setCount(c => c + 1)}>
        Update Parent
      </button>
    </>
  );
}

export default Parent;

```

### 💡 Why this works:

- `handleClick` keeps the **same reference**
    
- `Child` (wrapped with `React.memo`) won’t re-render unnecessarily

## ==🧭 React Router DOM – Summary Notes==

### 1️⃣ **Basic Routing Setup**

- Install: `npm install react-router-dom`
    
- Wrap App in `<BrowserRouter>`
    
- Use `<Routes>` and `<Route>` to define paths
    
- Use `<Link>` for navigation without refresh


`<Route path="/" element={<Home />} /> <Link to="/about">Go to About</Link>`

---

### 2️⃣ **Nested Routes**

- Used for routes **within** a component (like tabs or profile sections)
    
- Define child routes inside a parent

`<Route path="/dashboard" element={<Dashboard />}>   <Route path="settings" element={<Settings />} /> </Route>`

---

### 3️⃣ **useNavigate**

- Programmatic navigation (like redirect after login)
    
`const navigate = useNavigate(); navigate("/dashboard");`

---

### 4️⃣ **useParams**

- Read dynamic parts of URL (`/user/:id`)

`const { id } = useParams(); console.log(id); // from URL`

---

### 5️⃣ **useSearchParams**

- Read query parameters like `?filter=active`

`const [searchParams] = useSearchParams(); const filter = searchParams.get("filter");`

---

### 6️⃣ **useLocation**

- Access current URL path, query, hash, etc.


`const location = useLocation(); console.log(location.pathname); // current path`

---

### 7️⃣ **Protected Routes**

- Show a route only if user is logged in
    
- Redirect to login if not authenticated

`<Route path="/dashboard" element={   <ProtectedRoute>     <Dashboard />   </ProtectedRoute> } />`

`function ProtectedRoute({ children }) {   return isAuthenticated ? children : <Navigate to="/login" />; }`

# ==📘 Redux Complete Notes (for React JSX)==

---
## 🔧 1. Installation

Install Redux and React-Redux:

`npm install @reduxjs/toolkit react-redux`

---
## 🧠 2. What is Redux?

**Redux** is a state management library that stores your app's global state in one place — the **store**. Components can:

- **Read** from the store via `useSelector`
    
- **Update** the store via `dispatch(action)`

---
## 🧱 3. Core Redux Concepts

|Term|Purpose|
|---|---|
|**Store**|Holds the whole application state|
|**Action**|A plain object describing what happened (type + payload)|
|**Reducer**|A function that modifies the state based on the action|
|**Dispatch**|Sends an action to the store|
|**Selector**|Selects part of the state from the store|
|**Provider**|React context wrapper that gives components access to store|

---
## 🔁 Redux Data Flow (Cycle)

1. **User interacts** (clicks a button)
    
2. Component **dispatches an action**
    
3. Action is handled by **reducer**
    
4. Reducer **updates the state**
    
5. React component **re-renders** with updated state

---
## 🛠️ 4. Basic Setup Steps (ALWAYS)

### Step 1: Create a Redux Slice

📁 `features/counter/counterSlice.js`

`import { createSlice } from '@reduxjs/toolkit';  const counterSlice = createSlice({   name: 'counter',   initialState: { value: 0 },   reducers: {     increment: state => { state.value += 1 },     decrement: state => { state.value -= 1 },     incrementByAmount: (state, action) => {       state.value += action.payload;     }   } });  export const { increment, decrement, incrementByAmount } = counterSlice.actions; export default counterSlice.reducer;`

---
### Step 2: Setup Store

📁 `app/store.js`

`import { configureStore } from '@reduxjs/toolkit'; import counterReducer from '../features/counter/counterSlice';  export const store = configureStore({   reducer: {     counter: counterReducer   } });`

---
### Step 3: Provide the Store

📁 `index.js` or `main.jsx`

`import React from 'react'; import ReactDOM from 'react-dom'; import App from './App'; import { Provider } from 'react-redux'; import { store } from './app/store';  ReactDOM.render(   <Provider store={store}>     <App />   </Provider>,   document.getElementById('root') );`

---
### Step 4: Use Redux in Components

📁 `Counter.jsx`

`import React from 'react'; import { useSelector, useDispatch } from 'react-redux'; import { increment, decrement, incrementByAmount } from './features/counter/counterSlice';  const Counter = () => {   const count = useSelector(state => state.counter.value);   const dispatch = useDispatch();    return (     <div>       <h1>Count: {count}</h1>       <button onClick={() => dispatch(increment())}> + </button>       <button onClick={() => dispatch(decrement())}> - </button>       <button onClick={() => dispatch(incrementByAmount(5))}> +5 </button>     </div>   ); };  export default Counter;`

---
## 🧪 5. Behind the Scenes (How Redux Works Internally)

1. `useSelector` subscribes to the store and gets the state
    
2. `dispatch(action)` sends an object like `{ type: 'counter/increment' }`
    
3. The `counterReducer` checks this `action.type` and updates the state
    
4. New state is pushed into React, triggering re-render

---
## 🧩 6. Benefits of Redux

✅ Centralized state  
✅ Easy debugging (Redux DevTools)  
✅ Predictable state transitions  
✅ Encourages clean architecture  
✅ Works well with large apps


