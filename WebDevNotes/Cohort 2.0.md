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


# ORM

### What is ORM's?
**ORM (Object-Relational Mapping)** is a technique that allows developers to interact with a database using **object-oriented programming** instead of writing SQL queries.

### Key Points:

- Maps database tables to **classes** and rows to **objects**.
- Simplifies CRUD (Create, Read, Update, Delete) operations.
- Abstracts SQL queries into **method calls**.

### Advantages:

1. **Easier to Use**: Write code in your language of choice (e.g., JavaScript, Python).
2. **Less Error-Prone**: Avoid raw SQL queries, reducing syntax mistakes.
3. **Database Agnostic**: Easily switch between database systems (e.g., PostgreSQL, MySQL).

### Examples:

- **Prisma** (JavaScript/TypeScript)
- **TypeORM** (JavaScript/TypeScript)
- **Hibernate** (Java)
- **SQLAlchemy** (Python)

### **Prisma Notes**

**Prisma** is a next-generation **ORM** that simplifies database operations for modern development. It supports **PostgreSQL**, **MySQL**, **SQLite**, and more.

---

### **Why Use Prisma?**

1. **Type-Safe**: Autocompletes and validates queries based on your schema.
2. **Powerful**: Works seamlessly with relational databases.
3. **Easy Migration**: Built-in schema migrations.

---

### **Steps to Install and Use Prisma with PostgreSQL**

#### 1. **Install Prisma**

Make sure you have Node.js and npm installed.

bash

`npm install prisma --save-dev npm install @prisma/client`

#### 2. **Initialize Prisma**

Create the Prisma setup in your project.

bash

`npx prisma init`

This generates:

- `prisma/schema.prisma` file (to define your database schema).
- `.env` file (to store your database connection string).

---

#### 3. **Set up PostgreSQL**

- Install PostgreSQL and create a database (e.g., `mydb`).
- Update the `.env` file with your connection string:

env

`DATABASE_URL="postgresql://username:password@localhost:5432/mydb"`

---

#### 4. **Define the Schema**

Update `prisma/schema.prisma` to define your data models:

prisma

```
// prisma/schema.prisma  
datasource db {  
  provider = "postgresql"  
  url      = env("DATABASE_URL")  
}  
generator client {  
  provider = "prisma-client-js"  
}  
model User {  
  id    Int    @id @default(autoincrement())  
  name  String  
  email String @unique  
}
```

---

#### 5. **Migrate Your Database**
The **"Migrate Your Database"** step in Prisma is used to ensure that the database schema aligns with the models you define in your Prisma schema file (`schema.prisma`).
Generate and apply the database schema:

bash
`npx prisma migrate dev --name init`

---

#### 6. **Query Your Database**

Use Prisma Client in your application.

javascript

```
const { PrismaClient } = require('@prisma/client');  
  
// Create an instance of PrismaClient  
const prisma = new PrismaClient();  
  
async function main() {  
    try {  
        // Try to fetch users from the database  
        const users = await prisma.user.findMany();  
  
        if (users.length === 0) {  
            console.log('No users found in the database.');  
        } else {  
            console.log('Users fetched successfully:', users);  
        }  
  
        // Optionally, create a user to check if insert works  
        const newUser = await prisma.user.create({  
            data: {  
                name: 'Test User',  
                email: 'testuser@example.com',  
            },  
        });  
  
        console.log('User created successfully:', newUser);  
    } catch (error) {  
        console.error('Error connecting to the database:', error);  
    } finally {  
        // Disconnect Prisma client  
        await prisma.$disconnect();  
    }  
}  
  
// Execute the main function  
main();
````

---

### **Run the App**

1. Start PostgreSQL.
2. Run your Node.js script:
bash

`node app.js`


## AWS Architecture
## Cloudflare Worker
To deploy an Express.js project on **Cloudflare Workers**, you need to adapt your code because Cloudflare Workers do not natively support Node.js APIs. Instead, they run in a **Service Worker-like environment**. You can use libraries like `@honojs` (a lightweight framework similar to Express) to make the transition smoother.

Here's a step-by-step guide:

---

### **1. Install Cloudflare Workers CLI**

The `wrangler` CLI is used to manage and deploy Cloudflare Workers.

1. Install `wrangler` globally:
    
    bash
    
    Copy code
    
    `npm install -g wrangler`
    
2. Verify installation:
    
    bash
    
    Copy code
    
    `wrangler --version`
    
3. Log in to your Cloudflare account:
    
    bash
    
    Copy code
    
    `wrangler login`
    

---

### **2. Create a New Worker Project**

1. Create a new project:
    
    bash
    
    Copy code
    
    `wrangler init my-worker cd my-worker`
    
2. Choose **"JavaScript"** or **"TypeScript"** when prompted.
    
3. Install dependencies for Express-like behavior:
    
    bash
    
    Copy code
    
    `npm install hono`
    

---

### **3. Adapt Your Express.js Code**

Cloudflare Workers don't use `http` or `express`, but you can use Hono to write code similar to Express.js.

Here’s an example:

**`src/index.js`**:

javascript

Copy code

`import { Hono } from 'hono';  const app = new Hono();  // Define routes app.get('/', (c) => c.text('Hello, Cloudflare Workers!')); app.get('/api', (c) => c.json({ message: 'API endpoint' }));  // 404 handler app.all('*', (c) => c.text('Not Found', 404));  export default app;`

---

### **4. Update `wrangler.toml`**

Ensure your `wrangler.toml` file is set up correctly:

toml

Copy code

`name = "my-worker" main = "src/index.js" compatibility_date = "2025-01-02"  # Replace with the current date`

---

### **5. Test Locally**

Use `wrangler` to run the Worker locally:

bash

Copy code

`wrangler dev`

Open your browser and visit `http://localhost:8787` to see your Worker in action.

---

### **6. Deploy to Cloudflare**

Once you're satisfied with your Worker, deploy it to Cloudflare:

bash

Copy code

`wrangler publish`

You’ll get a public URL like `https://my-worker.<your-workers-subdomain>.workers.dev`.

---

### **7. Integrate with Custom Domains**

1. Go to the **Cloudflare Dashboard**.
2. Add a custom domain under **Workers** → **Routes**.
3. Map your Worker to your domain or a specific route (e.g., `api.myapp.com/*`).

---

### **Key Points When Using Cloudflare Workers**:

1. **Stateless**: Workers are stateless. Use external databases like PostgreSQL, Redis, or KV Store for persistence.
2. **Express Alternatives**: Use frameworks like Hono, Miniflare, or native Fetch APIs.
3. **Environment Variables**: Store secrets like API keys in `wrangler.toml` under the `[vars]` section.

## ngnix
### What is Nginx?

**Nginx** (pronounced "engine-x") is a high-performance web server and reverse proxy server. It is widely used for serving static content, load balancing, caching, and as a reverse proxy to route requests to backend servers.

Key features of Nginx:

- Serves static files (HTML, CSS, JS).
- Acts as a reverse proxy for backend applications (Node.js, Express.js, Python apps, etc.).
- Load balances traffic across multiple servers.
- Caches responses for faster performance.

---

### Installing Nginx

#### **1. On Linux**

- **Ubuntu/Debian**:
    
    bash
    `sudo apt update sudo apt install nginx`

After installation:

- Start Nginx:
    
    bash

    
    `sudo systemctl start nginx`
    
- Enable it to start on boot:
    
    bash
    
    Copy code
    
    `sudo systemctl enable nginx`
    

#### **2. On macOS**

Install using Homebrew:

bash

Copy code

`brew install nginx`

Start Nginx:

bash

Copy code

`sudo nginx`

#### **3. On Windows**

- Download the precompiled binaries from Nginx's official website.
- Extract and run `nginx.exe`.

---

### Setting Up Reverse Proxy with Nginx

A **reverse proxy** routes incoming requests from clients to one or more backend servers. For example, it can forward requests from `http://example.com` to `http://localhost:3000` (where your Express app is running).

#### Example Configuration

1. **Open the Nginx configuration file**:
    
    - On Linux/macOS:
        
        bash
        
        Copy code
        
        `sudo nano /etc/nginx/nginx.conf`
        
    - Or create a new file under `/etc/nginx/sites-available` and symlink it to `/etc/nginx/sites-enabled`.
2. **Edit the configuration**: Add a server block to route requests:
    
    nginx
    
    Copy code
    
    `server {     listen 80;     server_name yourdomain.com;      location / {         proxy_pass http://127.0.0.1:3000; # Forward to Express backend         proxy_http_version 1.1;         proxy_set_header Upgrade $http_upgrade;         proxy_set_header Connection 'upgrade';         proxy_set_header Host $host;         proxy_cache_bypass $http_upgrade;     } }`
    
3. **Test the configuration**:
    
    bash
    
    Copy code
    
    `sudo nginx -t`
    
4. **Restart Nginx**:
    
    bash
    
    Copy code
    
    `sudo systemctl restart nginx`
    

---

### Key Nginx Commands

- **Start Nginx**:
    
    bash
    
    `sudo systemctl start nginx`
    
- **Stop Nginx**:
    
    bash
    
    `sudo systemctl stop nginx`
    
- **Restart Nginx**:
    
    bash
    
    `sudo systemctl restart nginx`
    
- **Check status**:
    
    bash
    
    `sudo systemctl status nginx`
    
- **Reload configuration without downtime**:
    
    bash
    
    `sudo nginx -s reload`

## NPM Serve
`npm serve` is a command typically used to run the **`serve`** package, which is a simple HTTP server for serving static files (e.g., HTML, CSS, JavaScript). It is commonly used to preview static websites locally or deploy them for basic use.
### **How to Use `serve`:**

1. Install the `serve` package globally:
    bash
    `npm install -g serve`
2. Serve your static files:
    bash
    `serve <path-to-your-static-folder>`
    Example:
    bash
    `serve build`

This is often used with React applications after building them using `npm run build`.


### ==When using any database to insert some query always use $1 as a parameter to avoid SQL injection.==

## Connection pooling in serverless to DB

**Connection pooling** is a technique used to manage and reuse a fixed number of database connections, instead of creating and closing a new connection for every request. This improves performance by reducing the overhead of establishing a new connection each time and helps prevent connection limits from being exceeded.


# Week-14
### What is Next.js?

**Next.js** is a React framework that helps build web applications with:

- **Server-side Rendering (SSR):** Pages are rendered on the server and sent to the browser.
- **Static Site Generation (SSG):** Pages are pre-built as HTML during build time for faster loading.
- **API Routes:** Allows creating backend APIs within the same app.
- **Routing:** Built-in file-based routing system.

### How Next.js Works:

1. **Pre-rendering:** Pages are either:
    - **Static (SSG):** HTML is pre-generated at build time.
    - **Dynamic (SSR):** HTML is generated on the server per request.
2. **Routing:** Each file in the `pages/` folder is automatically a route (no need to install additional routing libraries).
3. **Data Fetching:** Fetch data using methods like `getStaticProps` (for SSG) or `getServerSideProps` (for SSR).
4. **API Routes:** You can create backend endpoints directly in the `pages/api/` directory.
5. **Client-side Rendering:** For parts of your app needing dynamic interaction, you can still use React hooks like `useState` and `useEffect`.

# Docker
#### **What is Docker?**

Docker is a platform that allows you to develop, ship, and run applications inside **containers**. Containers are lightweight, isolated environments that package an application and its dependencies together. Docker helps ensure that applications run consistently across different environments (development, testing, production).

- **Docker Image**: A blueprint or template used to create containers. It contains the application code, dependencies, and instructions for how to run the application.
- **Docker Container**: A running instance of a Docker image. It encapsulates an application and its environment.

#### 2. **How to Build a Docker Container from an Existing Project**

To build a container for an existing project, you need a **Dockerfile** that defines the environment in which your application runs.

- **Steps to Build a Docker Container:**
    
    1. **Create a Dockerfile**: A file with a set of instructions to define the image.
    2. **Build the Image**: Use the `docker build` command to create an image from the Dockerfile.
    3. **Run the Container**: Once the image is built, run it with `docker run`.
- **Example Dockerfile for a Node.js Application**:
    
    dockerfile
    
    Copy code
    
    `# Use official Node.js image as base FROM node:20  # Set working directory WORKDIR /app  # Copy package files first for caching dependencies COPY package*.json ./  # Install dependencies RUN npm install  # Copy the rest of the application code COPY . .  # Run build and generate Prisma client RUN npm run build RUN npx prisma generate  # Expose port EXPOSE 3000  # Start the application CMD ["node", "dist/index.js"]`
    
- **Build the Docker Image**:
    
    bash
    
    Copy code
    
    `docker build -t my-node-app .`
    
- **Run the Docker Container**:
    
    bash
    
    Copy code
    
    `docker run -d -p 3000:3000 my-node-app`
    

---

#### 3. **How to Pass Environment Variables**

You can pass environment variables to Docker containers in several ways:

1. **Using `ENV` in Dockerfile**: The `ENV` instruction sets environment variables that are available in the container.
    
    Example:
    
    dockerfile
    
    Copy code
    
    `ENV NODE_ENV=production ENV PORT=3000`
    
2. **Using `-e` flag with `docker run`**: Set environment variables when running a container with the `-e` flag.
    
    Example:
    
    bash
    
    Copy code
    
    `docker run -e NODE_ENV=production -e PORT=3000 my-node-app`
    
3. **Using `.env` File with Docker Compose**: If using Docker Compose, store environment variables in a `.env` file and reference them in `docker-compose.yml`.
    
    Example `.env`:
    
    makefile
    
    Copy code
    
    `NODE_ENV=production PORT=3000`
    
    Example `docker-compose.yml`:
    
    yaml
    
    Copy code
    
    `version: '3' services:   web:     image: my-node-app     ports:       - "3000:3000"     environment:       - NODE_ENV=${NODE_ENV}       - PORT=${PORT}`
    

---

#### 4. **Docker Layers and Optimizing Dockerfile**

- **What are Docker Layers?**
    
    - Each instruction in a Dockerfile (e.g., `RUN`, `COPY`, `ADD`) creates a new layer in the image. Layers are cached, which speeds up subsequent builds by reusing unchanged layers.
    - Layers are stacked to create the final image, and each layer adds to the image's size.
- **How to Optimize Dockerfile for Layers:**
    
    1. **Combine multiple commands** into a single `RUN` to minimize layers.
        
        dockerfile
        
        Copy code
        
        `# Instead of multiple RUN commands RUN apt-get update RUN apt-get install -y curl RUN apt-get install -y git  # Use a single RUN command RUN apt-get update && apt-get install -y curl git`
        
    2. **Order your Dockerfile instructions** to optimize caching:
        
        - Place instructions that are less likely to change (like installing dependencies) before copying your code, so they can be cached.
        - This reduces unnecessary work during rebuilds.
        
        Example:
        
        dockerfile
        
        Copy code
        
        `COPY package*.json ./ RUN npm install COPY . . RUN npm run build`
        
    3. **Use Multi-Stage Builds**: Multi-stage builds allow you to create smaller final images by using separate build and production stages.
        
        Example:
        
        dockerfile
        
        Copy code
        
        `# Build stage FROM node:20 AS build-stage WORKDIR /app COPY . . RUN npm install RUN npm run build  # Production stage FROM node:20 AS production-stage WORKDIR /app COPY --from=build-stage /app/dist /app/dist COPY --from=build-stage /app/node_modules /app/node_modules EXPOSE 3000 CMD ["node", "dist/index.js"]`
        
    4. **Use `.dockerignore` to exclude unnecessary files**: This prevents large files and directories (e.g., `node_modules`, `.git`) from being copied into the image.
        
        Example `.dockerignore`:
        
        bash
        
        Copy code
        
        `node_modules .git *.log`
        

---

### Docker Volumes and Networks

#### 1. **Docker Volumes**

Docker volumes are used to persist data generated by and used by Docker containers. They allow data to persist even after containers are stopped or deleted, making them ideal for use cases such as databases, logs, and other persistent data.

##### **Types of Storage in Docker:**

- **Volumes**: Managed by Docker, stored outside of the container filesystem, and can be shared between containers.
- **Bind Mounts**: Direct mapping of files or directories from the host machine to the container.
- **Tmpfs Mounts**: Store data in memory, typically used for temporary data.

##### **Why Use Volumes?**

1. **Persistence**: Data in containers is lost when the container is removed. Volumes provide a way to store data persistently.
2. **Sharing Data Between Containers**: Volumes can be mounted into multiple containers, allowing them to share data.
3. **Easy Backup and Restore**: Volumes can be easily backed up, restored, or moved between systems.

##### **How to Use Docker Volumes:**

1. **Create a Volume**:
    
    bash
    
    Copy code
    
    `docker volume create my-volume`
    
2. **Mount a Volume to a Container**: You can mount the volume using the `-v` or `--mount` flag with `docker run`.
    
    bash
    
    Copy code
    
    `docker run -d -v my-volume:/app/data my-image`
    
    This mounts the `my-volume` volume to the `/app/data` directory inside the container.
    
3. **Inspect a Volume**: To see details about a volume, use the `docker volume inspect` command:
    
    bash
    
    Copy code
    
    `docker volume inspect my-volume`
    
4. **List Volumes**: To list all volumes on your system:
    
    bash
    
    Copy code
    
    `docker volume ls`
    
5. **Remove a Volume**: To remove a volume (ensure it is not in use by any containers):
    
    bash
    
    Copy code
    
    `docker volume rm my-volume`
    

##### **Example Use Case:**

Let's say you're running a database container (e.g., MySQL) and want to persist the database data:

bash

Copy code

`docker run -d -v mysql-data:/var/lib/mysql --name mysql-container mysql:latest`

Here, `mysql-data` is a volume that will persist MySQL data between container restarts.

---

#### 2. **Docker Networks**

Docker networks allow containers to communicate with each other and with the outside world. By default, Docker creates a **bridge network** for containers, but you can create custom networks for more advanced use cases.

##### **Types of Networks in Docker:**

1. **Bridge Network** (default):
    - Containers on the same bridge network can communicate with each other using container names.
    - Suitable for standalone containers and testing.
2. **Host Network**:
    - The container shares the host's network namespace.
    - The container has the same IP address as the host.
    - Suitable for performance-sensitive applications (but limits isolation).
3. **Overlay Network**:
    - Used for multi-host communication (e.g., in Docker Swarm).
    - Allows containers across different Docker hosts to communicate.
4. **None Network**:
    - No network connectivity for the container.
    - Useful for containers that don't need any network access.

##### **How to Use Docker Networks:**

1. **Create a Custom Network**: You can create a custom network for containers to communicate in a controlled environment.
    
    bash
    
    Copy code
    
    `docker network create my-network`
    
2. **Run Containers on the Custom Network**: When running containers, you can specify the network they should join using the `--network` flag.
    
    bash
    
    Copy code
    
    `docker run -d --network my-network --name container1 my-image docker run -d --network my-network --name container2 my-image`
    
    Now, `container1` and `container2` can communicate using their container names on the `my-network`.
    
3. **Inspect a Network**: To view details about a network:
    
    bash
    
    Copy code
    
    `docker network inspect my-network`
    
4. **List Docker Networks**: To see all networks:
    
    bash
    
    Copy code
    
    `docker network ls`
    
5. **Remove a Network**: To remove a custom network (after ensuring no containers are using it):
    
    bash
    
    Copy code
    
    `docker network rm my-network`
    

##### **Example Use Case:**

Let's say you have a backend container and a frontend container, and you want them to communicate with each other. You can create a custom network for both containers:

bash

Copy code

`# Create a custom network docker network create app-network  # Run backend and frontend containers on the same network docker run -d --network app-network --name backend my-backend-image docker run -d --network app-network --name frontend my-frontend-image`

Now, the frontend can make requests to the backend by using the `backend` container name.

---

### Summary of Docker Volumes and Networks

#### **Volumes**:

- **Purpose**: To persist data outside of containers.
- **Commands**:
    - Create volume: `docker volume create <volume_name>`
    - Run container with volume: `docker run -v <volume_name>:<container_path>`
    - Inspect volume: `docker volume inspect <volume_name>`
    - Remove volume: `docker volume rm <volume_name>`

#### **Networks**:

- **Purpose**: To allow containers to communicate with each other or with the outside world.
- **Types of Networks**:
    - **Bridge**: Default, used for containers on the same host.
    - **Host**: Container shares the host's network.
    - **Overlay**: For multi-host communication (Docker Swarm).
    - **None**: No network connectivity.
- **Commands**:
    - Create network: `docker network create <network_name>`
    - Run container on a network: `docker run --network <network_name>`
    - Inspect network: `docker network inspect <network_name>`
    - Remove network: `docker network rm <network_name>`


### **Docker Compose - Quick Overview with Example**

#### **What is Docker Compose?**

Docker Compose is a tool used to define and run multi-container Docker applications. It allows you to define multiple services in a single YAML file (`docker-compose.yml`), making it easy to manage complex applications with multiple containers. You can then run all the services with a single command.

#### **Key Concepts in Docker Compose**

1. **Services**: Each container or application component, e.g., a backend API, a frontend application, or a database.
2. **Networks**: Docker Compose automatically creates networks for communication between services. You can also define custom networks.
3. **Volumes**: Persistent storage shared between services or between the host and the container.
4. **Build**: Docker Compose can build images using Dockerfiles for custom services.
5. **Environment Variables**: Set environment variables to configure services (e.g., database connection strings, application settings).

#### **Basic Structure of `docker-compose.yml`**

yaml

Copy code

`version: '3.8'  # Version of Docker Compose file format  services:  # Define all your services (containers) here   frontend:  # A service for the frontend container     build: ./frontend  # Build the frontend from the Dockerfile in the 'frontend' directory     ports:       - "3000:3000"  # Map port 3000 on the host to port 3000 in the container     networks:       - app-network  # Attach the service to a custom network    backend:  # A service for the backend container     build: ./backend  # Build the backend from the Dockerfile in the 'backend' directory     ports:       - "4000:4000"  # Map port 4000 on the host to port 4000 in the container     environment:       - DB_URI=mongodb://db:27017/myapp  # Set environment variables     depends_on:       - db  # Ensure backend starts after database service     networks:       - app-network  # Attach to the same network as frontend    db:  # A service for the database container (using a pre-built image)     image: mongo:latest  # Use the latest MongoDB image from Docker Hub     networks:       - app-network  # Attach to the same network  networks:  # Define the network   app-network:  # Custom network that services use to communicate     driver: bridge  # Default network driver`

#### **Explanation of the Compose File**

1. **version**: Specifies the version of the Docker Compose file format. Version '3.8' is widely used and supports many features.
2. **services**: This section defines the containers that make up your application.
    - **frontend**: Defines the frontend service, built from a `Dockerfile` in the `frontend` directory. Port 3000 is mapped.
    - **backend**: Defines the backend service, built from a `Dockerfile` in the `backend` directory. It uses MongoDB as the database and waits for the `db` service to be ready.
    - **db**: Defines the database service using the pre-built `mongo:latest` image from Docker Hub.
3. **networks**: All services are attached to a custom network (`app-network`) to allow inter-service communication.

#### **Steps to Use Docker Compose**

1. **Install Docker Compose** (if not installed):
    
    - Docker Compose is often bundled with Docker, but you can install it separately as well.
2. **Create Your Dockerfiles** for each service (frontend, backend, etc.):
    
    Example Dockerfile for **Frontend**:
    
    dockerfile
    
    Copy code
    
    `# Dockerfile for the frontend (React) FROM node:20 WORKDIR /app COPY . . RUN npm install RUN npm run build EXPOSE 3000 CMD ["npm", "start"]`
    
    Example Dockerfile for **Backend**:
    
    dockerfile
    
    Copy code
    
    `# Dockerfile for the backend (Node.js) FROM node:20 WORKDIR /app COPY . . RUN npm install RUN npm run build EXPOSE 4000 CMD ["npm", "start"]`
    
3. **Write `docker-compose.yml`**: Define all services (as shown above).
    
4. **Run Docker Compose**: In the same directory as `docker-compose.yml`, run:
    
    bash
    
    Copy code
    
    `docker-compose up --build`
    
    - `--build`: Rebuilds the images if you make changes to the Dockerfiles.
5. **Access Services**:
    
    - **Frontend**: Accessible on `http://localhost:3000`.
    - **Backend**: Accessible on `http://localhost:4000`.
6. **Stop and Remove Containers**: To stop and remove the containers:
    
    bash
    
    Copy code
    
    `docker-compose down`
    

---

#### **Docker Compose Commands**

- `docker-compose up`: Builds (if necessary) and starts all services.
- `docker-compose up --build`: Builds images before starting services.
- `docker-compose down`: Stops and removes containers, networks, and volumes.
- `docker-compose ps`: Lists the running containers.
- `docker-compose logs`: Shows logs for all containers.

### **What are Bind Mounts?**

A **bind mount** allows you to map a directory or file from your **host machine** (your computer) to a **container**. Any changes made inside the container will be reflected on your host machine and vice versa.

### **Example Scenario:**

Let's say you are developing a simple project on your local machine and want to run it inside a Docker container. You want the code to stay on your local machine, but have the container access it and run the code.

We'll use a simple **Node.js** project as an example.

### **Step 1: Create a Simple Project**

On your **host machine**, create a directory for the project.

bash

Copy code

`mkdir my-node-app cd my-node-app`

Inside this directory, create a simple `index.js` file:

javascript

Copy code

`// index.js console.log('Hello from Docker!');`

Create a `package.json` file as well:

json

Copy code

`{   "name": "my-node-app",   "version": "1.0.0",   "main": "index.js",   "scripts": {     "start": "node index.js"   } }`

### **Step 2: Create a Dockerfile**

Now, let's create a **Dockerfile** in the same directory.

Dockerfile

Copy code

`# Use an official Node.js image FROM node:20  # Set the working directory in the container WORKDIR /app  # Install dependencies (empty for now) COPY package.json . RUN npm install  # Copy the rest of the project files into the container COPY . .  # Expose the application port EXPOSE 8080  # Command to run the app CMD ["npm", "start"]`

This `Dockerfile` will build an image that:

1. Uses the official Node.js image.
2. Installs the dependencies (in this case, none, since we're not adding any for this example).
3. Copies all the project files into the container's `/app` directory.
4. Exposes port `8080`.
5. Runs the app using `npm start`.

### **Step 3: Use Bind Mounts to Link Code to the Container**

Now we will run this Docker container, but we want to **mount** the project directory from our host machine into the container so that any changes we make to the code on the host will immediately be reflected in the container.

Run the following Docker command:

bash

Copy code

`docker run -v $(pwd):/app -p 8080:8080 node:20 npm start`

### **Breaking down the command:**

- `-v $(pwd):/app`: This is where we use the bind mount. We are saying, "Mount my current directory (where the `my-node-app` folder is) to the `/app` directory inside the container."
    - `$(pwd)` will give the full path of the current directory on your machine.
    - `/app` is the path where the directory will be mounted inside the container.
- `-p 8080:8080`: This maps port 8080 from the container to port 8080 on the host machine. (For this example, it won't be used, since we're just logging to the console, but it's useful for web apps).
- `node:20 npm start`: This tells the container to use the Node.js image to run the `npm start` command.

### **What Happens Next?**

1. **Bind Mount in Action**: The `-v` option links the local directory (`$(pwd)`) to the container's `/app` directory. So, the container will use your code from your host machine.
    
2. **Changes Reflection**: If you edit the `index.js` file on your **local machine** while the container is running, the container will automatically use the updated version of `index.js` without needing to rebuild the container.
    
3. **Console Output**: The container runs `npm start`, and you'll see this in the container's log output:
    

bash

Copy code

`Hello from Docker!`

### **Step 4: Modify the Code Locally**

Now, let’s try modifying the `index.js` file on your local machine:

javascript

`// index.js console.log('Hello from the updated Docker container!');`

After saving the file, you’ll immediately see the updated message in the container's logs, because the file was **directly mounted**.

### **Step 5: Stopping the Container**

When you’re done, you can stop the container by pressing `Ctrl+C` or running:

bash

Copy code

`docker ps   # To find the container ID docker stop <container_id>  # Stop the container`


