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

