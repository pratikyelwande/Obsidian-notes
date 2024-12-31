- Node.js is a runtime environment that allows you to execute JavaScript code outside the browser.
- Node JS is a single threaded architecture it will handle only one request at a time it will not perform CPU intensive tasks in backend.
- Create basic server-
		```
	const http = require('node:http');
		
		// Create a local server to receive data from
		const server = http.createServer((req, res) => {
		  res.writeHead(200, { 'Content-Type': 'application/json' });
		  res.end(JSON.stringify({
		    data: 'Hello World!',
		  }));
		});
		
		server.listen(8000);

- When we create code it will not reflect changes in running state so we have to reload the server to avoid that we will use NODEMON.
- Npm i nodemon
- PS D:\React\NodeJS> npx nodemon .\script.js

	## ==HTTP status code-==
- **100 Continue**: The server acknowledges the request and asks the client to continue.
- **101 Switching Protocols**: Indicates that the protocol is being switched as requested by the client.
- ### **2xx: Success**

- **200 OK**: The request was successful.
    
    `res.statusCode = 200; res.end('Success');`
    
- **201 Created**: The request resulted in a new resource being created.
- `res.writeHead(201, { 'Content-Type': 'application/json' }); res.end(JSON.stringify({ message: 'Resource created' }));`

- The HTTP 202 status code indicates that the server has received the request and has accepted it for processing, but the processing is not yet complete.
- 203 : Non-Authoritative Information
- - The request was processed successfully.
	 The response might not be exactly what the origin server sent but was altered by an intermediary (e.g., a proxy or cache).

- **204 No Content**: The server successfully processed the request but returns no content.

### **3xx: Redirection**

- **301 Moved Permanently**: The resource has been moved to a new URL.
- **302 Found**: Temporary redirection and same as **307** 
 
    `res.writeHead(302, { Location: '/new-url' }); res.end();`
    
- **304 Not Modified**: The resource has not been modified since the last request.
- **308: Permanent Redirect** 

---

### **4xx: Client Errors**

- **400 Bad Request**: The request cannot be processed due to client-side errors.
    
    `res.writeHead(400, { 'Content-Type': 'text/plain' }); res.end('Bad Request');`
    
- **401 Unauthorized**: Authentication is required.
- **403 Forbidden**: The client does not have permission to access the resource.
- **404 Not Found**: The requested resource could not be found.
 
    `res.writeHead(404, { 'Content-Type': 'text/plain' }); res.end('Not Found');`
    
---
### **5xx: Server Errors**

- **500 Internal Server Error**: A generic error occurred on the server.

    `res.writeHead(500, { 'Content-Type': 'text/plain' }); res.end('Internal Server Error');`
    
- **502 Bad Gateway**: The server received an invalid response from an upstream server.
- **503 Service Unavailable**: The server is temporarily unavailable.

### **Comparison Table**

|**Aspect**|**Node.js**|**Express.js**|
|---|---|---|
|**Type**|Runtime environment|Web application framework|
|**Purpose**|Execute JavaScript on the server|Simplifies building web applications|
|**Level**|Low-level|Higher-level abstraction|
|**Routing**|Manual implementation required|Built-in routing system|
|**Middleware**|Custom logic needed|Built-in middleware support|
|**Learning Curve**|Steeper for beginners|Easier and faster to learn|
|**Use Case**|Custom server-side solutions|Web apps and REST APIs|
# Express JS

- What is middleware function?
	a function that accept request response & next parameters in it.
	**Middleware functions** in Express.js are functions that execute during the **request-response cycle**.
	- **Modify requests** or **responses** (e.g., parsing JSON, adding headers).
	- Execute **code** before the route handler runs.
	- **End the request** (e.g., sending an error response).
	- Call the next middleware function in the chain using `next()`.
```
app.use((req, res, next) => {
  console.log('Middleware executed');
  next(); // Pass control to the next middleware/route handler
});
```
##### **What is a Session?**

A **session** in Express.js is used to store data about a user across multiple requests. Unlike **cookies**, sessions store data on the server-side, and the client only receives a session identifier (typically stored in a cookie).

- **Purpose**: Sessions are used to persist user data (like login status) between HTTP requests.
- **Usage**: Commonly used for user authentication, remembering preferences, or storing temporary data during a user's visit.

---

##### **How to Install Session Middleware in Express.js?**

To handle sessions in Express.js, you need to install `express-session` middleware.

1. **Install the package**:

    `npm install express-session`
    
2. **Set up session in your Express app**:
   
    
    ``const express = require('express'); const session = require('express-session'); const app = express();  // Set up session middleware app.use(session({   secret: 'your-secret-key', // Secret to sign the session ID cookie   resave: false,  // Don't save session if it wasn't modified   saveUninitialized: true,  // Save a new session even if it's empty   cookie: { secure: false }  // Set to true if using HTTPS }));  app.get('/', (req, res) => {   // Store data in session   req.session.user = 'John Doe';   res.send('Session Data Set'); });  app.get('/profile', (req, res) => {   // Access session data   res.send(`Hello, ${req.session.user}`); });  app.listen(3000, () => console.log('Server running on port 3000'));``

### Connect-Flash in Express.js

**Connect-Flash** is a simple and lightweight flash messaging middleware for Express.js that allows you to store and display messages across requests. Flash messages are typically used for notifications such as success, error, or information messages after a user performs some action.

---

### **How to Install Connect-Flash**

1. **Install Connect-Flash** using npm:
   
    `npm install connect-flash`
    
2. **Install Express-session** (Required for storing the flash messages in the session):

    `npm install express-session`
---
### **Basic Usage**

1. **Set up the middleware:**
    - Flash messages are stored in the session, so you'll need to set up `express-session`.
    - Then, use `connect-flash` to handle the messages.

`const express = require('express'); const session = require('express-session'); const flash = require('connect-flash');  const app = express();  // Set up session and flash middleware app.use(session({   secret: 'your-secret-key',   resave: false,   saveUninitialized: true }));  app.use(flash()); // Initialize flash middleware  // Body parsing middleware (optional, for form handling) app.use(express.urlencoded({ extended: true })); app.use(express.json());  // Example route to set a flash message app.get('/set-flash', (req, res) => {   req.flash('info', 'Flash message set!');   res.redirect('/show-flash'); });  // Example route to display the flash message app.get('/show-flash', (req, res) => {   const messages = req.flash('info'); // Retrieve the flash message   res.send(messages.length ? messages : 'No flash messages'); });  app.listen(3000, () => console.log('Server running on port 3000'));`

### **CORS (Cross-Origin Resource Sharing) in Express.js**

#### **What is CORS?**

CORS is a security feature implemented by web browsers to control how resources (like APIs) on one domain can be accessed by web pages on another domain. By default, web pages can only make requests to the same domain unless explicitly allowed by the server.

**CORS** allows servers to specify which origins (domains) are permitted to access resources on the server.

---

### **How to Install CORS in Express.js?**

1. **Install CORS package** using npm:

    `npm install cors`
    
2. **Import and Use CORS in your Express App**:
    
    `const express = require('express'); const cors = require('cors'); // Import cors  const app = express();  // Use CORS middleware app.use(cors());  // This will allow all origins by default  // Example Route app.get('/', (req, res) => {   res.send('CORS enabled!'); });  app.listen(3000, () => {   console.log('Server running on port 3000'); });`
---
### **What is a Cookie?**

A **cookie** is a small piece of data that is stored on the client-side (in the user's browser) and sent back to the server with every subsequent request. Cookies are often used to store user-specific information, such as:

- Session data
- Authentication tokens
- User preferences

---

### **Installing Cookie Middleware**

To work with cookies in Express.js, you need to install the `cookie-parser` middleware.

**1. Install `cookie-parser`:**

`npm install cookie-parser`

---

### **Using `cookie-parser` in Express.js**

**2. Import and use `cookie-parser`:**

``const express = require('express'); const cookieParser = require('cookie-parser');  const app = express();  // Use cookie-parser middleware app.use(cookieParser());  // Route to set a cookie app.get('/set-cookie', (req, res) => {   // Set a cookie   res.cookie('username', 'Pratik');   res.send('Cookie is set!'); });  // Route to get the cookie app.get('/get-cookie', (req, res) => {   // Access a cookie   const username = req.cookies.username;   res.send(`Hello ${username}`); });  // Start the server app.listen(3000, () => {   console.log('Server is running on port 3000'); });``

---

### **Cookie Methods in Express:**

1. **Set Cookies**  
    To set a cookie, use `res.cookie(name, value, [options])`:
   
    `res.cookie('key', 'value');`
    
2. **Get Cookies**  
    To get cookies, use `req.cookies`:
    
    `const value = req.cookies['key'];`
    
3. **Delete Cookies**  
    To delete a cookie, use `res.clearCookie(name)`:

    `res.clearCookie('key');`

### **Morgan in Express.js**

#### **What is Morgan?**

- **Morgan** is a popular HTTP request logger middleware for **Node.js** and **Express.js** applications.
- It logs details about incoming HTTP requests (such as request method, URL, response time, etc.) to the console or to a file.
- Useful for debugging, monitoring, and logging request details in development or production environments.

---

#### **How to Install Morgan**

1. **Install via npm**: Run the following command in your project directory:

    `npm install morgan`
    
2. **Import Morgan** in your `app.js` or `server.js` file:

    `const morgan = require('morgan');`
    

---
#### **How to Use Morgan in Express**

1. **Basic Usage** (Logging to the console):
 
    `const express = require('express'); const morgan = require('morgan'); const app = express();  // Use morgan for logging HTTP requests app.use(morgan('tiny')); // 'tiny' is a predefined logging format  app.get('/', (req, res) => {   res.send('Hello, World!'); });  app.listen(3000, () => {   console.log('Server is running on port 3000'); });`

### **Dynamic Routing in Express.js**

#### **What is Dynamic Routing?**

Dynamic routing in **Express.js** allows you to define routes with **parameters** that can accept **variable values**. These routes are useful when you want to handle requests where parts of the URL change (e.g., user IDs, product names).

#### **Example of Dynamic Routing:**

``const express = require('express'); const app = express();  // Route with dynamic parameter (e.g., user ID) app.get('/user/:id', (req, res) => {   const userId = req.params.id;  // Access the dynamic part (user ID)   res.send(`User ID: ${userId}`); });  // Route with multiple dynamic parameters app.get('/product/:category/:productId', (req, res) => {   const { category, productId } = req.params;   res.send(`Category: ${category}, Product ID: ${productId}`); });  // Start the server app.listen(3000, () => console.log('Server is running on port 3000'));``


### **EJS in Express.js: Notes**

#### **What is EJS?**

EJS (Embedded JavaScript) is a **templating engine** for Node.js and Express.js. It allows you to embed JavaScript code into your HTML, making it easier to generate dynamic content.

- **Purpose**: It helps render dynamic HTML views by allowing data to be injected into the HTML templates.
- **Usage**: It simplifies the process of building complex views where content changes based on user interactions or server-side data.

---

### **How to Install EJS in Express.js**

#### **Step 1**: Initialize your project (if not done already)


`npm install ejs`

---
### **How to Use EJS in Express.js**

1. **Set up EJS as the View Engine**: In your Express app, you need to tell it to use EJS for rendering views.
   
    `const express = require('express'); const app = express();  // Set EJS as the view engine app.set('view engine', 'ejs');`
    
2. **Create a Views Folder**: Create a folder named `views` in the root of your project to store your `.ejs` files.
    
3. **Create an EJS Template**: Inside the `views` folder, create an `.ejs` file, e.g., `index.ejs`.
    
    html
    `<!-- views/index.ejs --> <h1>Welcome, <%= name %>!</h1>`
    
4. **Render the EJS Template**: In your route handler, use `res.render()` to render the template and pass dynamic data to it.
    
    javascript
    
    `app.get('/', (req, res) => {   const userName = 'Pratik';   res.render('index', { name: userName }); });`
    

---

### **Example: Basic Express App with EJS**

`const express = require('express'); const app = express();  // Set EJS as the view engine app.set('view engine', 'ejs');  // Route with dynamic content app.get('/', (req, res) => {   const userName = 'Pratik';   res.render('index', { name: userName }); });  // Start the server app.listen(3000, () => {   console.log('Server is running on port 3000'); });`

#### **index.ejs** (in the views folder):
html
`<!DOCTYPE html> <html lang="en"> <head>   <meta charset="UTF-8">   <title>Dynamic EJS</title> </head> <body>   <h1>Welcome, <%= name %>!</h1> </body> </html>`

### **Form Handling with EJS in Express.js**
index.ejs
`<!-- views/index.ejs -->  
<!DOCTYPE html>  
<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>Form Handling with EJS</title>  
</head>  
<body>  
<h1>Submit Your Info</h1>  
<form action="/submit" method="GET">  
    <label for="name">Name:</label>  
    <input type="text" id="name" name="name" required><br><br>  
    <label for="email">Email:</label>  
    <input type="email" id="email" name="email" required><br><br>  
    <button type="submit">Submit</button>  
</form>  
</body>  
</html>`
app.js
```
const express = require('express');  
const app = express();  
  
// Set EJS as the view engine  
app.set('view engine', 'ejs');  
app.use(express.json());  
app.use(express.urlencoded({extended: true}));  
  
  
// Define the route for the form  
app.get('/', (req, res) => {  
    res.render('index');  // Render 'index.ejs' template  
});  
  
// Handle the form submission  
app.get('/submit', (req, res) => {  
    console.log(req.query);  
    res.send("working")  
  
});  
  
// Start the server  
app.listen(3000, () => {  
    console.log('Server running on http://localhost:3000');  
});
```

### Create data in mongo in express-
```const express = require('express');  
const mongoose = require('mongoose');  
const app = express();  
  
// Connect to MongoDB  
mongoose.connect('mongodb://localhost:27017/mydatabase')  
  .then(() => console.log('Connected to MongoDB...'))  
  .catch(err => console.log('Could not connect to MongoDB... ', err));  
  
// Create the User schema  
const userSchema = mongoose.Schema({  
  username: String,  
  password: String,  
  email: String  
});  
  
// Create a mongoose model from the schema  
const User = mongoose.model('User', userSchema);  
  
app.get('/', (req, res) => {  
  res.send('Welcome to MongoDB Atlas!');  
});  
  
// Route to create a User  
app.get('/create', async (req, res) => {  
 let createuser=await User.create({  
    username: 'Guest',  
    password: 'Password123',  
    email: 'guest@example.com'  
  })  
  console.log("user created...");  
  res.send(createuser)  
});  
  
// Route to get all Users  
app.get('/users', (req, res) => {  
  User.find({})  
    .then(users => {  
      res.status(200).send(users);  
    })  
    .catch(err => {  
      console.log(err);  
      res.status(500).send(err);  
    });  
});  
  
app.listen(3000, () => {  
  console.log('Server is running on port 3000...');  
});
```

### Reading User Data from mongo-
```
const express = require('express');  
const mongoose = require('mongoose');  
const app = express();  
  
// Connect to MongoDB  
mongoose.connect('mongodb://localhost:27017/mydatabase')  
    .then(() => console.log('Connected to MongoDB...'))  
    .catch(err => console.log('Could not connect to MongoDB... ', err));  
  
// Create the User schema  
const userSchema = mongoose.Schema({  
    username: String,  
    password: String,  
    email: String  
});  
  
// Create a mongoose model from the schema  
const User = mongoose.model('User', userSchema);  
  
app.get('/', (req, res) => {  
    res.send('Welcome to MongoDB Atlas!');  
});  
  
// Route to read all users  
app.get("/read", async (req, res) => {  
    try {  
        const users = await User.find(); // Fetch all users from the database  
        res.status(200).send(users);  
    } catch (err) {  
        console.error('Error reading users:', err);  
        res.status(500).send({ message: "Error retrieving users", error: err });  
    }  
});  
  
app.listen(3000, () => {  
    console.log('Server is running on port 3000...');  
});
```

### Insert Many -
```const express = require('express');  
const app = express();  
const userModel= require('./models/user');  
app.use(express.json());  
const dummy=[  
    {        "username": "john_doe",  
        "name": "John Doe",  
        "age": "30"  
    },  
    {  
        "username": "jane_smith",  
        "name": "Jane Smith",  
        "age": "25"  
    },  
    {  
        "username": "mark_twain",  
        "name": "Mark Twain",  
        "age": "40"  
    },  
    {  
        "username": "lucy_brown",  
        "name": "Lucy Brown",  
        "age": "35"  
    },  
    {  
        "username": "peter_parker",  
        "name": "Peter Parker",  
        "age": "28"  
    }  
]  
  
app.get("/",(req,res)=>{  
    res.send("Welcome to our home page!")  
});  
  
app.get("/createmany",async (req,res)=>{  
 let data=   await  userModel.insertMany(dummy);  
  res.send(data)  
});  
  
app.listen(3000);
```

