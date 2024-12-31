Node.JS runtime | HTTP-

- what is ECMAScript?
- What is JavaScript?
- What is Node JS?
- What is Bun?

### **What is ECMAScript?**

ECMAScript (ES) is the standardized scripting language specification that serves as the foundation for JavaScript. It is maintained by ECMA International, under the Technical Committee 39 (TC39). ECMAScript defines the core syntax, types, objects, and functionality that JavaScript implements.

### **What is JavaScript?**

JavaScript is a high-level, interpreted programming language primarily used for building interactive and dynamic web applications. It is built on ECMAScript standards but adds APIs like DOM manipulation and event handling for working with web pages.
### **What is Node.js?**

Node.js is a ==runtime environment== that allows developers to ==execute JavaScript code outside the browse==r, making it possible to use JavaScript for backend/server-side development.

Key features:

- **Asynchronous I/O**: Non-blocking, event-driven architecture for handling multiple requests efficiently.
- **Built-in Modules**: Provides modules for handling HTTP, file systems, streams, and more.
- **Package Manager (npm)**: Facilitates dependency management for JavaScript projects.

### **What is Bun?**

Bun is a modern JavaScript runtime that competes with Node.js and Deno. It is built for speed, efficiency, and modern development needs.

Key features:

- **Performance**: ==Written in Zig==, it claims to outperform Node.js in script execution, startup time, and package management.
- **Integrated Tools**: Includes a bundler, transpiler, and npm-compatible package manager.
- **Use Case**: Designed to handle web development, server-side scripting, and more, with emphasis on developer productivity.

#### HTTP Server
Most common use is to frontend talk to its backend.

### ==Zod & Auth==
**Zod** is a TypeScript-first schema validation library that allows you to define, parse, and validate data structures. It's lightweight, easy to use, and eliminates boilerplate by combining schema definition and validation in a single step.

---

### **Key Features**

1. **Schema Definition**: Define the shape of data with intuitive, chainable methods.
2. **Validation**: Validate data at runtime to ensure it conforms to the schema.
3. **Type Inference**: Automatically infer TypeScript types from schemas.
4. **Composability**: Nest schemas to handle complex data structures.
5. **Error Handling**: Provides detailed error messages for invalid data.

---

### **Installation**

bash

Copy code

`npm install zod`

#### 1. **Creating a Schema**

`import { z } from "zod";  const UserSchema = z.object({   name: z.string(),   age: z.number().min(18), // Must be at least 18 });  const data = { name: "Alice", age: 25 };`

### Authentications
1) Hashing
2) Encryption
3) Json Web Tokens (JWT)
4) Local Storage

**JWT** (JSON Web Token) is a compact, URL-safe token format used to securely transmit information between parties as a JSON object. It is commonly used for **authentication** and **authorization** in modern web applications.

---

### **Structure of a JWT**

A JWT consists of three parts, separated by dots (`.`):


`HEADER.PAYLOAD.SIGNATURE`

#### **1. Header**

The header typically contains two parts:

- **Algorithm** used for signing (e.g., HS256, RS256).
- **Type** of token, which is `JWT`.


`{   "alg": "HS256",   "typ": "JWT" }`

#### **2. Payload**

The payload contains the **claims** — the information you want to transmit. Common claims include:

- **Registered claims**: Standardized fields (e.g., `sub`, `iat`, `exp`).
- **Public claims**: Custom data (e.g., `userId`, `role`).
- **Private claims**: Data shared between parties.


`{   "sub": "1234567890",      // Subject (user ID)   "name": "John Doe",       // Public claim   "admin": true,            // Custom claim   "iat": 1516239022,        // Issued at   "exp": 1516242622         // Expiry time }`

#### **3. Signature**

The signature ensures that the token hasn't been tampered with. It is created by encoding the **header** and **payload** and signing them using a secret key or private key.

`HMACSHA256(   base64UrlEncode(header) + "." + base64UrlEncode(payload),   secret )`

---
### **How JWT Works**

JWT is commonly used for **stateless authentication**. Here's the flow:

1. **Client Logs In**
    
    - The user sends credentials (e.g., username/password) to the server.
2. **Server Generates JWT**
    
    - If credentials are valid, the server generates a JWT containing user information (e.g., user ID, role) and signs it with a **secret key**.
3. **Client Stores JWT**
    
    - The client receives the JWT and stores it (e.g., in **localStorage** or **cookies**).
4. **Client Sends JWT**
    
    - For each subsequent request, the client sends the JWT in the **Authorization header**:
        
        makefile
        
        Copy code
        
        `Authorization: Bearer <token>`
        
5. **Server Verifies JWT**
    
    - The server verifies the token using the secret key:
        - Decodes the header and payload.
        - Recalculates the signature and compares it.
        - Checks claims like `exp` (expiration) to ensure the token is still valid.
6. **Access Granted**
    
    - If the token is valid, the server processes the request and sends the response.


## Week -9
### SWR-
Library lets u creates custom hooks.(React library created by **Vercel** for efficient data fetching)

```
npm install swr
```
Eg
```
import useSWR from 'swr';

// Fetcher function
const fetcher = (url) => fetch(url).then((res) => res.json());

function App() {
    const { data, error, isLoading } = useSWR('https://jsonplaceholder.typicode.com/posts', fetcher);

    if (isLoading) return <div>Loading...</div>;
    if (error) return <div>Error: {error.message}</div>;

    return (
        <ul>
            {data.map((post) => (
                <li key={post.id}>{post.title}</li>
            ))}
        </ul>
    );
}

export default App;

```

# Week-10 Databases

Databases are classified into different types based on their structure, data storage, and usage. Below are the common types of databases:

---

### **1. Relational Databases (RDBMS)**

- **Structure:** Stores data in rows and columns (tables).
- **Key Features:**
    - Follows ACID (Atomicity, Consistency, Isolation, Durability) properties.
    - Uses SQL for queries.
    - Relationships between tables using primary and foreign keys.
- **Examples:**
    - MySQL
    - PostgreSQL
    - SQLite
    - Microsoft SQL Server
    - Oracle Database
- **Best For:** Applications requiring structured data and complex queries.

---

### **2. NoSQL Databases**

- **Structure:** Non-tabular and more flexible for unstructured or semi-structured data.
- **Types of NoSQL Databases:**
    - **Document-Oriented:** JSON-like documents (e.g., MongoDB, CouchDB).
    - **Key-Value Stores:** Key-value pairs (e.g., Redis, DynamoDB).
    - **Column-Family Stores:** Data stored in columns (e.g., Apache Cassandra, HBase).
    - **Graph Databases:** Nodes and edges for relationships (e.g., Neo4j, ArangoDB).
- **Best For:** Big data, real-time analytics, unstructured data.

---

### **3. In-Memory Databases**

- **Structure:** Stores data in memory instead of disk for faster access.
- **Examples:**
    - Redis
    - Memcached
- **Best For:** Caching, session storage, real-time analytics.

---

### **7. Graph Databases**

- **Structure:** Focuses on relationships between data using nodes and edges.
- **Examples:**
    - Neo4j
    - Amazon Neptune
- **Best For:** Social networks, recommendation systems, and fraud detection.

---

### **8. Cloud Databases**

- **Structure:** Hosted on cloud platforms with high scalability and reliability.
- **Examples:**
    - Amazon RDS
    - Google Cloud Spanner
    - Microsoft Azure Cosmos DB
- **Best For:** Modern web apps, scalability, and on-demand access.
 ---

==To access Postgresql online use Neotech website.==
==Use PG library to connect interact with your DB through Express JS==
```
npm i pg
```

Eg of creating DB
```
import { Client } from 'pg';  
const showDatabases = async () => {  
    const client = new Client({  
        connectionString: 'postgresql://neondb_owner:daNHuny6R2mE@ep-weathered-grass-a50nxxs3.us-east-2.aws.neon.tech/neondb?sslmode=require'  
    });  
    try {  
        await client.connect();  
        const result = await client.query('SELECT datname FROM pg_database WHERE datistemplate = false');  
        console.log('Databases:', result.rows);  
    } catch (err) {  
        console.error('Error retrieving databases:', err);  
    } finally {  
        await client.end();  
    }  
};  
  
showDatabases();
```
