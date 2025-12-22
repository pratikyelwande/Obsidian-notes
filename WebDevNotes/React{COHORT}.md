Created by Facebook employee in 2013 and Open source in 2015.
# React Router DOM

The `react-router-dom` package contains bindings for using [React Router](https://github.com/remix-run/react-router) in web applications.
`npm i react-router-dom`

- React make virtual copies of DOM and then compares the elements.
- create vite react app-
	~ npm create vite
- JSX( JS XML)-combination of JS and HTML.
### Steps

1. **Install React Router**: `npm install react-router-dom`
2. **Wrap `App` in `BrowserRouter`**: Add `<BrowserRouter>` in `index.js`.
3. **Create Components**: Create `Header` or other components you want to route.
4. **Set Up Routes in App Component**: Use `Routes` and `Route` components with the `element` props
```<Routes>

        <Route path="/" element={<Home />} />

        <Route path="/about" element={<About />} />

      </Routes>
```
5. **Add Navigation Links**: Use `<Link>` components for easy navigation if needed.

```
<nav>

        <Link to="/">Home</Link>

        <Link to="/about">About</Link>

        <Link to="/contact">Contact</Link>

      </nav>
```

## **Lazy Routing**

Lazy routing means loading components **only when needed**, instead of loading everything at once. This helps make your app faster by reducing the initial load time.

---
### **Why Use Lazy Routing**

1. **Faster Initial Load**: Loads only what's necessary for the current page.
2. **Smaller App Size**: Unused parts of the app aren't loaded immediately.
3. **Better Performance**: Saves memory and bandwidth.
### **Example**
jsx

`const Dashboard = React.lazy(() => import('./Dashboard'));  <Suspense fallback={<div>Loading Dashboard...</div>}>   <Routes>     <Route path="/dashboard" element={<Dashboard />} />   </Routes> </Suspense>;
`
### **Two-Way Binding in React**

**Two-way binding** is a concept where the UI and component state stay synchronized, meaning:

- Changes in the UI (like user input) immediately update the component state.
- Updates to the component state reflect back in the UI, keeping the input and state in sync.

In React, two-way binding isn’t built-in by default. Instead, we manually implement it by:

1. Setting the component’s state as the value of an input field.
2. Using an `onChange` handler to update the state whenever the input field changes.

---

### **Example of Two-Way Binding in React**

Here’s an example using a text input to collect a username. This example demonstrates how two-way binding works in React.



```
import React, { useState } from 'react';

const App = () => {
  // Step 1: Define a state variable for the input value
  const [username, setUsername] = useState('');

  // Step 2: Handle form submission
  const submithandler = (e) => {
    e.preventDefault(); // Prevents page reload
    console.log("Submitted Username:", username); // Logs the current input value
    setUsername(''); // Resets the input field
  };

  return (
    <div>
      <form onSubmit={submithandler}>
        {/* Step 3: Bind the input's value to the state */}
        <input 
          value={username} // The input value reflects the current state
          onChange={(e) => setUsername(e.target.value)} // Updates state on change
          className='px-4 text-xl font-semibold' 
          type='text' 
          placeholder='Hello, enter your name' 
        />
        <button type="submit">Submit</button>
      </form>
    </div>
  );
}

export default App;

```

Npm i axios - command for the api fetching

### How to Fetech API -
```
import React, { useState } from 'react';

import axios from 'axios';

  

const App = () => {

  const [data, setData] = useState([]);

  

  const getData = async () => {

    const res = await axios.get('https://picsum.photos/v2/list');

    setData(res.data);

  };

  

  return (

    <>

      <button onClick={getData} className="bg-teal-600 text-2xl px-4 py-2 m-4 rounded">

        Get Data

      </button>

      <div className="grid grid-cols-2 gap-4">

        {data.map((e, idx) => (

          <div key={idx} className="p-2 border rounded-lg shadow-md">

            <img src={e.download_url} alt="" className="w-full h-auto rounded-lg" />

          </div>

        ))}

      </div>

    </>

  );

};

  

export default App;
```

## Tailwind Installation in React -
 [TailwindVite](https://tailwindcss.com/docs/guides/vite)

### Context Api 
It is used to centralize the data.
Eg
```App.jsx

import React, { useContext } from 'react'

import UserContext, { DataContext } from './context/UserContext'

const App = () => {

  const data = useContext(DataContext)

  console.log(data);

  return (

    <div>

      <h1>App</h1>

      <Header/>

      <Section/>

      <Footer/>

    </div>

  )

}

export default App
```

```UseContext.jsx

import React, { createContext } from 'react'

export const DataContext = createContext();

const UserContext = ({ children }) => {

    const username = "pratik"

    return (

        <DataContext.Provider value={username}>

            {children}

        </DataContext.Provider>

    )

}

export default UserContext

```
```Main.jsx

import { StrictMode } from 'react'

import { createRoot } from 'react-dom/client'

import App from './App.jsx'

import './index.css'

import UserContext from './context/UserContext.jsx'

createRoot(document.getElementById('root')).render(

<UserContext>

 <App />

</UserContext>
```

## Map & Filter-
MAP- In map array must be return. 

Filter- only print either true or false.
#### `filter`

- **Purpose**: Creates a new array with elements that pass a test (returns `true`).
- **Usage**: For selecting items based on conditions.
- **Example**:
    
    javascript
    
    Copy code
    
    `const numbers = [1, 2, 3, 4]; const evens = numbers.filter(num => num % 2 === 0); console.log(evens); // [2, 4]`
    

#### `map`

- **Purpose**: Creates a new array by transforming each element.
- **Usage**: For modifying each element in an array.
- **Example**:
    
    javascript
    
    Copy code
    
    `const numbers = [1, 2, 3]; const doubled = numbers.map(num => num * 2); console.log(doubled); // [2, 4, 6]`
    

#### Combining `filter` and `map`

Filter first, then transform:

javascript

Copy code

`const numbers = [1, 2, 3, 4, 5]; const squaredEvens = numbers.filter(num => num % 2 === 0).map(num => num ** 2); console.log(squaredEvens); // [4, 16]`


# Use State-
State in React is a way to track and manage changing data over time.
Working on objects-
```function App() {
const [count, setCount] = useState({name:"John", age:true});
  return (
    <>
    <h1>name: {count.name}</h1>
    <h1>age: {count.age.toString()}</h1>
    <button onClick={()=>setCount({...count, age:count.age+1})}>Increase Age</button>
    </>
  )
}
```

# Form Handling
It can be performed many ways 
1. ==UseRef==-
		Keep values between renders without re-rendering when updated.
		`useRef()` only returns one item. It returns an Object called `current`.
		When we initialize `useRef` we set the initial value: `useRef(0)`.

		```
		function App() {

		  const nm=useRef(null)

		  const handleSubmit=(e)=>{

	    e.preventDefault()

	      console.log(nm.current.value)
		  }
		  return (
		    <>
		
		    <form action="" onSubmit={handleSubmit}>
		
		     <input type="text" ref={nm}/>
		
		     <input type="submit" />
		
		    </form>
		
		    </>
		
		  );
		
		}```
		
2. ==React Hook Form-==
		 simplify form handling. RHF provides a `useForm` hook that manages form state and validation.
		 First install npm install react-hook-form
```const App =()=> {

  const { register, handleSubmit } = useForm();

  

  const onSubmit = async (data) => {

    console.log(data); // Log form data to verify it's working

  };

  

  return (

    <div>

      <form onSubmit={handleSubmit(onSubmit)}>

        <input {...register('email')} type="email" placeholder="Email" required />

        <input {...register('password')} type="password" placeholder="Password" required />

        <button type="submit">Login</button>

      </form>

    </div>

  );

}
```


## UseContext-
The `useContext` hook in React is used to manage shared state or data across a component tree without prop drilling.

### Dynamic Routing

Set up the main routes using `react-router-dom`.



`import React from "react"; import { BrowserRouter as Router, Routes, Route } from "react-router-dom"; import UserList from "./UserList"; import UserDetails from "./UserDetails";  const App = () => (   <Router>     <Routes>       <Route path="/" element={<UserList />} />       <Route path="/user/:id" element={<UserDetails />} />     </Routes>   </Router> );  export default App;`

---

### **2. UserList.jsx**

Create a list of users with links pointing to their respective dynamic routes.


``import React from "react"; import { Link } from "react-router-dom";  const users = [   { id: 1, name: "John Doe" },   { id: 2, name: "Jane Smith" },   { id: 3, name: "Alice Johnson" }, ];  const UserList = () => (   <div>     <h1>User List</h1>     <ul>       {users.map((user) => (         <li key={user.id}>           <Link to={`/user/${user.id}`}>{user.name}</Link>         </li>       ))}     </ul>   </div> );  export default UserList;``

---

### **3. UserDetails.jsx**

Fetch and display user details dynamically based on the route's `id` parameter.


`import React from "react"; import { useParams } from "react-router-dom";  const UserDetails = () => {   const { id } = useParams();    // Mock user details   const userDetails = {     1: { name: "John Doe", age: 28, email: "john.doe@example.com" },     2: { name: "Jane Smith", age: 32, email: "jane.smith@example.com" },     3: { name: "Alice Johnson", age: 24, email: "alice.johnson@example.com" },   };    const user = userDetails[id];    return (     <div>       {user ? (         <>           <h1>{user.name}</h1>           <p>Age: {user.age}</p>           <p>Email: {user.email}</p>         </>       ) : (         <p>User not found</p>       )}     </div>   ); };  export default UserDetails;`
### **How It Works**

1. **Dynamic Route**: `"/user/:id"` specifies a route that accepts a dynamic `id` parameter.
2. **`useParams` Hook**: Extracts the `id` from the URL (e.g., `/user/1` gives `id = 1`).
3. **Links**: `Link` components in `UserList` navigate to dynamic routes like `/user/1` or `/user/2`

# Async JS
### **Call Stack (Main Stack)**

- Executes **synchronous** code, one function at a time.
- Functions are **pushed** onto the stack when called and **popped** when completed.

`function greet() {   console.log("Hello"); } greet(); // Pushed, executed, then popped`

---
### **2. Microtask Queue (Promises)**

- Handles **Promises** and `async/await`.
- Microtasks have **higher priority** than Task Queue callbacks.

`Promise.resolve().then(() => {   console.log("Promise Task"); });`

---

### **3. Task Queue (Callback Queue)**

- Stores callbacks from `setTimeout`, `setInterval`, and other async tasks.
- Executed after all Microtasks are completed.

`setTimeout(() => {   console.log("Task Queue Callback"); }, 0);`

---
### **5 Event Loop**

- Manages the execution order:
    1. Executes the **Call Stack**.
    2. Processes the **Microtask Queue**.
    3. Processes the **Task Queue**.

`console.log("Start");  setTimeout(() => console.log("Task"), 0); Promise.resolve().then(() => console.log("Microtask"));  console.log("End");`

op-

`Start End Microtask Task`

---

### **Key Points**

1. **Synchronous code** runs first on the Call Stack.
2. **Asynchronous tasks** are handled by Web APIs, queued, and executed later.
3. **Microtasks (Promises)** have higher priority than Task Queue callbacks.

### **1. Callbacks**

A **callback** is a function passed as an argument to another function and executed after some operation is completed.

**Example:**

javascript

Copy code

`function fetchData(callback) {   setTimeout(() => {     console.log("Data fetched");     callback();   }, 1000); }  fetchData(() => {   console.log("Callback executed"); });`

---

### **2. Promises**

A **Promise** is an object that represents the eventual completion (or failure) of an asynchronous operation.

**States of a Promise:**

1. **Pending:** Initial state.
2. **Fulfilled:** Operation completed successfully.
3. **Rejected:** Operation failed.

**Example:**

javascript

Copy code

`const fetchData = new Promise((resolve, reject) => {   setTimeout(() => {     resolve("Data fetched");   }, 1000); });  fetchData   .then((data) => console.log(data)) // Runs when resolved   .catch((error) => console.log(error)); // Runs when rejected`

---

### **3. `async/await`**

`async/await` is syntactic sugar over Promises, making asynchronous code look synchronous.

**Example:**

javascript

Copy code

`async function fetchData() {   const data = await new Promise((resolve) => {     setTimeout(() => {       resolve("Data fetched");     }, 1000);   });   console.log(data); }  fetchData();`

### **4. Generators**

A **Generator** is a special type of function in JavaScript that can be paused and resumed, allowing **lazy evaluation** and more control over execution.

---

#### **Key Features:**

1. Declared using the `function*` syntax.
2. Use `yield` to pause the function and return a value.
3. The returned object is an **iterator** with a `.next()` method to resume the function.


`function* myGenerator() {   yield "Step 1";   yield "Step 2";   yield "Step 3"; }  const gen = myGenerator(); console.log(gen.next()); // { value: "Step 1", done: false } console.log(gen.next()); // { value: "Step 2", done: false } console.log(gen.next()); // { value: "Step 3", done: false } console.log(gen.next()); // { value: undefined, done: true }`


---

### **5. Web Workers**

**Web Workers** enable JavaScript to run tasks in the **background** without blocking the main thread, improving performance in complex or resource-heavy operations.

---

#### **Key Features:**

1. Run on a separate thread.
2. Communicate with the main thread using **message passing**.
3. No direct DOM access in workers (they don't share scope with the main thread).

---

`// worker.js self.onmessage = (message) => {   const result = message.data * 2; // Example: doubling the input   self.postMessage(result); };`

2. **Use the Worker in Main File:**

`const worker = new Worker('worker.js');  // Send data to the worker worker.postMessage(5);  // Receive the result from the worker worker.onmessage = (event) => {   console.log("Result from worker:", event.data); // Output: 10 };`

---

#### **Terminate a Worker:**

`worker.terminate(); // Stops the worker immediately`

---

# Redux

	 **What is Redux?**

Redux is a library for managing **state** in JavaScript applications. It is especially useful when your app has many components that need to share data. Redux helps you:

- Keep all application data (state) in a **single, centralized store**.
- Ensure state changes are **predictable** by using **actions** and **reducers**.
- Debug and trace state updates easily with tools like **Redux DevTools**.

#### **Step 1: Set up a React Project**

1. **Create a new React app:**
    
    bash
    
    Copy code
    
    `npx create-react-app redux-example --template javascript`
    
    - This creates a new React app named `redux-example`.
2. **Navigate to your project folder:**
    
    bash
    
    Copy code
    
    `cd redux-example`
    
3. **Start the app:**
    
    bash
    
    Copy code
    
    `npm start`
    
    - Your app should open in the browser at `http://localhost:3000`.

---

### **Step 2: Install Redux and React-Redux**

1. **Install Redux Toolkit and React-Redux:**
    
    bash
    
    Copy code
    
    `npm install @reduxjs/toolkit react-redux`
    
2. **Verify the installation:**
    
    - Check the `package.json` file. You should see the installed packages:
        
        json
        
        Copy code
        
        `"@reduxjs/toolkit": "^1.x.x", "react-redux": "^8.x.x"`
        

---

### **Step 3: Create the Redux Store**

1. Create a folder for your store:
    
    bash
    
    Copy code
    
    `mkdir src/app`
    
2. Create a `store.js` file inside `src/app`:
    
    bash
    
    Copy code
    
    `touch src/app/store.js`
    
3. Add the following code to `store.js`:
    
    jsx
    
    Copy code
    
    `import { configureStore } from '@reduxjs/toolkit';  // For now, the store is empty export const store = configureStore({   reducer: {}, // Reducers will be added here });`
    

---

### **Step 4: Provide the Redux Store to Your React App**

1. Open `src/index.js` (or `src/main.jsx` if using Vite).
    
2. Import the `Provider` and the `store`:
    
    jsx
    
    Copy code
    
    `import React from 'react'; import ReactDOM from 'react-dom'; import App from './App'; import { Provider } from 'react-redux'; import { store } from './app/store';  ReactDOM.render(   <Provider store={store}>     <App />   </Provider>,   document.getElementById('root') );`
    
3. **What you just did:**
    
    - Wrapped the `<App>` component with the `<Provider>` component.
    - Passed the `store` to the `<Provider>`. Now, the store is accessible to the entire app.

---

### **Step 5: Create a Redux Slice**

1. Create a folder for features:
    
    bash
    
    Copy code
    
    `mkdir src/features mkdir src/features/counter`
    
2. Create a file named `counterSlice.js` inside `src/features/counter`:
    
    `touch src/features/counter/counterSlice.js`
    
3. Add the following code to `counterSlice.js`:
    
  
    
    `import { createSlice } from '@reduxjs/toolkit';  const initialState = {   value: 0, };  const counterSlice = createSlice({   name: 'counter',   initialState,   reducers: {     increment: (state) => {       state.value += 1;     },     decrement: (state) => {       state.value -= 1;     },     incrementByAmount: (state, action) => {       state.value += action.payload;     },   }, });  export const { increment, decrement, incrementByAmount } = counterSlice.actions;  export default counterSlice.reducer;`
    
4. **What you just did:**
    
    - Defined an initial state for the counter.
    - Created three actions:
        - `increment` to increase the count.
        - `decrement` to decrease the count.
        - `incrementByAmount` to add a specific number.

---

### **Step 6: Add the Reducer to the Store**

1. Open `src/app/store.js`.
    
2. Import the counter reducer:
    
    jsx
    
    Copy code
    
    `import counterReducer from '../features/counter/counterSlice';`
    
3. Add the reducer to the store:
    
    jsx
    
    Copy code
    
    `export const store = configureStore({   reducer: {     counter: counterReducer,   }, });`
    
4. **What you just did:**
    
    - Registered the `counter` reducer with the store. The `counter` state is now managed by Redux.

---

### **Step 7: Create a Counter Component**

1. Create a file named `Counter.jsx` inside `src/features/counter`:
    
    bash
    
    Copy code
    
    `touch src/features/counter/Counter.jsx`
    
2. Add the following code to `Counter.jsx`:
    
    jsx
    
    Copy code
    
    `import React from 'react'; import { useSelector, useDispatch } from 'react-redux'; import { increment, decrement, incrementByAmount } from './counterSlice';  const Counter = () => {   const count = useSelector((state) => state.counter.value);   const dispatch = useDispatch();    return (     <div>       <h1>Counter: {count}</h1>       <button onClick={() => dispatch(increment())}>Increment</button>       <button onClick={() => dispatch(decrement())}>Decrement</button>       <button onClick={() => dispatch(incrementByAmount(5))}>Add 5</button>     </div>   ); };  export default Counter;`
    
3. **What you just did:**
    
    - Used `useSelector` to read the current count value from the store.
    - Used `useDispatch` to send actions (`increment`, `decrement`, `incrementByAmount`) to the store.

---

### **Step 8: Render the Counter Component**

1. Open `src/App.jsx`.
    
2. Import and render the `Counter` component:
    
    jsx
    
    Copy code
    
    `import React from 'react'; import Counter from './features/counter/Counter';  const App = () => {   return (     <div>       <h1>Redux Example</h1>       <Counter />     </div>   ); };  export default App;`
    
3. **What you just did:**
    
    - Added the `Counter` component to your app.

---

### **Step 9: Run the App**

1. Start the development server:
    
    bash
    
    Copy code
    
    `npm start`
    
2. You should see the counter on the screen:
    
    - Click the **Increment** and **Decrement** buttons to change the count.
    - Click the **Add 5** button to increase the count by 5.

---

### **Summary of What You Built**

- A React app with Redux managing the state.
- The counter state and logic are centralized in the Redux store.
- Components interact with the state using `useSelector` and `useDispatch`.

---

### **Key Commands Recap**

1. **Install Redux Toolkit**:
    
    bash
    
    Copy code
    
    `npm install @reduxjs/toolkit react-redux`
    
2. **Wrap `<App>` with `<Provider>`** in `index.js`.
    
3. **Create a Redux Slice** using `createSlice`.
    
4. **Add Reducers to the Store** using `configureStore`.
    
5. **Access State** using `useSelector` and **Dispatch Actions** using `useDispatch`.
    

Enjoy exploring Redux! 😊

4o

##### You said:

redux diagram

###### ChatGPT said:

ChatGPT

Here’s a **Redux Workflow Diagram** to help visualize how Redux works in a React application.

---

### **Redux Workflow Diagram**

plaintext

Copy code

`[React Components] ----> [Dispatch Action] ----> [Redux Store] ----> [State Updates]       |                                 |                        |       V                                 V                        V [useSelector (Read State)] <-----> [Reducers (Update State)] <-----> [Store (Global State)]`

---

### **Explanation of the Workflow**

1. **React Components**:
    
    - React components are where your UI and user interactions exist.
    - These components can dispatch actions to update the state (using `useDispatch`).
2. **Dispatch Action**:
    
    - Components interact with the Redux store by dispatching **actions** (which are plain JavaScript objects describing a change you want to make).
    - Actions can be dispatched using `dispatch(action)`.
3. **Redux Store**:
    
    - The Redux store holds the **global state** of your application.
    - The store is initialized with a root reducer that contains all the app's slices.
4. **Reducers**:
    
    - A **reducer** is a function that receives the current state and an action, then returns a new state.
    - When an action is dispatched, the reducer processes it and updates the state accordingly.
    - Reducers are pure functions, meaning they only depend on their inputs (state and action) and do not have side effects.
5. **State Updates**:
    
    - Once the action is processed, the **state** is updated in the Redux store.
    - Components that are connected to the store using `useSelector` are automatically re-rendered with the updated state.


## **State Management using recoil**

**Recoil** is a state management library for React that provides a more flexible and efficient way to manage state compared to **Context API** and **Redux**. It is designed to be simpler, more scalable, and better suited for managing complex state.

- `useRecoilState`: Read and write atom state.
- `useRecoilValue`: Read atom/selector state.
- `useSetRecoilState`: Write atom state without reading it.
- `useResetRecoilState`: Reset atom to its default value.

### **1. RecoilRoot**

- **What**: It acts as a provider, enabling the use of Recoil throughout your React component tree.
- **Why**: It is necessary to wrap your app with `<RecoilRoot>` for Recoil to work.

#### Example:
jsx

`import { RecoilRoot } from 'recoil';  function App() {   return (     <RecoilRoot>       <YourComponents />     </RecoilRoot>   ); }`

---
### **2. Atoms**

- **What**: The basic unit of state in Recoil, like a global state variable.
- **Why**: Atoms store data that can be shared across components, and when an atom's value changes, only the components using it will re-render.
#### Example:
jsx

`import { atom } from 'recoil';  const countState = atom({   key: 'countState', // Unique ID for this atom   default: 0, // Initial value });`

---

### **3. Selectors**

- **What**: A derived state that computes its value based on atoms or other selectors.
- **Why**: Use selectors for reusable or computed state, like filtering or transforming data.

#### Example:
jsx

`import { selector } from 'recoil'; import { countState } from './atoms';  const doubledCount = selector({   key: 'doubledCount', // Unique ID   get: ({ get }) => get(countState) * 2, // Computed value });`

---

### **4. Recoil Hooks**

- **What**: Hooks provided by Recoil to interact with atoms and selectors.
- **Why**: These hooks allow you to read, write, or reset Recoil state.

#### Common Recoil Hooks:

- **`useRecoilState`**: Read and write atom state.
- **`useRecoilValue`**: Read atom or selector state.
- **`useSetRecoilState`**: Write atom state without reading it.
- **`useResetRecoilState`**: Reset atom to its default value.

#### Example:

jsx
`import { useRecoilState } from 'recoil'; import { countState } from './atoms';  function Counter() {   const [count, setCount] = useRecoilState(countState);    return (     <div>       <button onClick={() => setCount(count - 1)}>-</button>       {count}       <button onClick={() => setCount(count + 1)}>+</button>     </div>   ); }`

---

### **5. Asynchronous Selectors (Optional)**

- **What**: Selectors that fetch or compute data asynchronously.
- **Why**: Useful for handling API calls or other asynchronous logic in a centralized way.
#### Example:

jsx
`import { selector } from 'recoil';  const asyncData = selector({   key: 'asyncData',   get: async () => {     const response = await fetch('https://jsonplaceholder.typicode.com/posts');     return response.json();   }, });`

## Example-
App.jsx
```import React from 'react';  
import { RecoilRoot } from 'recoil'; // RecoilRoot to provide the Recoil context  
import Counter from './components/Counter'; // Import the Counter component  
  
function App() {  
  return (  
      <RecoilRoot>        <Counter />  
      </RecoilRoot>  
  );  
}  
  
export default App;
```

atom.jsx
```import {atom, selector} from 'recoil';  
  
// Define the atom (shared state)  
export const countState = atom({  
    key: 'countState', // Unique ID for this atom  
    default: 0,        // Initial value  
});  
  
export const evenselector = selector({  
    key: 'evenselector',  
    get: ({get}) => {  
        const count = get(countState);  
        return count % 2 === 0 ? 'Even' : 'Odd';  
    },  
})
```

counter.jsx
```import React from 'react';  
import {useRecoilState, useRecoilValue} from 'recoil';  
import { countState, evenselector } from '../recoil/atom/atom.jsx'; // Import the atom  
  
// Counter component  
function Counter() {  
    // Access the state and setter using useRecoilState  
    const [count, setCount] = useRecoilState(countState);  
  
    return (  
        <div style={{ textAlign: 'center', marginTop: '50px' }}>  
            <h1>Counter: {count}</h1>  
            <button onClick={() => setCount(count - 1)} style={{ marginRight: '10px' }}>  
                Decrement  
            </button>  
            <button onClick={() => setCount(count + 1)}>Increment</button>  
            <UseEvenCount /> {/* Add EvenOrNot component */}  
        </div>    );  
}  
  
// Custom hook to use evenselector  
function UseEvenCount() {  
    const count = useRecoilValue(evenselector);  
    return count;  
}  
  
export default Counter;
```

## Advance
### **1. `loadable`**:

- **Purpose**: Used to manage **asynchronous state** like API calls or other data-fetching operations in Recoil.
- **How it works**: It helps to track the status of an async operation (loading, success, error) and store it in state. You can use it to handle things like fetching data and showing loading indicators or error messages.

### **2. `atomFamily`**:

- **Purpose**: Creates a **group of atoms** (state variables) that are similar but can have **different values** based on a unique key or parameter.
- **How it works**: It's useful when you need to store a set of related states, such as managing data for multiple users or items, where each state is distinct but follows the same structure.

### **3. `selectorFamily`**:

- **Purpose**: Similar to `atomFamily`, but for **derived state**. It allows you to create selectors (computed values) that depend on a unique key or parameter.
- **How it works**: It's used when you need to compute or transform data for different keys (e.g., filtering or sorting a list based on a specific parameter).

**Code Eg**
https://github.com/100xdevs-cohort-2/7.4

