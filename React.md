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
4. **Set Up Routes in App Component**: Use `Routes` and `Route` components with the `element` prop.
5. **Add Navigation Links**: Use `<Link>` components for easy navigation if needed.





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