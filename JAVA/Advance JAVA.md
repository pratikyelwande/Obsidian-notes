# 📒 Maven 

---
## 📌 1. What is Maven?

- **Maven** = Project Management & Build Tool for Java.
    
- Developed by **Apache**.
    
- Handles:
    
    1. **Dependency Management** – Automatically downloads JARs.
        
    2. **Build Process** – Compiles, tests, packages code.
        
    3. **Project Structure** – Standardized directory layout.
        
    4. **Plugins** – Adds tasks like deployment, testing, reporting.
        

---

## 📌 2. Why Use Maven?

Without Maven ❌

- You manually download JARs.
    
- Handle conflicts yourself.
    
- No standard project structure.
    

With Maven ✅

- Just add dependency in `pom.xml`.
    
- Maven fetches the JAR from **Maven Central Repository**.
    
- Consistent structure across projects.
    

---

## 📌 3. Maven Directory Structure

`my-app  ├── src  │   ├── main  │   │   ├── java         # Source code  │   │   └── resources    # Config files  │   └── test  │       ├── java         # Test code  │       └── resources  ├── target               # Compiled output (auto-generated)  └── pom.xml              # Project Object Model file`

---

## 📌 4. The `pom.xml`

Heart of Maven = **POM (Project Object Model)**  
Example:

`<project xmlns="http://maven.apache.org/POM/4.0.0"          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"          xsi:schemaLocation="http://maven.apache.org/POM/4.0.0                               http://maven.apache.org/xsd/maven-4.0.0.xsd">      <modelVersion>4.0.0</modelVersion>      <groupId>com.example</groupId>     <artifactId>my-app</artifactId>     <version>1.0-SNAPSHOT</version>      <dependencies>         <!-- Example: JUnit dependency -->         <dependency>             <groupId>junit</groupId>             <artifactId>junit</artifactId>             <version>4.13.2</version>             <scope>test</scope>         </dependency>     </dependencies> </project>`

- **groupId** → Organization/project domain (`com.example`).
    
- **artifactId** → Project/module name (`my-app`).
    
- **version** → Version of project (`1.0-SNAPSHOT`).
    
- **dependencies** → List of required libraries.
    

---

## 📌 5. Maven Lifecycle & Phases

Maven has **3 lifecycles**:

1. **default** → For build (compile → test → package → install → deploy).
    
2. **clean** → Cleans previous build (`mvn clean`).
    
3. **site** → Generates project documentation.
    

Phases in default lifecycle:

- `validate` → Check if project is correct.
    
- `compile` → Compile source code.
    
- `test` → Run unit tests.
    
- `package` → Package into JAR/WAR.
    
- `install` → Install in local repository.
    
- `deploy` → Deploy to remote repository.
    

---

## 📌 6. Common Maven Commands

- `mvn clean` → Deletes `target` folder.
    
- `mvn compile` → Compiles source code.
    
- `mvn test` → Runs tests.
    
- `mvn package` → Builds JAR/WAR.
    
- `mvn install` → Installs package in local repo (`~/.m2`).
    
- `mvn deploy` → Uploads to remote repo.
    

---

## 📌 7. Maven Repositories

- **Local Repository** → `~/.m2/repository` on your machine.
    
- **Central Repository** → Official Maven repo (default).
    
- **Remote Repository** → Company/internal repositories.
    

---

## 📌 8. Dependency Management

Add a dependency in `pom.xml`:

`<dependency>   <groupId>mysql</groupId>   <artifactId>mysql-connector-java</artifactId>   <version>8.0.33</version> </dependency>`

👉 Maven downloads it from **Central Repository** automatically.

---

## 📌 9. Maven Plugins

- Extend Maven functionality.  
    Examples:
    
- `maven-compiler-plugin` → Compiles code.
    
- `maven-surefire-plugin` → Runs tests.
    
- `maven-jar-plugin` → Creates JAR files.
    

---

## 📌 10. Important Interview Questions

### 🔹 Q1. What is Maven?

👉 Maven is a build automation & dependency management tool for Java projects.

---

### 🔹 Q2. Difference between Ant and Maven?

- **Ant** → Task-based (you define tasks manually).
    
- **Maven** → Convention-based (standard structure, predefined lifecycle).
    

---

### 🔹 Q3. What is the difference between `compile` and `install` phase?

- `compile` → Just compiles code.
    
- `install` → Builds and copies the artifact into **local repository**.
    

---

### 🔹 Q4. What is the difference between local, central, and remote repository?

- **Local** → On your machine (`.m2`).
    
- **Central** → Global public repo.
    
- **Remote** → Custom/private repo.
    

---

### 🔹 Q5. What is a Maven Archetype?

👉 A **template** for project structure (e.g., `maven-archetype-quickstart` creates a basic Java project).

---

### 🔹 Q6. What is `pom.xml` used for?

👉 Contains project configuration: dependencies, build plugins, version, repositories.

---

### 🔹 Q7. What are Maven build lifecycles?

👉 `default`, `clean`, `site`.

---

### 🔹 Q8. What is a SNAPSHOT version?

👉 Indicates a **development version** (changes frequently, not stable).  
Example: `1.0-SNAPSHOT`.

---

### 🔹 Q9. How does Maven handle dependency conflicts?

👉 Maven uses **dependency mediation** – by default, it picks the **nearest definition** in dependency tree.

---

### 🔹 Q10. Can we skip tests while building?

👉 Yes → `mvn package -DskipTests`.

# ==Hibernate==

## 🔹 What is ORM?

- **ORM (Object Relational Mapping)** is a technique that maps Java objects to database tables.
    
- Instead of writing SQL manually, ORM automatically translates object state ↔ database records.
    
- Example:
    
    - Java Class → `Employee.java`
        
    - DB Table → `employee`
        
    - Object → `emp.setName("Pratik")` → Stored in DB column `emp_name`.
        

👉 Hibernate is the **most popular ORM framework in Java**.

---

## 🔹 Why Hibernate?

- Reduces boilerplate JDBC code.
    
- Portable across different databases.
    
- Auto table creation.
    
- Caching support.
    
- Supports HQL (Hibernate Query Language).
    
- Provides **Lazy Loading**, **Transactions**, **Mappings** (One-to-One, One-to-Many, etc.).
    

---

## 🔹 Hibernate Architecture

1. **Configuration** → Reads config (`hibernate.cfg.xml`).
    
2. **SessionFactory** → Heavy object, one per DB, creates sessions.
    
3. **Session** → Lightweight, performs CRUD (like JDBC connection).
    
4. **Transaction** → Handles commit/rollback.
    
5. **Query / Criteria** → Executes queries.
    

---

## 🔹 Steps to Setup Hibernate in IntelliJ (with MySQL)

### 1️⃣ Create Maven Project

- In IntelliJ → New Project → Maven → Enter GroupId & ArtifactId.
    

### 2️⃣ Add Dependencies in `pom.xml`

```<dependencies>
    <!-- Hibernate Core -->
    <dependency>
        <groupId>org.hibernate.orm</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>6.4.4.Final</version>
    </dependency>

    <!-- MySQL Connector -->
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <version>8.0.33</version>
    </dependency>

    <!-- JPA API -->
    <dependency>
        <groupId>jakarta.persistence</groupId>
        <artifactId>jakarta.persistence-api</artifactId>
        <version>3.1.0</version>
    </dependency>
</dependencies>
```
---

### 3️⃣ Create Hibernate Config File → `resources/hibernate.cfg.xml`

```<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">

<hibernate-configuration>
    <session-factory>
        <!-- DB Connection -->
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/demohibernate</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">root</property>

        <!-- Dialect -->
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>

        <!-- Auto Table Creation -->
        <property name="hibernate.hbm2ddl.auto">update</property>

        <!-- Show SQL -->
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>

        <!-- Entity Class -->
        <mapping class="org.example.Employee"/>
    </session-factory>
</hibernate-configuration>

```

---

### 4️⃣ Create Entity Class → `Employee.java`

```import jakarta.persistence.*;

@Entity
@Table(name = "employee")
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "emp_name", nullable = false)
    private String name;

    private double salary;

    // Getters, setters, toString
}

```

---

### 5️⃣ Create Main Class → `App.java`

```import org.hibernate.Session;
import org.hibernate.SessionFactory;
import org.hibernate.Transaction;
import org.hibernate.cfg.Configuration;

import java.util.List;

public class App {
    public static void main(String[] args) {
        SessionFactory factory = new Configuration().configure().buildSessionFactory();
        Session session = factory.openSession();

        // Insert
        Transaction tx = session.beginTransaction();
        Employee emp = new Employee();
        emp.setName("Pratik");
        emp.setSalary(75000);
        session.save(emp);
        tx.commit();
        System.out.println("✅ Employee Created: " + emp);

        // Read
        List<Employee> employees = session.createQuery("from Employee", Employee.class).list();
        employees.forEach(System.out::println);

        session.close();
        factory.close();
    }
}
```

---
## 🔹 Hibernate CRUD Quick Reference

| Operation    | Code                                                           |
| ------------ | -------------------------------------------------------------- |
| Insert       | `session.save(emp);`                                           |
| Select by ID | `session.get(Employee.class, 1);`                              |
| Select All   | `session.createQuery("from Employee", Employee.class).list();` |
| Update       | `session.update(emp);`                                         |
| Delete       | `session.delete(emp);`                                         |

---
## 🔹 Hibernate Key Concepts

- **hbm2ddl.auto**:
    
    - `create` → Creates table fresh every time.
        
    - `update` → Updates schema (best for dev).
        
    - `validate` → Validates schema.
        
    - `create-drop` → Drops table on exit.
        
- **Lazy vs Eager Loading**:
    
    - `Lazy` → Loads when accessed.
        
    - `Eager` → Loads immediately.
        
- **Caching**:
    
    - Level 1: Session scope.
        
    - Level 2: SessionFactory scope.
        

---
## 🎯 Hibernate Interview Q&A (Short Notes with Examples)

### 1. What is Hibernate?

ORM framework to map Java objects with database tables.

---
### 2. Difference between JDBC & Hibernate?

- JDBC → Manual SQL, result set handling.
    
- Hibernate → Automatic mapping, HQL.

---

### 3. Difference between get() vs load()?

`Employee e1 = session.get(Employee.class, 1); // returns null if not found Employee e2 = session.load(Employee.class, 1); // throws exception if not found`

---
### 4. Difference between save() vs persist()?

- `save()` → Returns ID.
    
- `persist()` → Doesn’t return ID, but ensures persistence.

---

### 5. What is HQL?

Hibernate Query Language, object-oriented.

`List<Employee> list = session.createQuery("from Employee where salary > :s", Employee.class)                              .setParameter("s", 50000)                              .list();`

---

### 6. What is Lazy Loading?

Objects fetched only when accessed.

---

### 7. What are Hibernate caching levels?

- First Level (Session).
    
- Second Level (SessionFactory).
    
- Query Cache.

---
### 8. How to configure Hibernate?

- Add dependencies.
    
- Create `hibernate.cfg.xml`.
    
- Add entity classes.
    
- Use `SessionFactory` + `Session`.


# Spring Framework
## Servlet

### Working of servlet

![[{29E369AA-2867-4F31-BEFE-AD6EB170FC26}.png]]
# 🟢 What is a Servlet?

- A **Servlet** is a Java class that runs on the **server** and handles **client requests** (usually HTTP requests).
    
- It is part of the **Java EE / Jakarta EE** standard.
    
- Runs inside a **Servlet Container** (like Tomcat, Jetty, GlassFish).
    
- Main role: Take input from client (browser), process it (logic/DB), and send a response (HTML/JSON/etc.).
    

---

# 🟢 Servlet Lifecycle

Every servlet goes through **3 main phases**:

1. **Loading & Initialization**
    
    - Container loads servlet class into memory.
        
    - Calls `init(ServletConfig config)` **once**.
        
2. **Request Handling**
    
    - For every request → calls `service(HttpServletRequest req, HttpServletResponse res)`.
        
    - Based on HTTP method:
        
        - `doGet()` → for GET request
            
        - `doPost()` → for POST request
            
        - `doPut()`, `doDelete()`, etc.
            
3. **Destruction**
    
    - When container shuts down or servlet unloaded → calls `destroy()` **once**.
        

---

# 🟢 Servlet API Classes

Main packages:

- `javax.servlet.*` (base interfaces)
    
- `javax.servlet.http.*` (HTTP-specific classes)
    

Important classes:

- `HttpServlet` → base class for HTTP Servlets.
    
- `HttpServletRequest` → represents client request (headers, params, body).
    
- `HttpServletResponse` → represents response (write output, set headers, status).
    
- `ServletConfig` → per-servlet config.
    
- `ServletContext` → shared info across all servlets.
    

---

# 🟢 Writing a Servlet

Example: **HelloServlet**

```import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class HelloServlet extends HttpServlet {
    public void doGet(HttpServletRequest req, HttpServletResponse res) throws IOException {
        res.setContentType("text/html");
        PrintWriter out = res.getWriter();
        out.println("<h1>Hello from Servlet!</h1>");
    }
}

```

### Deploying:

1. Package into `.war` (Web Archive).
    
2. Put inside Tomcat `webapps/`.
    
3. Configure mapping in `web.xml` OR use `@WebServlet` annotation.
    

---

# 🟢 Request & Response

- **HttpServletRequest** → get request info:
    
    - `getParameter("username")`
        
    - `getHeader("User-Agent")`
        
    - `getSession()`
        
- **HttpServletResponse** → build response:
    
    - `setContentType("text/html")`
        
    - `setStatus(200)`
        
    - `getWriter().println("...")`
        

---

# 🟢 Servlet Config & Context

- **ServletConfig**: Initialization parameters (specific to one servlet).
    
- **ServletContext**: Shared application-wide parameters.
    

Example (web.xml):

```<servlet>
  <servlet-name>Hello</servlet-name>
  <servlet-class>HelloServlet</servlet-class>
  <init-param>
    <param-name>message</param-name>
    <param-value>Welcome!</param-value>
  </init-param>
</servlet>
```

In servlet:

`String msg = getServletConfig().getInitParameter("message");`

---

# 🟢 Session Management

HTTP is **stateless**, so Servlets use:

1. **Cookies**
    
    - Small data stored in client browser.
        
    - `response.addCookie(new Cookie("user", "Pratik"));`
        
2. **URL Rewriting**
    
    - Append session info in URL.
        
    - `response.encodeURL("dashboard.jsp");`
        
3. **HttpSession**
    
    - Most common.
        
    - `HttpSession session = request.getSession();`
        
    - `session.setAttribute("name", "Pratik");`
        
    - `session.getAttribute("name");`
        

---

# 🟢 Request Dispatching

Servlets can forward/redirect:

- **Forward (server-side)** → request stays same.
    
    `RequestDispatcher rd = req.getRequestDispatcher("home.jsp"); rd.forward(req, res);`
    
- **Redirect (client-side)** → browser makes new request.
    
    `res.sendRedirect("https://google.com");`
    

---

# 🟢 Filters

- Special components that **intercept requests/responses** before reaching servlets or JSP.
    
- Used for logging, authentication, compression, etc.
    
```
@WebFilter("/*")
public class LogFilter implements Filter {
   public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) 
      throws IOException, ServletException {
      System.out.println("Request received at " + new Date());
      chain.doFilter(req, res); // pass request along
   }
}
```

---
# 🟢 Listeners

- For listening to events in Servlet context/session.
    
- Example: track session creation, app startup, shutdown.

```@WebListener
public class MyListener implements ServletContextListener {
   public void contextInitialized(ServletContextEvent sce) {
      System.out.println("App started!");
   }
}
```

---
# 🟢 Advantages of Servlets

✅ Portable (Java-based).  
✅ Efficient (multi-threaded, one instance per servlet).  
✅ Secure (runs inside container sandbox).  
✅ Extensible (filters, listeners).

---
# 🟢 Limitations of Servlets

❌ Writing HTML in Java (`out.println("<h1>..</h1>")`) is painful.  
❌ Mixing business logic + UI logic → messy.  
❌ Hard to maintain large apps.

👉 That’s why **JSP** (frontend view) was introduced.  
👉 Then **MVC frameworks** like **Struts, Spring MVC** improved separation.  
👉 Finally **Spring Boot** simplified setup + configuration.

---

# 🟢 Summary Mindmap

- Servlet = **Java class for request/response**.
    
- Lifecycle = `init()` → `service()` → `destroy()`.
    
- APIs: `HttpServletRequest`, `HttpServletResponse`.
    
- Features: Config, Context, Sessions, Filters, Listeners.
    
- Used with JSP for MVC.

---
# 🔹 Basic Level

### 1. What is a Servlet?

👉 A servlet is a **Java class** that runs on a **web server** inside a **servlet container** to handle client requests and generate responses, usually over **HTTP**.

---

### 2. What is a Servlet Container?

👉 A **servlet container** (like Tomcat, Jetty) is part of a web server that:

- Manages servlet lifecycle (init → service → destroy).
    
- Provides request/response objects.
    
- Handles threading, security, session management.
    

---

### 3. Explain the lifecycle of a Servlet.

- **`init()`** → called once when servlet is loaded.
    
- **`service()`** → called for each request, dispatches to `doGet()`, `doPost()`, etc.
    
- **`destroy()`** → called once when servlet is unloaded.
    

---

### 4. Difference between `doGet()` and `doPost()`?

- `doGet()`:
    
    - Used for idempotent operations (fetch data).
        
    - Params passed in URL (limited length).
        
    - Visible in browser history.
        
- `doPost()`:
    
    - Used for sensitive/large data (form submission).
        
    - Params in request body.
        
    - Not visible in URL.
        

---

### 5. What is the difference between `sendRedirect()` and `forward()`?

- **Forward** (`RequestDispatcher.forward()`):
    
    - Server-side transfer, browser unaware.
        
    - URL in browser doesn’t change.
        
- **Redirect** (`response.sendRedirect()`):
    
    - Client-side, browser makes a new request.
        
    - URL changes.
        
    - Slower than forward.
        

---

# 🔹 Intermediate Level

### 6. What are `ServletConfig` and `ServletContext`?

- **ServletConfig**: Config params for a **specific servlet**.
    
- **ServletContext**: Shared config info for **whole application**.
    

---

### 7. How does the Servlet handle multiple requests?

👉 Servlet containers create **one instance per servlet**.  
For each request → a **new thread** is spawned → calls `service()` method.

---

### 8. How does session management work in Servlets?

- **Cookies**
    
- **URL rewriting**
    
- **Hidden form fields**
    
- **HttpSession object** (most common).
    

---

### 9. What are Filters in Servlets?

👉 Filters intercept requests/responses before they reach servlets or after.  
Used for **logging, authentication, compression, auditing** etc.

---

### 10. What are Listeners in Servlets?

👉 Special classes that listen to **events** in the web application (context initialized, session created/destroyed).  
E.g., `ServletContextListener`, `HttpSessionListener`.

---

# 🔹 Advanced Level

### 11. What is the difference between GenericServlet and HttpServlet?

- **GenericServlet**: Protocol independent, base class for all servlets.
    
- **HttpServlet**: Subclass specialized for **HTTP protocol**.
    

---

### 12. What are advantages of Servlets over CGI?

- Servlets are **multi-threaded** → better performance.
    
- Same servlet instance serves multiple requests.
    
- Platform-independent.
    
- Built-in session management.
    

---

### 13. How can you handle exceptions in a Servlet?

- Using **try-catch** inside servlet.
    
- Using **error-page** in `web.xml`.
    
- Using **Filter** for centralized error handling.
    

---

### 14. What is the difference between JSP and Servlet?

- **Servlet** → Controller (Java code for logic).
    
- **JSP** → View (HTML + Java for presentation).
    
- JSP internally compiles into a servlet.
    

---

### 15. What is the difference between Servlet and Spring Controller?

- **Servlet**: Low-level, directly handles request/response.
    
- **Spring Controller**: Built on top of servlets, provides cleaner MVC architecture with annotations, dependency injection, etc.
    

---

# 🔹 Practical/Code-based

### 16. Example: How to get request parameters in a Servlet?

`String username = request.getParameter("username"); String password = request.getParameter("password");`

---

### 17. Example: How to set attributes and forward to JSP?

`request.setAttribute("user", "Pratik"); RequestDispatcher rd = request.getRequestDispatcher("welcome.jsp"); rd.forward(request, response);`

---

### 18. Example: How to use HttpSession in Servlet?

`HttpSession session = request.getSession(); session.setAttribute("username", "Pratik");  String name = (String) session.getAttribute("username");`

---

### 19. Can we have multiple servlets in one web app?

👉 Yes, each servlet is mapped to different URLs via `web.xml` or `@WebServlet`.

---

### 20. How does the container map a URL to a Servlet?

- Using `web.xml` mapping:
    

`<servlet-mapping>    <servlet-name>Hello</servlet-name>    <url-pattern>/hello</url-pattern> </servlet-mapping>`

- Or using annotation:
    
`@WebServlet("/hello")`

# 🔹 What is **==Spring==** MVC?

Spring MVC (**Model–View–Controller**) is a **web framework** built on the **Servlet API**.  
It simplifies developing Java web apps by handling request–response flow, binding data, and rendering views.

👉 Think of it as an **enhanced version of Servlets + JSP + MVC architecture** with many features out of the box.

---

# 🔹 Core Components of Spring MVC

1. **DispatcherServlet** → The **front controller**, entry point for every request.
    
2. **HandlerMapping** → Finds which controller should handle a request.
    
3. **Controller** → Handles the request, prepares the model, and returns a view name.
    
4. **Model** → Holds data that the view will use.
    
5. **ViewResolver** → Maps the view name returned by the controller to an actual JSP/HTML/Thymeleaf file.
    
6. **View** → Renders the response to the client.
    

---

# 🔹 Working of Spring MVC (Step by Step Flow)

Let’s say a client sends a request → `http://localhost:8080/myapp/hello`.

### 1. **Request comes in**

- The request first hits **DispatcherServlet** (configured in `web.xml` or via Spring Boot autoconfig).
    
- DispatcherServlet is the **Front Controller**.
    

### 2. **Handler Mapping**

- DispatcherServlet asks **HandlerMapping**:  
    👉 _“Which controller method should handle `/hello`?”_
    
- HandlerMapping finds the right controller (`HelloController`).
    

### 3. **Controller Execution**

- Controller executes, prepares data, and returns a **ModelAndView** (model data + view name).
    

### 4. **View Resolver**

- DispatcherServlet asks **ViewResolver**:  
    👉 _“Where is the view named `hello`?”_
    
- ViewResolver maps `hello` → `hello.jsp` (or `hello.html` in Thymeleaf).
    

### 5. **View Rendering**

- View is rendered (with model data injected).
    

### 6. **Response to Client**

- HTML response goes back to the browser.
    

---

# 🔹 Diagram of Spring MVC Flow

```
[Client Browser]
        |
        v
[DispatcherServlet]  <-- Front Controller
        |
   (asks HandlerMapping)
        |
        v
   [Controller] <-- Executes business logic
        |
        v
   [Model + View name]
        |
   (asks ViewResolver)
        |
        v
   [View (JSP/Thymeleaf/etc)]
        |
        v
   [Response to Client]

```
# 🔹 Example Code

**Controller:**
```
@Controller
public class HelloController {

    @GetMapping("/hello")
    public String hello(Model model) {
        model.addAttribute("username", "Pratik");
        return "hello";  // View name → resolved by ViewResolver
    }
}

```

**View (hello.jsp):**

`<html> <body>    <h1>Hello, ${username}!</h1> </body> </html>`

**Spring config (if not using Spring Boot):**

```
<bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
    <property name="prefix" value="/WEB-INF/views/"/>
    <property name="suffix" value=".jsp"/>
</bean>
```

👉 Now `return "hello";` maps to `/WEB-INF/views/hello.jsp`.

# 🎯 Spring MVC Interview Questions & Answers

---

### 1. What is Spring MVC?

👉 A web framework built on the Servlet API, following the **Model-View-Controller** design pattern. It provides features like data binding, validation, view resolution, REST API support, and integration with Spring features.

---

### 2. What is DispatcherServlet in Spring MVC?

👉 It is the **front controller**. All requests first hit `DispatcherServlet`, which coordinates with HandlerMapping, Controllers, and ViewResolver to generate responses.

---

### 3. Explain Spring MVC workflow.

1. Client request → DispatcherServlet
    
2. DispatcherServlet → HandlerMapping
    
3. HandlerMapping → Controller
    
4. Controller → returns Model + View name
    
5. DispatcherServlet → ViewResolver
    
6. ViewResolver → View
    
7. View → Response
    

---

### 4. Difference between @Controller and @RestController?

- `@Controller` → Used in MVC apps; returns **view name** (JSP, Thymeleaf).
    
- `@RestController` → Returns **JSON/XML directly** (used in REST APIs).
    

---

### 5. How is data passed from Controller to View?

👉 Using **Model**, **ModelMap**, or **ModelAndView**.  
Example:

`model.addAttribute("name", "Pratik");`

---

### 6. What is a ViewResolver?

👉 A component that maps **logical view names** (returned by controllers) to actual views (JSP, Thymeleaf, etc.).

---

### 7. How does Spring MVC handle exceptions?

👉 Using:

- `@ExceptionHandler` → Method-level exception handling.
    
- `@ControllerAdvice` → Global exception handling.
    

---

### 8. Difference between Servlet and Spring MVC?

|Feature|Servlet/JSP|Spring MVC|
|---|---|---|
|Request handling|`doGet()`, `doPost()`|`@GetMapping`, `@PostMapping`|
|View handling|PrintWriter/JSP forwarding|ViewResolver + multiple view types|
|Data binding|Manual `getParameter()`|Automatic (`@ModelAttribute`)|
|REST support|Manual JSON/XML handling|Built-in (`@RestController`)|
|Exception handling|Try-catch or `web.xml` error pages|`@ExceptionHandler`, `@ControllerAdvice`|

---

### 9. Can Spring MVC be used without a web.xml?

👉 Yes. With Servlet 3.0+ and Spring’s Java-based config, you can configure `DispatcherServlet` programmatically without `web.xml`.

---

### 10. What is @ModelAttribute used for?

👉 Used to bind request parameters directly to Java objects.  
Example:

`@PostMapping("/register") public String register(@ModelAttribute User user) {     return "success"; }`

---

### 11. What is HandlerMapping in Spring MVC?

👉 It maps incoming requests to the correct **controller method**.

---

### 12. What is the role of Interceptors in Spring MVC?

👉 Similar to Servlets Filters. Used to perform tasks like logging, authentication, performance monitoring **before or after** controller execution.

## ==Layered architecture-==

![[Pasted image 20251001191856.png]]
### 📌 Explanation of the Diagram

- **Clients** → Users (like browser, mobile apps, API consumers).
    
- **Controller Layer** → Handles client requests and returns responses (REST endpoints).
    
- **Service Layer** → Holds **business logic**, talks to repositories, may use utilities.
    
- **Repository Layer** → Interacts with the **DB** (JPA/Hibernate/JDBC).
    
- **DB** → Stores persistent data.
    

### 🔧 Supporting Components on Top

- **DTO (Data Transfer Object):**
    
    - Used to transfer data between layers without exposing entities.
        
    - Helps in data validation, response shaping.
        
- **Utility Classes:**
    
    - Helper classes (e.g., for string formatting, date conversion, JWT token handling).
        
- **Entity:**
    
    - Domain model mapped to DB tables with `@Entity`.
        
- **Configuration:**
    
    - Centralized setup (security config, bean definitions, CORS, DB configs, etc.).
        

---

### 🔄 Request–Response Flow (based on your diagram):

1. **Client → Controller** (REST request).
    
2. **Controller → Service** (delegates business logic).
    
3. **Service → Repository** (queries database).
    
4. **Repository → DB** (fetch/insert/update data).
    
5. **DB → Repository → Service → Controller → Client** (response back).
    

Along the way:

- **DTOs** are used between **Controller ↔ Service**.
    
- **Entities** are used between **Service ↔ Repository**.
    
- **Utilities** can be used anywhere inside services.
    
- **Configuration** affects all layers.


# ==Controller Layer Annotations Notes==

---

## **1. @RestController**

### **Definition**

- Combines `@Controller` + `@ResponseBody`.
    
- Used to create **RESTful web services**.
    
- Automatically converts Java objects to **JSON/XML** in the HTTP response.
    

### **When to Use**

- For APIs that **return data**, not HTML views.
    

### **Example**

`@RestController @RequestMapping("/api") public class HelloController {      @GetMapping("/hello")     public String sayHello() {         return "Hello, Spring Boot!";     } }`

- URL: `/api/hello` → Output: `"Hello, Spring Boot!"`
    

### **Key Points**

- No need for `@ResponseBody` on each method.
    
- Works well with `@GetMapping`, `@PostMapping`, etc.
    

---

## **2. @Controller**

### **Definition**

- Marks a class as a **Spring MVC controller**.
    
- By default, it returns **view templates** (like Thymeleaf, JSP).
    

### **Difference from @RestController**

|Feature|@Controller|@RestController|
|---|---|---|
|Returns View|Yes (HTML pages)|No|
|Returns JSON|Requires @ResponseBody|Automatic|
|Used For|Web applications|REST APIs|

### **Example**

`@Controller public class HomeController {      @GetMapping("/home")     public String home() {         return "home"; // Looks for home.html or home.jsp     } }`

---

## **3. @RequestMapping**

### **Definition**

- Maps HTTP requests to **classes or methods**.
    
- Can specify **URL, method type, headers, params, consumes, produces**.
    

### **Usage**

- Can be applied at **class level** (base path) or **method level** (endpoint).
    

### **Example**

`@RestController @RequestMapping("/api") public class UserController {      @RequestMapping(value="/users", method=RequestMethod.GET)     public String getUsers() {         return "All users";     } }`

### **Key Points**

- Parent annotation of `@GetMapping`, `@PostMapping`, etc.
    
- Flexible: can define headers, params, content types.
    

---

## **4. @GetMapping / @PostMapping / @PutMapping / @DeleteMapping / @PatchMapping**

### **Definition**

- Specialized shortcuts of `@RequestMapping` for specific HTTP methods.
    

|Annotation|HTTP Method|Usage|
|---|---|---|
|@GetMapping|GET|Fetch data|
|@PostMapping|POST|Create data|
|@PutMapping|PUT|Update/replace data|
|@DeleteMapping|DELETE|Delete data|
|@PatchMapping|PATCH|Partial update|

### **Example**

```
@RestController
@RequestMapping("/posts")
public class PostController {

    @GetMapping("/{id}")
    public String getPost(@PathVariable int id) {
        return "Post ID: " + id;
    }

    @PostMapping
    public String createPost(@RequestBody Post post) {
        return "Post created: " + post.getTitle();
    }
}

```

---

## **5. @PathVariable**

### **Definition**

- Extracts **dynamic values from the URL path**.
    
- Often used for IDs or resource identifiers.
    

### **Example**

`@GetMapping("/users/{id}") public String getUser(@PathVariable int id) {     return "User ID: " + id; }`

- URL: `/users/10` → Output: `"User ID: 10"`
    

### **Multiple Variables**

```
@GetMapping("/orders/{orderId}/items/{itemId}")
public String getItem(@PathVariable int orderId, @PathVariable int itemId) {
    return "Order: " + orderId + ", Item: " + itemId;
}

```

---

## **6. @RequestParam**

### **Definition**

- Extracts **query parameters** from the URL (after `?`).
    
- Useful for **search, filter, pagination**.
    

### **Example**

```
@GetMapping("/search")
public String search(@RequestParam String query, @RequestParam(defaultValue="10") int limit) {
    return "Query: " + query + ", Limit: " + limit;
}

```

- URL: `/search?query=java&limit=5` → Output: `"Query: java, Limit: 5"`
    

### **Key Points**

- Can be **optional** using `required=false` or `defaultValue`.
    
- Can accept **List** for multiple values: `?tag=a&tag=b`.
    

---

## **7. @RequestBody**

### **Definition**

- Binds **HTTP request body** (usually JSON) to a **Java object**.
    
- Automatically converts JSON → Java object using **Jackson**.
    

### **Example**

`@PostMapping("/users") public String createUser(@RequestBody User user) {     return "User created: " + user.getFirstName(); }`

- URL Body (JSON):
    

`{   "firstName": "Pratik",   "lastName": "Yelwande",   "age": 25 }`

### **Key Points**

- Default constructor needed in Java class.
    
- Used mainly with POST, PUT, PATCH.
    
- Works well with `@Valid` for validation.
    

---

## **8. @ResponseBody**

### **Definition**

- Converts **method return value → JSON/XML** and sends it in HTTP response.
    
- Used with **@Controller** when you don’t want a view.
    

### **Example**

```
@Controller
@RequestMapping("/api")
public class HelloController {

    @GetMapping("/hello")
    @ResponseBody
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}

```

### **Key Points**

- Automatically included in `@RestController`.
    
- Use only if you’re using **plain @Controller**.
    

---

## **9. ResponseEntity**

### **Definition**

- Represents **entire HTTP response**: body + status code + headers.
    
- Gives **full control** over the response.
    

### **Example 1: Simple Response**

```
@GetMapping("/user")
public ResponseEntity<User> getUser() {
    User user = new User("Pratik", "Yelwande");
    return new ResponseEntity<>(user, HttpStatus.OK);
}

```

### **Example 2: With 404**

```
@GetMapping("/user/{id}")
public ResponseEntity<User> getUserById(@PathVariable int id) {
    User user = findUserById(id);
    if(user == null) return new ResponseEntity<>(HttpStatus.NOT_FOUND);
    return new ResponseEntity<>(user, HttpStatus.OK);
}

```

### **Example 3: With Headers**

```
@GetMapping("/user/header")
public ResponseEntity<String> getWithHeader() {
    HttpHeaders headers = new HttpHeaders();
    headers.add("Custom-Header", "PratikYelwande");
    return new ResponseEntity<>("Hello World", headers, HttpStatus.OK);
}

```

---

## **Quick Reference Table**

|Annotation / Class|Purpose|Usage Example|
|---|---|---|
|@RestController|REST API class (JSON)|`@RestController public class UserController`|
|@Controller|MVC controller (HTML view)|`@Controller public class HomeController`|
|@RequestMapping|Map URLs & HTTP methods|`@RequestMapping("/users")`|
|@GetMapping|GET requests|`@GetMapping("/users")`|
|@PostMapping|POST requests|`@PostMapping("/users")`|
|@PutMapping|PUT requests|`@PutMapping("/users/{id}")`|
|@DeleteMapping|DELETE requests|`@DeleteMapping("/users/{id}")`|
|@PatchMapping|PATCH requests|`@PatchMapping("/users/{id}")`|
|@PathVariable|Extract path values|`/users/{id}` → `@PathVariable int id`|
|@RequestParam|Extract query params|`/search?query=java` → `@RequestParam String query`|
|@RequestBody|Map request JSON → Java object|`@RequestBody User user`|
|@ResponseBody|Map return value → JSON|`@ResponseBody public String hello()`|
|ResponseEntity|Full control of HTTP response|`ResponseEntity<User> return new ResponseEntity<>(user, HttpStatus.OK)`|

# ==Bean==
## 🧠 **1. What is Spring Framework?**

Spring is a **Java framework** that makes it easy to build **enterprise applications** by handling:

- Object creation and management
    
- Dependency Injection (DI)
    
- Web application development
    
- Data access and integration
    
- Security, AOP, Transactions, etc.
    

Spring provides **lightweight**, **loosely coupled**, and **testable** code through **IoC (Inversion of Control)** and **DI (Dependency Injection)**.

---

## ⚙️ **2. How Spring Works (Inversion of Control)**

Normally, you create objects manually:

`Car car = new Car();`

In Spring, you don’t create objects directly —  
Instead, you let **Spring Container** create and manage them.

This is called **Inversion of Control (IoC)**  
→ Control of object creation is **inverted** (given to the container).

---

## 🏗️ **3. Spring Container**

The **Spring Container** is the **core** of the Spring Framework.  
It:

- Creates objects (Beans)
    
- Manages their lifecycle
    
- Injects dependencies automatically
    

### 🔸 Types of Containers

1. **BeanFactory** → Basic container, lazy initialization
    
2. **ApplicationContext** → Advanced container, used in Spring Boot
    

Spring Boot automatically creates an `ApplicationContext` when your app runs.

---

## 🤝 **4. Dependency Injection (DI)**

Dependency Injection is a design pattern where:

- One object **depends** on another object
    
- Spring **injects** those dependencies automatically
    

### Example (Without DI):

`Car car = new Car(new Engine());`

### Example (With DI):

`@Autowired private Engine engine;`

➡ Spring automatically gives the `Engine` object to `Car`.

### 💡 Types of DI:

1. **Constructor Injection**
    
2. **Setter Injection**
    
3. **Field Injection** (via `@Autowired`)
    

---

## 🌿 **5. ==What is a Bean?**==

A **Bean** is simply an **object managed by the Spring Container**.  
It’s created, configured, and destroyed by Spring.

### Bean Lifecycle:

1. **Instantiation** → Bean is created
    
2. **Dependency Injection** → Dependencies are injected
    
3. **Initialization** → `@PostConstruct` runs
    
4. **Usage** → Bean is available
    
5. **Destruction** → `@PreDestroy` runs
    

---

## 🧩 **6. Ways to Create Beans**

|Method|Description|Example|
|---|---|---|
|`@Component`|Automatic bean detection|`@Component public class Student {}`|
|`@Service`|For service layer classes|`@Service public class StudentService {}`|
|`@Repository`|For DAO/persistence layer|`@Repository public class StudentRepository {}`|
|`@Controller`|For MVC controllers|`@Controller public class StudentController {}`|
|`@RestController`|For REST APIs (JSON/XML)|`@RestController public class ApiController {}`|
|`@Bean`|Manual bean registration|`@Bean public Student student() { return new Student(); }`|

---

## 🧱 **7. @Component vs @Bean**

|Feature|`@Component`|`@Bean`|
|---|---|---|
|Where used|On **class level**|On **method level** inside a `@Configuration` class|
|Who creates the object|Spring automatically detects & creates|You manually define and return the object|
|Used for|Your own classes|Third-party classes or custom config|
|Scanning required?|Yes (`@ComponentScan`)|No|
|Example|`@Component public class Student {}`|`@Bean public Student student() { return new Student(); }`|

### 🔹 Analogy:

- `@Component` → “Spring, find and create this automatically.”
    
- `@Bean` → “Spring, I’ll tell you **exactly how to create** this.”
    

---

## 🧩 **8. Common Annotations in Spring Boot**

|Annotation|Purpose|
|---|---|
|`@SpringBootApplication`|Entry point of Spring Boot app (enables auto configuration + component scan)|
|`@Component`|Generic Spring-managed class|
|`@Service`|Marks business/service layer class|
|`@Repository`|Marks persistence layer class|
|`@Controller`|Handles web requests (MVC)|
|`@RestController`|Returns JSON/XML (for APIs)|
|`@Autowired`|Performs dependency injection|
|`@Configuration`|Marks a class containing `@Bean` methods|
|`@Bean`|Manually defines and returns a bean object|

---

## 🧠 **9. When to Use What**

|Scenario|Use|
|---|---|
|You’re writing your own class|`@Component`, `@Service`, `@Repository`, `@Controller`|
|You need to register a third-party object|`@Bean`|
|You want to inject dependencies automatically|`@Autowired`|
|You want to customize bean creation logic|`@Bean` inside `@Configuration`|
# 🌿 **Example of a Bean in Spring Boot**

---

## 🧩 **1. Create a Normal Java Class**

Let’s say we have a simple class named `Student` — and we’ll turn it into a Spring-managed **bean**.

```
package com.example.demo;

public class Student {
    private String name;

    public Student(String name) {
        this.name = name;
    }

    public void show() {
        System.out.println("Student name: " + name);
    }
}

```

---

## ⚙️ **2. Create a Configuration Class with `@Bean`**

Now, we’ll manually register `Student` as a **bean** using `@Bean`.  
This is **manual bean creation**.

```
package com.example.demo;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class AppConfig {

    @Bean
    public Student studentBean() {
        // You manually create the object here 👇
        return new Student("Pratik");
    }
}

```

➡ `@Configuration` tells Spring that this class provides bean definitions.  
➡ `@Bean` tells Spring to **execute this method** and register the returned object as a **bean**.

---

## 🏃 **3. Use the Bean in Your Main Application**

Now, let’s use it in the main Spring Boot class.

```
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;

@SpringBootApplication
public class DemoApplication {

    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(DemoApplication.class, args);

        // Get the bean from Spring Container
        Student student = context.getBean(Student.class);
        student.show();
    }
}

```

### ✅ Output:

`Student name: Pratik`

---

## 🧠 **How This Works Behind the Scenes**

1. Spring Boot starts and creates an **ApplicationContext (Spring Container)**.
    
2. It looks at your `@Configuration` class (`AppConfig`).
    
3. It finds the method `@Bean public Student studentBean()`
    
4. Executes it → registers the returned object (`Student`) as a **Spring Bean**.
    
5. When you call `context.getBean(Student.class)` — Spring returns that same object.
    

---

## 🧱 **4. Example Using `@Component` (Auto Bean)**

Here’s how you can do the same thing **automatically** using `@Component` (no `@Bean` needed):

```
package com.example.demo;

import org.springframework.stereotype.Component;

@Component
public class Student {
    public void show() {
        System.out.println("Student Bean created automatically by Spring!");
    }
}

```

Now in your main class, just inject it:

`@Autowired private Student student;`

Or:

`Student student = context.getBean(Student.class); student.show();`

✅ Output:

`Student Bean created automatically by Spring!`

---

## 🧩 **5. Key Difference (Recap)**

|Aspect|`@Component`|`@Bean`|
|---|---|---|
|Type|Automatic Bean Creation|Manual Bean Creation|
|Used On|Class|Method inside `@Configuration`|
|Object Creation|Spring handles it|You define how it’s created|
|Example Use|Your own classes|Third-party or custom setup|
# ==🌱 **Spring Bean Lifecycle**==
## 🧠 **What It Means**

Every **Bean** in Spring goes through a specific **lifecycle** inside the **Spring Container** — from **creation to destruction**.  
Spring manages this whole process automatically, but you can **intervene at specific stages** if you want to run custom logic.

---

## ⚙️ **Full Lifecycle Stages**

Here’s the complete flow 👇

|Step|Stage|Description|
|---|---|---|
|1|**Instantiation**|Spring creates the bean instance (calls `new`)|
|2|**Populate Properties**|Injects dependencies (using `@Autowired`, constructor, etc.)|
|3|**Set Bean Name**|If implementing `BeanNameAware`, bean knows its name|
|4|**Set Bean Factory**|If implementing `BeanFactoryAware`, bean gets factory reference|
|5|**Pre-Initialization**|Runs `BeanPostProcessor` **before** initialization|
|6|**Initialization**|Executes `@PostConstruct` or `InitializingBean.afterPropertiesSet()`|
|7|**Post-Initialization**|Runs `BeanPostProcessor` **after** initialization|
|8|**Ready for Use**|Bean is available for the app|
|9|**Destruction**|On container shutdown, runs `@PreDestroy` or `DisposableBean.destroy()`|

---

## 🌿 **Simplified View**

`Create → Inject Dependencies → Init → Use → Destroy`

---

## 💻 **Example — Full Bean Lifecycle**

```
package com.example.demo;

import jakarta.annotation.PostConstruct;
import jakarta.annotation.PreDestroy;
import org.springframework.stereotype.Component;

@Component
public class Student {

    public Student() {
        System.out.println("1️⃣ Constructor: Student object created");
    }

    @PostConstruct
    public void init() {
        System.out.println("2️⃣ @PostConstruct: Initialization logic");
    }

    public void study() {
        System.out.println("3️⃣ Bean in use: Student is studying");
    }

    @PreDestroy
    public void destroy() {
        System.out.println("4️⃣ @PreDestroy: Cleanup before bean destruction");
    }
}

```

---

### 🏃 **Main Application**

```
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ConfigurableApplicationContext;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        ConfigurableApplicationContext context = SpringApplication.run(DemoApplication.class, args);

        Student student = context.getBean(Student.class);
        student.study();

        // Closing context to trigger @PreDestroy
        context.close();
    }
}

```

---

### ✅ **Output**

`1️⃣ Constructor: Student object created 2️⃣ @PostConstruct: Initialization logic 3️⃣ Bean in use: Student is studying 4️⃣ @PreDestroy: Cleanup before bean destruction`

---

## 🧩 **Alternative Lifecycle Hooks**

|Method|Interface|Purpose|
|---|---|---|
|`afterPropertiesSet()`|`InitializingBean`|Runs after all properties are set|
|`destroy()`|`DisposableBean`|Runs before destruction|
|`initMethod` / `destroyMethod`|In `@Bean`|Custom init/destroy methods|
|`@PostConstruct`|Annotation|Runs after dependency injection|
|`@PreDestroy`|Annotation|Runs before destruction|

---

### Example using `@Bean` init/destroy methods

```
@Configuration
public class AppConfig {

    @Bean(initMethod = "init", destroyMethod = "cleanup")
    public Student student() {
        return new Student();
    }
}

public class Student {
    public void init() {
        System.out.println("Bean init method called");
    }

    public void cleanup() {
        System.out.println("Bean destroy method called");
    }
}

```

---

## 🧾 **Summary**

|Phase|Description|Common Annotation/Method|
|---|---|---|
|1️⃣ Instantiation|Bean object created|Constructor|
|2️⃣ Dependency Injection|Dependencies injected|`@Autowired`|
|3️⃣ Initialization|Custom init logic|`@PostConstruct`, `afterPropertiesSet()`, `initMethod`|
|4️⃣ In Use|Bean used by app|Your business logic|
|5️⃣ Destruction|Cleanup before shutdown|`@PreDestroy`, `destroy()`, `destroyMethod`|
# ==Dependency Injection==
## 🧠 **1. What is Dependency Injection?**

Dependency Injection means the Spring container automatically provides the required objects (beans) to a class instead of the class creating them manually.

➡ In Spring, **the container (ApplicationContext)** provides these dependencies automatically.

---

### 🧩 Example (Without DI)
```
public class Student {
    private MathTeacher teacher = new MathTeacher(); // ❌ Tight coupling

    public void startStudy() {
        teacher.teach();
    }
}

```
Here, `Student` **creates** the `MathTeacher` itself using `new`.  
This makes it **tightly coupled** — you can’t easily replace `MathTeacher` with another teacher (like `ScienceTeacher`).

---

### ✅ Example (With DI)

```
@Component
public class Student {
    private final Teacher teacher;

    // Constructor injection
    @Autowired
    public Student(Teacher teacher) {
        this.teacher = teacher;
    }

    public void startStudy() {
        teacher.teach();
    }
}

```
```
@Component
public class MathTeacher implements Teacher {
    @Override
    public void teach() {
        System.out.println("Teaching Mathematics...");
    }
}

```
Now `Student` doesn’t create the teacher —  
Spring does! 💪  
The **dependency (Teacher)** is **injected** into the **Student** class automatically.

---

## 🧱 **2. Why Dependency Injection?**

|Problem Without DI|How DI Solves It|
|---|---|
|Tight coupling (hard to change code)|Loose coupling|
|Hard to test|Easier unit testing (use mocks)|
|Manual object creation|Automatic object management|
|Duplicated code|Centralized bean control (container)|

---

## ⚙️ **3. How Spring Handles DI**

When your app starts:

1. Spring scans your classes for annotations like `@Component`, `@Service`, `@Repository`
    
2. It creates all these **beans** and keeps them in the **ApplicationContext**
    
3. When it sees `@Autowired`, it **injects** the required bean automatically
    

---

## 💡 **4. Types of Dependency Injection in Spring**

|Type|Example|Description|
|---|---|---|
|**Constructor Injection**|✅ Recommended|Inject via constructor|
|**Setter Injection**|Inject via setter method||
|**Field Injection**|Inject directly into the field (less preferred)||

---

### ✅ **Constructor Injection**

```
@Component
public class Student {
    private final Teacher teacher;

    @Autowired
    public Student(Teacher teacher) {
        this.teacher = teacher;
    }

    public void study() {
        teacher.teach();
    }
}

```

➡ Most preferred — **immutable** and **testable**.

---

### ⚙️ **Setter Injection**

```
@Component
public class Student {
    private Teacher teacher;

    @Autowired
    public void setTeacher(Teacher teacher) {
        this.teacher = teacher;
    }
}

```

➡ Useful when dependency is **optional** or may change later.

---

### ⚡ **Field Injection (Quick but not ideal)**

`@Component public class Student {      @Autowired     private Teacher teacher; }`

➡ Simple, but **not recommended** for large applications or testing because it uses reflection.

---

## 🌱 **5. Example — Complete Flow**

```
@Component
class Engine {
    public void start() {
        System.out.println("Engine started...");
    }
}

@Component
class Car {
    private final Engine engine;

    @Autowired
    public Car(Engine engine) { // Constructor Injection
        this.engine = engine;
    }

    public void drive() {
        engine.start();
        System.out.println("Car is running...");
    }
}

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(DemoApplication.class, args);

        Car car = context.getBean(Car.class);
        car.drive();
    }
}

```

### ✅ Output:

`Engine started... Car is running...`

---

## 🧩 **6. What Happens Internally**

1. Spring scans all classes for annotations (`@Component`, etc.)
    
2. Creates beans (`Engine`, `Car`)
    
3. When creating `Car`, it sees it needs an `Engine`
    
4. Spring automatically **injects the Engine bean into Car**
    
5. Both objects are now **managed by the container**
    

---

## 🧱 **7. Difference Between IoC and DI**

|Concept|Meaning|
|---|---|
|**IoC (Inversion of Control)**|Framework controls the creation & lifecycle of objects|
|**DI (Dependency Injection)**|IoC technique where dependencies are provided instead of being created|

🧩 Simply put:

> **DI is a way to achieve IoC.**

---

## 🗣️ **Interview Tip**

> **Q:** What is Dependency Injection in Spring Boot?  
> **A:** It’s a design pattern where Spring automatically provides an object’s dependencies instead of the class creating them. It promotes loose coupling and easier testing. DI is implemented by the Spring IoC container using annotations like `@Autowired`, `@Component`, `@Service`, etc.

# Bean Scopes — Notes & Code Examples

**Purpose:** Quick reference notes explaining Spring bean scopes with concise definitions, when to use them, interview tips, and full code examples you can drop into a Spring Boot web app.

---

## 1. What is a Bean Scope?

A **bean scope** controls two things:

1. **How many instances** of a bean Spring creates.
    
2. **How long** each bean instance lives (its lifecycle).
    

Default scope in Spring is **`singleton`**.

---

## 2. Common Scopes (Summary Table)

|Scope|Instances|Lifetime|Typical use|
|---|---|---|---|
|`singleton`|1 per Spring container|Entire application lifecycle|Stateless services, repositories|
|`prototype`|New instance each request to container|Client responsible for destruction|Short-lived, stateful objects|
|`request`|1 per HTTP request|Duration of HTTP request|Request-specific data in web apps|
|`session`|1 per HTTP session|Duration of HTTP session|User-specific data across requests (e.g., shopping cart)|
|`application`|1 per ServletContext|Lifetime of web application|App-wide shared objects in web apps|
|`websocket`|1 per WebSocket session|WebSocket session lifecycle|State per WebSocket connection|

---

## 3. Important Notes

- `singleton` is the default.
    
- `prototype` beans are created each time you call `getBean()` or inject them — Spring does not manage their full lifecycle (you handle destruction).
    
- `request` and `session` scopes only work in a **web-aware** Spring application (Spring MVC / Spring Boot web).
    
- When injecting a `request` or `session` scoped bean into a `singleton` bean, use a scoped proxy: `@Scope(value = "request", proxyMode = ScopedProxyMode.TARGET_CLASS)`.
    

---

## 4. Full Code Examples

Below are minimal examples that you can paste into a Spring Boot project (`spring-boot-starter-web`).

### A. Singleton (default)

```java
// src/main/java/com/example/demo/service/SingletonService.java
package com.example.demo.service;

import org.springframework.stereotype.Service;

@Service // default scope = singleton
public class SingletonService {
    private final long createdAt = System.currentTimeMillis();

    public String info() {
        return "SingletonService createdAt=" + createdAt;
    }
}
```

### B. Prototype

```java
// src/main/java/com/example/demo/service/PrototypeService.java
package com.example.demo.service;

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope("prototype")
public class PrototypeService {
    private final long createdAt = System.currentTimeMillis();

    public String info() {
        return "PrototypeService createdAt=" + createdAt;
    }
}
```

**Controller to test singleton vs prototype**

```java
// src/main/java/com/example/demo/controller/TestController.java
package com.example.demo.controller;

import com.example.demo.service.SingletonService;
import com.example.demo.service.PrototypeService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class TestController {

    @Autowired
    private SingletonService singletonService;

    @Autowired
    private PrototypeService prototypeService; // note: injected once into controller

    @GetMapping("/test")
    public String test() {
        String s1 = singletonService.info();
        String p1 = prototypeService.info();
        return "singleton: " + s1 + "\nprototype (injected): " + p1;
    }
}
```

**Important:** The `prototypeService` above is injected into the controller only once — the controller (singleton) holds that prototype instance. To get a new prototype instance per request or call, use `ObjectFactory`, `Provider` (JSR-330), or lookup method injection.

Example using `ObjectFactory`:

```java
@Autowired
private ObjectFactory<PrototypeService> prototypeFactory;

@GetMapping("/test-new-proto")
public String testNewProto() {
    PrototypeService p = prototypeFactory.getObject();
    return p.info();
}
```

---

### C. Request Scope

```java
// src/main/java/com/example/demo/beans/RequestBean.java
package com.example.demo.beans;

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope("request")
public class RequestBean {
    private final long createdAt = System.currentTimeMillis();
    public String info() { return "RequestBean createdAt=" + createdAt; }
}
```

```java
// src/main/java/com/example/demo/controller/RequestController.java
package com.example.demo.controller;

import com.example.demo.beans.RequestBean;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class RequestController {
    @Autowired
    private RequestBean requestBean;

    @GetMapping("/request")
    public String request() {
        return requestBean.info();
    }
}
```

**Behaviour:** Each HTTP request to `/request` will get a different `createdAt` value because a new `RequestBean` instance is created per request.

---

### D. Session Scope

```java
// src/main/java/com/example/demo/beans/SessionBean.java
package com.example.demo.beans;

import org.springframework.context.annotation.Scope;
import org.springframework.stereotype.Component;

@Component
@Scope("session")
public class SessionBean {
    private final String id = "SessionBean@" + System.currentTimeMillis();
    public String id() { return id; }
}
```

```java
// src/main/java/com/example/demo/controller/SessionController.java
package com.example.demo.controller;

import com.example.demo.beans.SessionBean;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class SessionController {
    @Autowired
    private SessionBean sessionBean;

    @GetMapping("/session")
    public String session() {
        return sessionBean.id();
    }
}
```

**Behaviour:** Multiple requests from the _same browser_ (same session) will return the same id. Requests from a different browser or incognito window will return a different id.

---

### E. Injecting request/session beans into a singleton (use proxy)

When a singleton bean depends on a request/session bean, use a scoped proxy so Spring can inject a proxy that resolves the correct scoped instance at runtime.

```java
@Component
@Scope(value = "request", proxyMode = org.springframework.context.annotation.ScopedProxyMode.TARGET_CLASS)
public class RequestBeanProxy {
    private final long createdAt = System.currentTimeMillis();
    public String info() { return "RequestBeanProxy: " + createdAt; }
}
```

Now a singleton can `@Autowired` this proxy safely.

---

## 5. Quick Interview Answers

- **Default scope?** `singleton`.
    
- **When to use `prototype`?** When you need a new instance every time and want instance-level state.
    
- **When to use `request` or `session`?** In web apps for request-specific or session-specific state respectively.
    
- **How to inject request-scoped bean into singleton?** Use `proxyMode = ScopedProxyMode.TARGET_CLASS` or `ObjectFactory/Provider` to obtain instances lazily.
    

---

## 6. Extra Tips

- Prefer stateless `singleton` services for scalability and thread-safety.
    
- Keep `session` scope usage limited — storing large objects in session can cause memory pressure.
    
- For prototype beans used frequently, manage lifecycle carefully to avoid leaks.
    

---

==🧠 @ConditionalOnProperty== 
---------------------------------------------

🔹 Definition:
@ConditionalOnProperty is used in Spring Boot to enable or disable 
a bean or configuration based on the value of a property in 
application.properties or application.yml.

---------------------------------------------
🔹 Syntax:
@ConditionalOnProperty(
    name = "property.name",
    havingValue = "desiredValue",
    matchIfMissing = false
)

Parameters:
- name → The property name to check
- havingValue → The value which must match for the bean to load
- matchIfMissing → If true, bean loads even if property is missing

---------------------------------------------
🔹 Purpose:
- Conditionally create beans
- Useful for enabling/disabling modules
- Used for feature flags or environment-specific behavior

---------------------------------------------
🔹 Example: MySQL vs NoSQL Database

Step 1: application.properties
------------------------------
database.type=mysql
# change to nosql to switch

Step 2: DatabaseConfig.java
---------------------------
import org.springframework.boot.autoconfigure.condition.ConditionalOnProperty;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class DatabaseConfig {

    @Bean
    @ConditionalOnProperty(name = "database.type", havingValue = "mysql")
    public DatabaseConnection mysqlConnection() {
        return new DatabaseConnection("Connected to MySQL Database");
    }

    @Bean
    @ConditionalOnProperty(name = "database.type", havingValue = "nosql")
    public DatabaseConnection nosqlConnection() {
        return new DatabaseConnection("Connected to NoSQL Database");
    }
}

Step 3: DatabaseConnection.java
-------------------------------
public class DatabaseConnection {
    private String message;

    public DatabaseConnection(String message) {
        this.message = message;
    }

    public void connect() {
        System.out.println(message);
    }
}

Step 4: DemoApp.java
--------------------
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApp implements CommandLineRunner {

    @Autowired
    private DatabaseConnection databaseConnection;

    public static void main(String[] args) {
        SpringApplication.run(DemoApp.class, args);
    }

    @Override
    public void run(String... args) {
        databaseConnection.connect();
    }
}

---------------------------------------------
🔹 Output:
If database.type=mysql → "Connected to MySQL Database"
If database.type=nosql → "Connected to NoSQL Database"

---------------------------------------------
🔹 Important Points:
- Property should be inside:
  src/main/resources/application.properties
- Do NOT put it in pom.xml (pom is only for dependencies)

---------------------------------------------
🔹 Common Use Cases:
- Switching between databases (MySQL / NoSQL)
- Enabling or disabling features (email, logging, cache)
- Loading mock vs real services for testing
- Feature toggles and environment control

==🧠 @Profile== 
-------------------------------

🔹 Definition:
@Profile is a Spring annotation used to specify 
which environment (profile) a bean or configuration should be active in.

It helps to load specific beans only when a certain profile is active.

---------------------------------------------
🔹 Syntax:
@Profile("profileName")

Example:
@Profile("dev")
public class DevConfig { ... }

---------------------------------------------
🔹 Purpose:
- Used for **environment-based configurations** (e.g., dev, test, prod)
- Helps manage multiple environments without changing code
- Works with Spring’s "profiles" feature

---------------------------------------------
🔹 How Profiles Work:

You can define active profiles in:
application.properties
-----------------------
spring.profiles.active=dev

OR in application.yml
---------------------
spring:
  profiles:
    active: dev

You can also set it via command line:
java -jar app.jar --spring.profiles.active=prod

---------------------------------------------
🔹 Example: Database Configuration per Environment

application.properties
-----------------------
spring.profiles.active=dev

DatabaseConfig.java
-------------------
```
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.Profile;

@Configuration
public class DatabaseConfig {

    @Bean
    @Profile("dev")
    public DatabaseConnection devDatabaseConnection() {
        return new DatabaseConnection("Connected to DEV Database");
    }

    @Bean
    @Profile("prod")
    public DatabaseConnection prodDatabaseConnection() {
        return new DatabaseConnection("Connected to PROD Database");
    }
}
```

DatabaseConnection.java
-----------------------
```
public class DatabaseConnection {
    private String message;

    public DatabaseConnection(String message) {
        this.message = message;
    }

    public void connect() {
        System.out.println(message);
    }
}
```

DemoApp.java
------------
```
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApp implements CommandLineRunner {

    @Autowired
    private DatabaseConnection databaseConnection;

    public static void main(String[] args) {
        SpringApplication.run(DemoApp.class, args);
    }

    @Override
    public void run(String... args) {
        databaseConnection.connect();
    }
}
```

---------------------------------------------
🔹 Output:
If spring.profiles.active=dev → "Connected to DEV Database"
If spring.profiles.active=prod → "Connected to PROD Database"

---------------------------------------------
🔹 Difference Between @Profile and @ConditionalOnProperty:
| Feature | @Profile | @ConditionalOnProperty |
|----------|-----------|------------------------|
| Based on | Active environment profile | Specific property value |
| Used for | dev/test/prod setups | Feature toggles or options |
| Configured in | spring.profiles.active | application.properties (custom key) |
| Example | dev, prod | feature.enabled=true |

---------------------------------------------
🔹 Common Use Cases:
- Environment-specific database configs
- Logging settings per environment
- Mail or API service variations between dev/test/prod
- Switching between mock and real services

## ==1️⃣ What is AOP?==
[AOP Notes]([https://notebook.zohopublic.in/public/notes/dcr5z12bd30d9fbc2454e9881904115682227]())
- **AOP (Aspect-Oriented Programming)** helps you handle **cross-cutting concerns** like logging, security, transactions, caching, auditing, etc.
    
- It allows you to **add extra behavior** to your methods **without changing the business logic**.


**Example cross-cutting concerns:**

- Logging every method call
    
- Security checks before method execution
    
- Performance measurement
    
---
## 2️⃣ Key Terms

|Term|Meaning|
|---|---|
|**Aspect**|A class containing cross-cutting logic (advice + pointcut)|
|**Advice**|Action to perform (before, after, around, etc.)|
|**Pointcut**|Expression that selects which methods trigger advice|
|**JoinPoint**|A point during execution of a method (target method call)|
|**Proxy**|Object created by Spring that wraps the target class to run aspects|

---

## 3️⃣ AOP Annotations

|Annotation|When it runs|Example|
|---|---|---|
|`@Aspect`|Marks a class as an Aspect|`@Aspect public class LoggingAspect {}`|
|`@Before`|Before target method|`@Before("execution(* com.app.service.*.*(..))")`|
|`@After`|After target method (any outcome)|`@After("execution(* com.app.service.*.*(..))")`|
|`@AfterReturning`|After successful execution|`@AfterReturning("execution(* com.app.service.*.*(..))")`|
|`@AfterThrowing`|After exception thrown|`@AfterThrowing("execution(* com.app.service.*.*(..))")`|
|`@Around`|Before & after, can modify result|`@Around("execution(* com.app.service.*.*(..))")`|
|`@Pointcut`|Defines reusable pointcut|`@Pointcut("execution(* com.app.service.*.*(..))")`|

---

## 4️⃣ Pointcut Expressions (How to select methods)

| Type            | Matches                                                                                                          | Example                                |
| --------------- | ---------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| `execution()`   | Matches a particular method in a particular class                                                                | `execution(* com.app.service.*.*(..))` |
| `within()`      | Methods inside class/package                                                                                     | `within(com.app.controller.*)`         |
| `this()`        | Proxy object type                                                                                                | `this(UserService)`                    |
| `target()`      | Target object type                                                                                               | `target(UserService)`                  |
| `args()`        | Matches any method with particular parameters and that parameters class is annotated with particular annotation. | `args(String,int)`                     |
| `@annotation()` | Matches any method that is annotated with given annotation                                                       | `@annotation(AdminOnly)`               |
| `@within()`     | matches any method in a Class which has  specific annotation                                                     | `@within(RestController)`              |
| `@target()`     | Target class annotation                                                                                          | `@target(Service)`                     |
| `bean()`        | Bean name                                                                                                        | `bean(userService)`                    |

**Modifiers `*`**:

- `*` in return type → any return type
    
- `*` in method name → any method
    
- **Private/protected methods are NOT intercepted** by default proxy-based Spring AOP
    

---

## 5️⃣ Advice Examples

### 🔹 Before Advice

```
@Aspect
@Component
public class LoggingAspect {

    @Before("execution(* com.app.service.*.*(..))")
    public void logBefore() {
        System.out.println("Before service method");
    }
}

```

---

### 🔹 After Returning Advice

```
@AfterReturning("execution(* com.app.service.*.*(..))")
public void logAfterReturning() {
    System.out.println("Method executed successfully");
}

```

---

### 🔹 After Throwing Advice

```
@AfterThrowing(pointcut = "execution(* com.app.service.*.*(..))", throwing = "ex")
public void logException(Exception ex) {
    System.out.println("Exception: " + ex.getMessage());
}

```

---

### 🔹 Around Advice

```
@Around("execution(* com.app.service.*.*(..))")
public Object logExecutionTime(ProceedingJoinPoint joinPoint) throws Throwable {
    long start = System.currentTimeMillis();
    Object result = joinPoint.proceed(); // call actual method
    long end = System.currentTimeMillis();
    System.out.println(joinPoint.getSignature() + " executed in " + (end - start) + "ms");
    return result;
}

```

---

## 6️⃣ Using @annotation

```
@Before("@annotation(com.example.security.AdminOnly)")
public void checkAdmin() {
    System.out.println("Admin-only method called");
}

```

- Runs **only for methods annotated with `@AdminOnly`**
    
- **Does not run automatically** — method is executed only when called
    
- `@within` → class-level annotation; `@annotation` → method-level annotation
    

---

## 7️⃣ Example Aspect with Pointcut Method

```
@Aspect
@Component
public class LoggingAspect {

    // reusable pointcut
    @Pointcut("execution(* com.app.service.*.*(..))")
    public void serviceLayer() {}

    @Before("serviceLayer()")
    public void logBefore() {
        System.out.println("Before service method");
    }

    @AfterReturning("serviceLayer()")
    public void logAfter() {
        System.out.println("After service method");
    }
}

```

---

## 8️⃣ How it works (Proxy)

```
Client → Proxy (wraps target) → Target method

1. Client calls method on bean
2. Proxy intercepts
3. Proxy checks pointcut match
4. If matched, advice runs (before/after/around)
5. Target method executes
6. After advice runs (if any)

```

---

## 9️⃣ Real-world Use Cases

|Use Case|Example|
|---|---|
|Logging|Log every method in service layer|
|Security|Check JWT / role before method (`@annotation(AdminOnly)`)|
|Transactions|`@Transactional` internally uses AOP|
|Performance|Measure method execution time with `@Around`|
|Caching|`@Cacheable` / `@CacheEvict` (Spring AOP-based)|
|Exception Handling|Catch & log exceptions centrally|
|Auditing|Track who changed data (DB)|
### ==💡 What is `@Transactional`?==

> The `@Transactional` annotation in Spring is used to **manage database transactions automatically** (Declarative Transaction Management).

It tells Spring that the **method or class** should be executed **within a transaction context** —  
either start a new transaction or join an existing one.

---

### 🧱 **Basic Definition**

`@Transactional public void transferMoney() {     // Database operations }`

➡️ If any exception occurs in this method, the **entire transaction is rolled back** automatically.  
➡️ If successful, the **changes are committed** to the database.

---

## ⚙️ **Key Features**

|Feature|Description|
|---|---|
|**Atomicity**|All or nothing — if one fails, everything rolls back.|
|**Consistency**|Keeps data consistent across operations.|
|**Isolation**|Controls how concurrent transactions affect each other.|
|**Durability**|Once committed, data stays saved even after crash.|

---

## 🧠 **Where You Can Use `@Transactional`**

- On **methods**
    
- On **classes** (applies to all public methods inside that class)
    
- Works with both **Service** and **Repository** layers

## 🧩 Types of Transaction Management in Spring

### **1. Programmatic Transaction Management**

👉 You **manually control** the transaction in your code.

You decide **when to begin, commit, or roll back** a transaction.

#### 🧠 Example:

```
@Service
public class AccountService {

    @Autowired
    private PlatformTransactionManager transactionManager;

    public void transferMoney() {
        DefaultTransactionDefinition def = new DefaultTransactionDefinition();
        TransactionStatus status = transactionManager.getTransaction(def);
        try {
            // Your DB operations here
            // ...
            transactionManager.commit(status);
        } catch (Exception e) {
            transactionManager.rollback(status);
            throw e;
        }
    }
}

```

✅ **Advantage**: Full control over transaction flow.  
❌ **Disadvantage**: More boilerplate code — not recommended for most cases.

---

### **2. Declarative Transaction Management (using `@Transactional`)**

👉 You **declare** transaction boundaries using annotations, and Spring manages them automatically.

#### 🧠 Example:

```
@Transactional
public void transferMoney() {
    // DB operations
}
```

✅ **Advantage**: Clean, less code, easier to maintain.  
❌ **Disadvantage**: Less granular control (Spring decides the flow).

## 🔄 What is Transaction Propagation?

When one **transactional method calls another transactional method**,  
**Propagation** defines how these transactions should behave together.

In short:

> It decides whether the **called method** should run in the **same transaction** or **start a new one**.

---

## 🧠 Real-life Analogy

Imagine you’re buying groceries 🛒 and you’re paying with one **wallet (transaction)**.

- If your friend adds an item to your bill, it’s part of your same payment → **same transaction (REQUIRED)**
    
- If your friend pays separately → **new transaction (REQUIRES_NEW)**
    
- If your friend just checks prices but doesn’t buy → **no transaction (NOT_SUPPORTED)**
    

---

Now let’s understand **each type** with **simple code examples** 👇

---

## 🧩 Example Setup

We have two service classes:

```
@Service
public class ServiceA {
    @Autowired
    private ServiceB serviceB;

    @Transactional(propagation = Propagation.REQUIRED)
    public void methodA() {
        System.out.println("Start A");
        serviceB.methodB();
        System.out.println("End A");
    }
}

```

```
@Service
public class ServiceB {

    @Transactional(propagation = Propagation.REQUIRED)
    public void methodB() {
        System.out.println("Inside B");
    }
}

```

---

## 🧱 Propagation Types Explained

---

### 🟢 1. `REQUIRED` (Default)

> If a transaction exists, join it; otherwise, create a new one.

```
// A has @Transactional(REQUIRED)
// B has @Transactional(REQUIRED)

```

➡️ If `methodA()` starts a transaction,  
`methodB()` will **join the same transaction**.

✅ If an exception occurs in B → **A and B both roll back**.

🧩 **Think:** “Use my existing wallet.”

---

### 🔵 2. `REQUIRES_NEW`

> Always create a **new independent transaction** — suspends the current one.

```
@Transactional(propagation = Propagation.REQUIRES_NEW)
public void methodB() {
    System.out.println("Inside B");
}
```
➡️ When `methodA()` calls `methodB()`:

- A’s transaction pauses
    
- B runs in its **own new transaction**
    

✅ If B fails → only **B rolls back**, A continues.  
✅ If A fails later → only **A rolls back**, not B.

🧩 **Think:** “Use your own wallet, I’ll pay mine separately.”

---

### 🟣 3. `SUPPORTS`

> If a transaction exists, join it. If not, run **without** a transaction.

```
@Transactional(propagation = Propagation.SUPPORTS)
public void methodB() {
    System.out.println("Inside B");
}
```

✅ If called from a transactional method → joins it.  
✅ If called alone → just runs normally (no transaction).

🧩 **Think:** “I’ll join your wallet if you’re paying, else I’ll just window shop.”

---

### 🟠 4. `NOT_SUPPORTED`

> Don’t run inside a transaction. Suspend any existing one.

```
@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void methodB() {
    System.out.println("Inside B");
}
```

✅ Even if A has a transaction, B will **pause** it and run **without** one.

🧩 **Think:** “Pause your payment, I’m just looking.”

---

### 🔴 5. `MANDATORY`

> Must run **inside an existing transaction**, otherwise throws an error.

```
@Transactional(propagation = Propagation.MANDATORY)
public void methodB() {
    System.out.println("Inside B");
}
```

✅ Works only if called **inside another transactional method**.  
❌ If called alone → `IllegalTransactionStateException`.

🧩 **Think:** “You must have a wallet — I can’t start my own.”

---

### ⚪ 6. `NEVER`

> Must **not** run inside a transaction, else throw exception.

```
@Transactional(propagation = Propagation.NEVER)
public void methodB() {
    System.out.println("Inside B");
}
```

✅ If no transaction → runs fine.  
❌ If called from A (which has a transaction) → throws exception.

🧩 **Think:** “I refuse to join any group payment.”

---

### 🟡 7. `NESTED`

> Starts a **sub-transaction** within the main one — can roll back independently.

```
@Transactional(propagation = Propagation.NESTED)
public void methodB() {
    System.out.println("Inside B");
}
```

✅ B’s rollback doesn’t affect A.  
✅ But if A rolls back → B also rolls back.

🧩 **Think:** “I’ll pay from my pocket, but if you cancel, I’ll cancel too.”

## 💡 What is Isolation Level?

> Isolation level defines **how much one transaction is allowed to see or affect other concurrent transactions**.

In simple words:

> It controls how **data consistency** is maintained when **multiple users or transactions** access the same data **at the same time**.

---

### 🧠 Real-life Analogy

Imagine 2 people using the same **bank account** at the same time 🏦

- You → checking balance
    
- Someone else → withdrawing money
    

Isolation level decides whether you both **see the same data** or not.

---

## ⚙️ Why Isolation Levels Exist?

Databases often run **many transactions in parallel** for speed.  
But concurrency can create problems like:

|Problem|Example|
|---|---|
|**Dirty Read**|Read uncommitted data of another transaction|
|**Non-repeatable Read**|Same query gives different results in same transaction|
|**Phantom Read**|New rows appear/disappear between two reads|
# ⚠️ The 3 Major Problems in Transactions

|Problem|Happens When|Prevented By|
|---|---|---|
|🟡 **Dirty Read**|Reading uncommitted changes|READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE|
|🟠 **Non-Repeatable Read**|Data changes between two reads|REPEATABLE_READ, SERIALIZABLE|
|🔴 **Phantom Read**|New rows appear/disappear|SERIALIZABLE|

---

## 🟡 1. Dirty Read

### 💬 What It Means

A transaction **reads data** that has been **modified but not committed** by another transaction.  
If that other transaction **rolls back**, the first transaction ends up with **invalid (dirty) data**.

### 🏦 Example (Bank)

- **T1 (You)**: Checking your balance → ₹1000
    
- **T2 (Another User)**: Withdraws ₹500 → Updates balance to ₹500 but **not committed** yet
    
- **T1 reads again** → sees ₹500
    
- **T2 rolls back** → actual balance still ₹1000
    

👉 You saw ₹500 temporarily — that was **dirty data**.

---

### 🧩 SQL-style Example

```
-- Transaction 1
BEGIN;
SELECT balance FROM account WHERE id = 1;  -- returns 1000

-- Transaction 2
BEGIN;
UPDATE account SET balance = 500 WHERE id = 1;  -- not committed yet

-- Transaction 1 (still running)
SELECT balance FROM account WHERE id = 1;  -- returns 500 (dirty read)

-- Transaction 2
ROLLBACK;  -- undo changes
```
Now T1 saw a value (₹500) that never actually existed permanently.

---

### 🧠 Easy Analogy

> “You peeked at your friend’s exam paper before they finished writing — and they later erased the answer.”

---

### ✅ Solution

Use **READ_COMMITTED** or higher isolation level.  
That ensures transactions **only see committed data**.

---

## 🟠 2. Non-Repeatable Read

### 💬 What It Means

A transaction reads **the same record twice**, but the **data changes in between** due to another transaction.

So your second read returns **different results** — not repeatable.

---

### 🏦 Example (Bank)

- **T1 (You)**: Reads balance = ₹1000
    
- **T2 (Another)**: Commits update → sets balance = ₹500
    
- **T1 reads again** → now balance = ₹500
    

Same query gave **different results** in the same transaction.

---

### 🧩 SQL Example

```
-- Transaction 1
BEGIN;
SELECT balance FROM account WHERE id = 1;  -- 1000

-- Transaction 2
BEGIN;
UPDATE account SET balance = 500 WHERE id = 1;
COMMIT;

-- Transaction 1 (still running)
SELECT balance FROM account WHERE id = 1;  -- 500 (non-repeatable)
COMMIT;

```

---

### 🧠 Analogy

> “You checked your marks online twice — the second time it changed because the teacher updated it.”

---

### ✅ Solution

Use **REPEATABLE_READ** or **SERIALIZABLE**.  
They ensure rows you’ve read can’t be changed by others until your transaction completes.

---

## 🔴 3. Phantom Read

### 💬 What It Means

A transaction runs a **query that returns multiple rows** (like `SELECT * FROM accounts WHERE balance > 1000`),  
but another transaction **inserts or deletes rows** that affect that result set.

So when you run the same query again, **new “phantom” rows appear or disappear**.

---

### 🏦 Example (Bank)

- **T1:** Reads all customers with balance > ₹1000 → gets 3 rows
    
- **T2:** Inserts a new customer with balance ₹1500 and commits
    
- **T1:** Runs the same query again → gets 4 rows
    

👉 The extra record is called a **phantom row**.

---

### 🧩 SQL Example

```
-- Transaction 1
BEGIN;
SELECT * FROM account WHERE balance > 1000;  -- returns 3 rows

-- Transaction 2
BEGIN;
INSERT INTO account (id, balance) VALUES (10, 1500);
COMMIT;

-- Transaction 1
SELECT * FROM account WHERE balance > 1000;  -- returns 4 rows (phantom read)
COMMIT;
```

---

### 🧠 Analogy

> “You counted how many people are in the room — someone quietly walked in later. When you count again, the number changed.”

---

### ✅ Solution

Only **SERIALIZABLE** isolation level prevents this by locking even the **range of rows**, not just individual ones.

---
## 🧩 The Four Isolation Levels (from lowest to highest)

|Level|Prevents|Allows|Consistency|Performance|
|---|---|---|---|---|
|1️⃣ **READ_UNCOMMITTED**|Nothing|Dirty, Non-repeatable, Phantom reads|❌ Low|✅ Fast|
|2️⃣ **READ_COMMITTED**|Dirty reads|Non-repeatable, Phantom reads|⚖️ Medium|⚖️ Medium|
|3️⃣ **REPEATABLE_READ**|Dirty + Non-repeatable reads|Phantom reads|✅ High|⏳ Slower|
|4️⃣ **SERIALIZABLE**|Dirty, Non-repeatable, Phantom|None|🧱 Highest|🐢 Slowest|

---

## 🧠 Let’s Understand Each One with an Example

Imagine two transactions (T1 and T2):

|Time|Transaction 1 (T1)|Transaction 2 (T2)|
|---|---|---|
|Step 1|Reads balance = ₹1000||
|Step 2||Updates balance to ₹500 but not committed|
|Step 3|Reads balance again → ?||

---

### 🟢 1. READ_UNCOMMITTED

> You can **read uncommitted (dirty)** data from another transaction.

So T1 sees balance = ₹500 even though T2 hasn’t committed yet.

If T2 rolls back → T1 saw **wrong data** ❌

🧠 **Think:** “Peek into someone’s notebook before they finish writing.”

---

### 🔵 2. READ_COMMITTED (Default in most databases)

> You can **only read committed data**.

T1 will not see T2’s update until T2 commits.  
✅ Dirty reads prevented.  
❌ But if T2 commits later, T1’s next read might show different value → **non-repeatable read**.

🧠 **Think:** “I’ll only read after you submit your notebook.”

---

### 🟣 3. REPEATABLE_READ (Default in MySQL)

> Once T1 reads data, no one can change it until T1 finishes.

✅ Prevents dirty and non-repeatable reads.  
❌ But new rows can still appear (phantom reads).

🧠 **Think:** “Freeze the rows I read.”

---

### 🔴 4. SERIALIZABLE

> Transactions execute **one after another** (like in a queue).  
> No interference at all.

✅ 100% consistent  
❌ Very slow, as it locks entire tables.

🧠 **Think:** “Only one person allowed in the bank at a time.”

---

## ⚙️ Setting Isolation Level in Spring

You can set it in the `@Transactional` annotation:

```
@Transactional(isolation = Isolation.READ_COMMITTED)
public void processTransaction() {
    // DB operations
}
```

Spring uses constants from:

`import org.springframework.transaction.annotation.Isolation;`

Available values:

- `Isolation.DEFAULT`
    
- `Isolation.READ_UNCOMMITTED`
    
- `Isolation.READ_COMMITTED`
    
- `Isolation.REPEATABLE_READ`
    
- `Isolation.SERIALIZABLE`

## 💡 What is ==Programmatic Transaction Management==?

**Programmatic Transaction Management** means

> You **manually control** the transaction in your Java code —  
> explicitly starting, committing, or rolling back transactions yourself.

So instead of letting Spring handle it with `@Transactional`,  
**you decide when to start and end** the transaction in your logic.

---

### 🧠 Simple Definition

> You use code like `transactionManager.getTransaction()`,  
> `transactionManager.commit()`, and `transactionManager.rollback()` manually.

---

## ⚙️ When do we use it?

✅ When you need **very fine-grained control**,  
like committing part of a transaction or conditionally rolling back only certain parts.

❌ But it’s usually **not recommended** for normal apps — too much boilerplate code.  
Declarative (`@Transactional`) is preferred 99% of the time.

---

## 🧩 Example

Let’s say you have a banking system where you transfer money from one account to another.

---

### 💬 Example without transaction (bad)

```
public void transferMoney() {
    accountRepository.debit("A", 1000);
    accountRepository.credit("B", 1000);
}
```

If the debit succeeds but the credit fails → inconsistent state. ❌

---

### ✅ Example with Programmatic Transaction

```
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;
import org.springframework.transaction.PlatformTransactionManager;
import org.springframework.transaction.TransactionStatus;
import org.springframework.transaction.support.DefaultTransactionDefinition;

@Service
public class BankService {

    @Autowired
    private PlatformTransactionManager transactionManager;

    @Autowired
    private AccountRepository accountRepository;

    public void transferMoney(String from, String to, double amount) {

        // 1️⃣ Define transaction
        DefaultTransactionDefinition def = new DefaultTransactionDefinition();
        TransactionStatus status = transactionManager.getTransaction(def);

        try {
            // 2️⃣ Execute DB operations
            accountRepository.debit(from, amount);
            accountRepository.credit(to, amount);

            // 3️⃣ If everything is fine → commit
            transactionManager.commit(status);
            System.out.println("✅ Transaction committed successfully.");

        } catch (Exception e) {
            // 4️⃣ If any error → rollback
            transactionManager.rollback(status);
            System.out.println("❌ Transaction rolled back due to: " + e.getMessage());
        }
    }
}
```

---

## 🔍 Explanation

1. **`PlatformTransactionManager`** — The main Spring interface for handling transactions manually.
    
2. **`DefaultTransactionDefinition`** — Defines basic properties of the transaction.
    
3. **`TransactionStatus`** — Represents the current transaction (active or not).
    
4. You manually call:
    
    - `transactionManager.getTransaction(def)` → start
        
    - `transactionManager.commit(status)` → commit
        
    - `transactionManager.rollback(status)` → rollback
        

---

## ⚖️ Declarative vs Programmatic — Quick Comparison

|Feature|Declarative (`@Transactional`)|Programmatic (`PlatformTransactionManager`)|
|---|---|---|
|**Control**|Spring manages automatically|You manually control|
|**Code Complexity**|Very simple, annotation-based|More verbose and manual|
|**Usage**|99% of normal cases|When you need fine control|
|**Propagation**|Supported (`Propagation.REQUIRED`, etc.)|❌ Not applicable|
|**Rollback Handling**|Automatic|You handle manually|


### ==🔹 What is `@Async`?==

[Notes](https://notebook.zohopublic.in/public/notes/dcr5zd72620f1d2574b40a39fe1b017931423)

`@Async` allows methods to **run in a separate background thread** — without blocking the main thread.  
It helps execute time-consuming tasks **asynchronously**.

---

### 🧩 **Simplest Example**

```
@SpringBootApplication
@EnableAsync // Enables async support
public class AsyncExampleApp {
    public static void main(String[] args) {
        SpringApplication.run(AsyncExampleApp.class, args);
    }
}

```

```
@Service
public class EmailService {

    @Async
    public void sendEmail(String userEmail) {
        System.out.println("Sending email to " + userEmail + 
            " - Thread: " + Thread.currentThread().getName());
        try { Thread.sleep(3000); } catch (Exception e) {}
        System.out.println("Email sent to " + userEmail);
    }
}
```

```
@RestController
public class MailController {

    @Autowired
    private EmailService emailService;

    @GetMapping("/send")
    public String send() {
        System.out.println("Main Thread: " + Thread.currentThread().getName());
        emailService.sendEmail("test@gmail.com");
        System.out.println("Main thread continues...");
        return "Email sending in background!";
    }
}
```

🧾 **Output Example**

```
Main Thread: http-nio-8080-exec-1
Main thread continues...
Sending email to test@gmail.com - Thread: task-1
Email sent to test@gmail.com
```

✅ **Main thread and async thread run side by side!**

---

### ⚙️ **Why Async?**

- Prevents blocking main thread (e.g., web request)
    
- Ideal for background tasks → email, file upload, report generation, etc.
    
- Improves performance and responsiveness
    

---

## 🧵 **Executors in Spring (Thread Managers)**

When `@Async` runs, Spring needs an **Executor** to manage threads.

---

### 🔸 1. **SimpleAsyncTaskExecutor**

- Creates a **new thread for every task**
    
- **No thread pooling**
    
- Light-weight but not efficient for large apps
    

```
SimpleAsyncTaskExecutor executor = new SimpleAsyncTaskExecutor();
executor.execute(() -> System.out.println("Task running"));
```

🟡 Use only for testing or very small workloads.

---

### 🔸 2. **ThreadPoolTaskExecutor** ✅ _(Best for Spring Boot)_

- Uses a **pool of reusable threads**
    
- Supports tuning: corePoolSize, maxPoolSize, queueCapacity, etc.
    
- Integrates with Spring lifecycle and `@Async`
    

```
@Configuration
@EnableAsync
public class AsyncConfig {
    @Bean(name = "customExecutor")
    public Executor taskExecutor() {
        ThreadPoolTaskExecutor executor = new ThreadPoolTaskExecutor();
        executor.setCorePoolSize(3);
        executor.setMaxPoolSize(6);
        executor.setQueueCapacity(20);
        executor.setThreadNamePrefix("Async-Thread-");
        executor.initialize();
        return executor;
    }
}
```

Usage:

`@Async("customExecutor") public void task() { ... }`

🟢 **Recommended for production.**

---

### 🔸 3. **ThreadPoolExecutor**

- Core **Java class** from `java.util.concurrent`
    
- `ThreadPoolTaskExecutor` internally uses this
    
- Use if you want **manual thread pool control**
    

```
ExecutorService executor = new ThreadPoolExecutor(
    2, 5, 10, TimeUnit.SECONDS, new LinkedBlockingQueue<>()
);
executor.execute(() -> System.out.println("Task running"));
```

---

### 🔸 4. **SyncTaskExecutor**

- Runs tasks **in the same thread (synchronously)**
    
- No async behavior, mainly for testing
    
```SyncTaskExecutor executor = new SyncTaskExecutor();
executor.execute(() -> System.out.println("Runs in main thread"));
```

---

## ⚖️ **Comparison Table**

|Executor|Reuses Threads|Thread Pool|Async?|Suitable For|
|---|---|---|---|---|
|`SimpleAsyncTaskExecutor`|❌ No|❌ No|✅ Yes|Small tasks/testing|
|`ThreadPoolTaskExecutor`|✅ Yes|✅ Yes|✅ Yes|🌟 Best for Spring Boot|
|`ThreadPoolExecutor`|✅ Yes|✅ Yes|✅ Yes|Custom Java configs|
|`SyncTaskExecutor`|❌ N/A|❌ N/A|❌ No|Testing only|

---

## 🧠 **`ThreadPoolTaskExecutor` vs `ThreadPoolExecutor`**

|Feature|`ThreadPoolTaskExecutor`|`ThreadPoolExecutor`|
|---|---|---|
|Origin|Spring|Java core|
|Integration|Fully integrated with Spring|Standalone|
|Lifecycle management|Auto-shutdown on context close|Manual shutdown|
|Configuration|Easy setters|Complex constructor|
|Best for|Spring Boot apps|Custom / non-Spring code|

✅ **Recommended in Spring Boot:** `ThreadPoolTaskExecutor`

---

## 🧩 **Tuning Tips**

- **CPU-bound tasks** → `corePoolSize ≈ CPU cores`
    
- **I/O-bound tasks** → `corePoolSize ≈ 2 × CPU cores`
    
- Use `CallerRunsPolicy` for graceful degradation
    
- Set:
    
    `executor.setWaitForTasksToCompleteOnShutdown(true); executor.setAwaitTerminationSeconds(30);`
    

---

## 🧭 **In short**

|Concept|Meaning|
|---|---|
|`@Async`|Runs method in background thread|
|`@EnableAsync`|Enables async support|
|**Executor**|Manages async threads|
|`ThreadPoolTaskExecutor`|Best choice for Spring Boot|
|Benefit|Frees main thread, improves responsiveness|

## 🚀 1️⃣ What is an ==Interceptor==?

An **Interceptor** in Spring Boot is used to **intercept HTTP requests and responses** before or after they reach the **controller**.

You can run custom logic:

- Before the controller method executes
    
- After the controller executes
    
- After the entire request completes
---
## 🧠 2️⃣ Why Use Interceptors?

Common use cases:

- 🔐 Authentication / Authorization
    
- 🧾 Logging & Auditing
    
- ⏱ Performance measurement (execution time)
    
- 🧭 Request modification
    
- 🧹 Resource cleanup

---

## ⚙️ 3️⃣ Lifecycle Methods in `HandlerInterceptor`

|Method|When it runs|Purpose|
|---|---|---|
|`preHandle()`|Before Controller executes|Validate request, check auth, log|
|`postHandle()`|After Controller executes (before response)|Modify response or model|
|`afterCompletion()`|After complete request|Cleanup, logging, metrics|

---
## 🧱 4️⃣ Steps to Create an Interceptor

---
### **Step 1 — Create an Interceptor Class**

```
package com.example.demo.interceptor;

import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;
import org.springframework.web.servlet.HandlerInterceptor;

@Component
public class MyInterceptor implements HandlerInterceptor {

    // 1️⃣ Runs before controller
    @Override
    public boolean preHandle(HttpServletRequest request,
                             HttpServletResponse response,
                             Object handler) throws Exception {
        System.out.println("🚀 PreHandle: Before Controller - " + request.getRequestURI());
        return true; // true = continue, false = block
    }

    // 2️⃣ Runs after controller method, before view rendering
    @Override
    public void postHandle(HttpServletRequest request,
                           HttpServletResponse response,
                           Object handler,
                           org.springframework.web.servlet.ModelAndView modelAndView) throws Exception {
        System.out.println("✅ PostHandle: After Controller");
    }

    // 3️⃣ Runs after the complete request finishes
    @Override
    public void afterCompletion(HttpServletRequest request,
                                HttpServletResponse response,
                                Object handler,
                                Exception ex) throws Exception {
        System.out.println("🏁 AfterCompletion: Request Completed");
    }
}

```

---

### **Step 2 — Register Interceptor in Config**

```
package com.example.demo.config;

import com.example.demo.interceptor.MyInterceptor;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
public class WebConfig implements WebMvcConfigurer {

    @Autowired
    private MyInterceptor myInterceptor;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(myInterceptor)
                .addPathPatterns("/api/**")          // apply to specific routes
                .excludePathPatterns("/api/login");  // exclude specific routes
    }
}

```

---

### **Step 3 — Create a Simple Controller**

```
package com.example.demo.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class TestController {

    @GetMapping("/api/hello")
    public String hello() {
        System.out.println("👋 Inside Controller");
        return "Hello from Controller!";
    }
}

```

---

### **Step 4 — Output When You Hit `/api/hello`**

```
🚀 PreHandle: Before Controller - /api/hello
👋 Inside Controller
✅ PostHandle: After Controller
🏁 AfterCompletion: Request Completed

```

---

## 🧩 5️⃣ Creating Custom Interceptor (e.g., Authentication Interceptor)

You can build your own custom interceptor by adding logic inside `preHandle()`.

Example — JWT / API Key Authentication Interceptor 👇

```
package com.example.demo.interceptor;

import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;
import org.springframework.web.servlet.HandlerInterceptor;

@Component
public class AuthInterceptor implements HandlerInterceptor {

    @Override
    public boolean preHandle(HttpServletRequest request,
                             HttpServletResponse response,
                             Object handler) throws Exception {

        String apiKey = request.getHeader("X-API-KEY");

        if ("secret123".equals(apiKey)) {
            System.out.println("✅ Authorized Request");
            return true;
        } else {
            System.out.println("❌ Unauthorized Access");
            response.setStatus(HttpServletResponse.SC_UNAUTHORIZED);
            response.getWriter().write("Unauthorized Request");
            return false;
        }
    }
}

```

Then register it in config as usual:

```
@Configuration
public class InterceptorConfig implements WebMvcConfigurer {

    @Autowired
    private AuthInterceptor authInterceptor;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(authInterceptor)
                .addPathPatterns("/api/secure/**");
    }
}

```

---

### ✅ Output Example

If you call `/api/secure/data` without header:

`❌ Unauthorized Access HTTP 401 Unauthorized`

If you call with header `X-API-KEY: secret123`:

`✅ Authorized Request Response: Sensitive Data Accessed ✅`

## 🌐 **1️⃣ What is a ==Filter==?**
[Filter](https://notebook.zohopublic.in/public/notes/dcr5z502a3a0746974f36b75a50729b691d58)
A **Filter** is a component that intercepts HTTP requests and responses **before** they reach the Spring MVC layer (DispatcherServlet) or **after** the response is generated.

It is part of the **Servlet API** and runs inside the **Servlet Container (Tomcat)**.

📌 **Think of it like a gatekeeper** — checking every request entering or leaving your application.

---

## ⚙️ **2️⃣ Purpose of Filters**

|Purpose|Example|
|---|---|
|🔐 Authentication|Validate tokens / API keys before request processing|
|🧾 Logging|Log request and response details|
|⚡ Pre/Post Processing|Add headers, wrap responses, compress data|
|🚫 Blocking Requests|Restrict access to certain URLs/IPs|
|🌍 CORS|Handle cross-origin resource sharing|

---

## 🔩 **3️⃣ Filter Interface**

Filters implement the `javax.servlet.Filter` interface.

### Main method:

```
void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
        throws IOException, ServletException;

```

- `request` → incoming request
    
- `response` → outgoing response
    
- `chain` → passes control to the next filter or servlet
    

---

## 🔁 **4️⃣ Filter Execution Flow**

```
Client
  ↓
Filter(s)
  ↓
DispatcherServlet
  ↓
Controller
  ↓
Service
  ↓
Repository (DB)
  ↓
Response
  ↑
Filter(s)
  ↑
Client

```

![[Pasted image 20251028120941.png]]

✅ Filters run **before and after** the request reaches the controller.

---

## 💻 **5️⃣ Example 1: Logging Filter**

```
@Component
public class LoggingFilter implements Filter {

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain)
            throws IOException, ServletException {

        HttpServletRequest req = (HttpServletRequest) request;
        long start = System.currentTimeMillis();

        System.out.println("➡️ Request: " + req.getMethod() + " " + req.getRequestURI());

        chain.doFilter(request, response);  // Continue to next filter or controller

        System.out.println("⬅️ Completed in " + (System.currentTimeMillis() - start) + " ms");
    }
}

```

✅ **Use case:** Logging all HTTP requests and response times.

---
## ⚙️ **7️⃣ Registering Filters**

### Option 1️⃣ — Using `@Component`

- Simplest method.
    
- Spring auto-registers the filter.
    

`@Component public class LoggingFilter implements Filter { ... }`

---

### Option 2️⃣ — Using `FilterRegistrationBean`

- Gives you control over **order** and **URL patterns**.
    

```
@Configuration
public class FilterConfig {

    @Bean
    public FilterRegistrationBean<LoggingFilter> registerLoggingFilter() {
        FilterRegistrationBean<LoggingFilter> reg = new FilterRegistrationBean<>();
        reg.setFilter(new LoggingFilter());
        reg.addUrlPatterns("/api/*");  // Apply to /api only
        reg.setOrder(1);  // Lower number = higher priority
        return reg;
    }
}
```

---

## 🧠 **8️⃣ Internal Working**

1. Request comes to the **Servlet Container (Tomcat)**.
    
2. Container passes it to registered **Filters**.
    
3. Filters may modify, block, or log the request.
    
4. After all filters pass → goes to **DispatcherServlet** → Controller.
    
5. Response travels back → Filters can modify the response again.

## **==HATEOAS**==
[HATEOAS](https://notebook.zohopublic.in/public/notes/dcr5z26771d816c4f47b7a63d7e1d45129fd7)
 Full form: Hypermedia As The Engine Of Application State
 It tells the client what the next action you can perform on particular item.

```
Normally: API sends only data.
With HATEOAS: API sends data + useful links for next actions.

Example (normal response):
{
  "id": 1,
  "name": "John"
}

Example (with HATEOAS):
{
  "id": 1,
  "name": "John",
  "_links": {
    "self": {"href": "http://localhost:8080/employees/1"},
    "all-employees": {"href": "http://localhost:8080/employees"}
  }
}

```

---

## ⚙️ Implementation in Spring Boot

### 1️⃣ Add dependency in `pom.xml`

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-hateoas</artifactId>
</dependency>

```

---

### 2️⃣ Imports in Controller

```
import org.springframework.hateoas.EntityModel;
import org.springframework.hateoas.server.mvc.WebMvcLinkBuilder;

```

---

### 3️⃣ Example Code

```
@GetMapping("/{id}")
public EntityModel<Employee> getEmployee(@PathVariable Long id) {
    Employee emp = new Employee(id, "John", "HR");

    EntityModel<Employee> model = EntityModel.of(emp);

    model.add(WebMvcLinkBuilder.linkTo(
            WebMvcLinkBuilder.methodOn(EmployeeController.class).getEmployee(id))
            .withSelfRel());

    model.add(WebMvcLinkBuilder.linkTo(
            WebMvcLinkBuilder.methodOn(EmployeeController.class).getAllEmployees())
            .withRel("all-employees"));

    return model;
}

```

---

## 🧾 Output Example

```
{
  "id": 1,
  "name": "John",
  "department": "HR",
  "_links": {
    "self": {"href": "http://localhost:8080/employees/1"},
    "all-employees": {"href": "http://localhost:8080/employees"}
  }
}

```

---

## ✅ Benefits

```
🔹 Clients discover API features through links (no hardcoding URLs).
🔹 Easier to evolve APIs (links auto-adjust if paths change).
🔹 Makes APIs more RESTful and self-documenting.
🔹 Supports dynamic navigation between resources.
```

## ==**Response Entity-==**
[Notes](https://notebook.zohopublic.in/public/notes/9wn9o2148145a9ab9476ca8b75e801ca27882)
## 🧩 What is `ResponseEntity` in Spring Boot?

`ResponseEntity` is a **class** in Spring Boot used to **represent the entire HTTP response**, including:

1. **Body (data you want to send)**
    
2. **HTTP Status Code (like 200, 404, 500)**
    
3. **Headers (like Content-Type, Location, etc.)**

Think of it like this:

> ✅ `ResponseEntity` = HTTP Response (Body + Status + Headers)

# 🧩 SPRING BOOT EXCEPTION HANDLING

---
## ⚙️ 1️⃣ What Is Exception Handling?

> **Definition (Interview):**  
> Exception handling is a mechanism to **handle runtime errors gracefully** without crashing the application.  
> In Spring Boot, it ensures that when an exception occurs, the app returns a **proper HTTP response** instead of a server crash or Whitelabel error page.

---
## ⚙️ 2️⃣ How It Works Internally (Under the Hood)

When an exception occurs inside a controller, Spring passes it through several internal classes:
### 🔁 Flow:

1. Exception is thrown inside the controller.
    
2. `HandlerExceptionResolverComposite` receives it.
    
3. It passes it to multiple resolvers one by one:
    
    - `ExceptionHandlerExceptionResolver`
        
    - `ResponseStatusExceptionResolver`
        
    - `DefaultHandlerExceptionResolver`
        
4. The **first resolver that can handle** the exception stops further propagation.
    
5. The resolver converts the exception into a proper **HTTP response**.

![[Pasted image 20251029113911.png]]

![[Pasted image 20251029113830.png]]

---

### 🧠 Role of Each Resolver

|Resolver|Purpose|
|---|---|
|**ExceptionHandlerExceptionResolver**|Looks for `@ExceptionHandler` methods (local or global) and calls them.|
|**ResponseStatusExceptionResolver**|Handles exceptions annotated with `@ResponseStatus`.|
|**DefaultHandlerExceptionResolver**|Handles framework-level exceptions (e.g., `HttpRequestMethodNotSupportedException`).|

---

## ⚙️ 3️⃣ Developer-Level Exception Handling Methods

Spring Boot provides **3 main ways** to handle exceptions:

|Method|Description|Scope|
|---|---|---|
|**`@ExceptionHandler`**|Handles specific exceptions inside a single controller.|Local|
|**`@ControllerAdvice` / `@RestControllerAdvice`**|Handles exceptions globally for all controllers.|Global|
|**`@ResponseStatus` / `ResponseStatusException`**|Maps exceptions to HTTP status codes.|Anywhere|

---

## 🧩 4️⃣ Local Exception Handling Example

```
@RestController
public class UserController {

    @GetMapping("/user/{id}")
    public String getUser(@PathVariable int id) {
        if (id <= 0) {
            throw new IllegalArgumentException("Invalid user ID");
        }
        return "User found: " + id;
    }

    @ExceptionHandler(IllegalArgumentException.class)
    public ResponseEntity<String> handleIllegalArgument(IllegalArgumentException ex) {
        return ResponseEntity.badRequest().body("Handled locally: " + ex.getMessage());
    }
}

```

✅ Handles exceptions **only for this controller**.  
❌ Other controllers throwing the same exception will not use this handler.

---

## 🌍 5️⃣ Global Exception Handling Example

```
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(IllegalArgumentException.class)
    public ResponseEntity<String> handleIllegalArgument(IllegalArgumentException ex) {
        return ResponseEntity.badRequest().body("Handled globally: " + ex.getMessage());
    }

    @ExceptionHandler(Exception.class)
    public ResponseEntity<String> handleGeneric(Exception ex) {
        return ResponseEntity.internalServerError()
                .body("Global error: " + ex.getMessage());
    }
}
```

✅ Applies to **all controllers** in the project.  
✅ Useful for centralized error handling.

---
## 🧭 6️⃣ Local vs Global Handler — Who Runs First?

|Situation|Who Handles|Reason|
|---|---|---|
|Exception has local `@ExceptionHandler`|✅ Local Handler|Local handlers have higher priority.|
|No local handler found|✅ Global Handler|Spring searches in global handlers next.|
|Neither found|❌ Default Handler|Spring shows Whitelabel error (500).|

---
## ⚖️ 7️⃣ `ResponseEntity` — Why It’s Used

- Represents the **entire HTTP response**, not just text.
    
- Lets you control:
    
    - ✅ Status code (e.g., 400, 404, 500)
        
    - ✅ Headers
        
    - ✅ Body
        

### Example:

```
return ResponseEntity.badRequest()
        .body("Handled globally: " + ex.getMessage());
```

Equivalent to:

```
return new ResponseEntity<>("Handled globally: " + ex.getMessage(), HttpStatus.BAD_REQUEST);
```

### Without ResponseEntity

If you return just `String`, status = **200 OK** (not ideal for errors).

---

## 🏷️ 8️⃣ Using `@ResponseStatus` (Custom Exception Class)

```
@ResponseStatus(HttpStatus.NOT_FOUND)
public class ResourceNotFoundException extends RuntimeException {
    public ResourceNotFoundException(String msg) {
        super(msg);
    }
}
```

```
@GetMapping("/user/{id}")
public String getUser(@PathVariable int id) {
    if (id == 0)
        throw new ResourceNotFoundException("User not found");
    return "User found: " + id;
}
```

➡️ Returns HTTP **404 Not Found** automatically.

---
## ⚙️ 9️⃣ Using `ResponseStatusException` (Inline)

```
@GetMapping("/user/{id}")
public String getUser(@PathVariable int id) {
    if (id == 0)
        throw new ResponseStatusException(HttpStatus.BAD_REQUEST, "ID cannot be zero");
    return "User found: " + id;
}
```

➡️ Quick way to throw an exception without creating a separate class.

---
## 🧾 Summary Table

|Approach|Annotation|Scope|Use Case|Example|
|---|---|---|---|---|
|Local|`@ExceptionHandler`|Controller|Handle controller-specific exceptions|Inside controller|
|Global|`@RestControllerAdvice` + `@ExceptionHandler`|All controllers|Centralized error handling|Separate class|
|Status-based|`@ResponseStatus`|Exception class|Custom status for exception|Define custom exception|
|Inline|`ResponseStatusException`|Controller|Quick custom HTTP error|Throw directly|

---
## 💡 Key Interview Pointers

|Question|Short Answer|
|---|---|
|What is exception handling?|Handling runtime errors gracefully without crashing.|
|How do you handle exceptions globally?|Using `@RestControllerAdvice` + `@ExceptionHandler`.|
|Why use ResponseEntity?|To control HTTP status, headers, and body in response.|
|What if no handler is found?|Spring’s default resolver sends a 500 error.|
|Difference between local & global handler?|Local → controller only, Global → all controllers.|

## ==**JPA (Java Persistence API)==**
[Notes](https://notebook.zohopublic.in/public/notes/9wn9o5fd6c0f15d68425d9b98284f48186179)

![[Pasted image 20251030152509.png]]
### 🧩 **1. Persistence Unit**

A **Persistence Unit** is the configuration block defined in `persistence.xml` (or auto-configured by Spring Boot) that tells JPA:

- which database to connect to,
    
- which entities to manage, and
    
- which provider (like Hibernate) to use.
    

Think of it as a “database connection profile + JPA setup.”

🔹 **1:1 relationship with `EntityManagerFactory`** — one persistence unit creates one factory.

---

### ⚙️ **2. EntityManagerFactory**

The **EntityManagerFactory** is a heavyweight object responsible for creating `EntityManager` instances.

- It reads metadata from the persistence unit.
    
- It holds connection pool configuration, caching info, and mapping data.
    
- In a Spring Boot app, this is typically created and managed by Spring (via `LocalContainerEntityManagerFactoryBean`).
    

🔹 **1:Many relationship** — one factory can produce many `EntityManager`s, usually one per transaction or request.

---

### 🧠 **3. EntityManager**

The **EntityManager** is the core JPA interface used to perform database operations like `persist()`, `find()`, `remove()`, etc.

- It acts as a **bridge between your application and the database**.
    
- Each `EntityManager` controls a **Persistence Context** — an in-memory cache of managed entities.
    

🔹 **1:1 relationship** — each `EntityManager` manages exactly one persistence context.

---

### 💾 **4. Persistence Context**

This is where things get interesting.  
A **Persistence Context** is like a small in-memory database that keeps track of all entities currently being managed by JPA.

Think of the **Persistence Context** as **JPA’s memory or workspace** where it keeps track of all the entities (objects) it is currently managing inside a transaction.

It’s like a _temporary storage area_ between your Java program and the database.

---
### 🧠 Real-life Analogy

Imagine you’re a **teacher** managing students in a classroom.

- The **classroom** = Persistence Context
    
- The **students** = Entities (like `User`, `Product`, etc.)
    
- The **teacher** = EntityManager
    

When a student (entity) enters the classroom (gets persisted), the teacher knows everything about them — their name, marks, and whether they’ve changed anything.

If a student changes their mark (you call a setter method), the teacher notices and updates the gradebook (database) _only at the end of class (transaction commit)_.
![[Pasted image 20251030153325.png]]
The **Persistence Context** is managed by the **EntityManager**, and every entity inside it can move through different **states**:  
`New → Managed → Removed → Detached`.

Let’s break this down step by step.

---

### 🧱 1. New (Transient) State

The entity is just a normal Java object — **not yet known** to JPA or the database.

Example:

`User user = new User("Pratik", "p@mail.com");`

At this point:

- Not in Persistence Context.
    
- No database record.
    
- JPA doesn’t track it.

---
### 🧩 2. Managed (Persistent) State

When you call:

`entityManager.persist(user);`

→ JPA adds the object to the **Persistence Context**.

Now it’s **managed**, meaning:

- JPA tracks every change you make.
    
- It will automatically update the DB when the transaction commits or when you call `flush()`.
    

Example:

`user.setEmail("new@mail.com");`

JPA notes this internally (dirty checking).  
At the end of the transaction → it sends an `UPDATE` query to the DB.

---

### 🔁 3. Detached State

After the transaction ends or when you call:

`entityManager.detach(user);`

the entity is **no longer tracked**.

So if you change fields now, JPA will **not** save them automatically.

Example:

`user.setName("NewName"); // not saved`

If you later want to reattach it:

`entityManager.merge(user);`

Now it becomes **Managed** again.

---

### ❌ 4. Removed State

When you call:

`entityManager.remove(user);`

the entity is marked for **deletion** in the Persistence Context.

- The record will be deleted from the database when the transaction commits or when you call `flush()`.
    

Until that commit happens, the entity still exists in memory — just flagged as "to be deleted".


---

### 🧱 **5. Entities**

These are your mapped classes — typically annotated with `@Entity`.  
They represent database tables and are the actual Java objects you manipulate.

---

### 🧩 **6. Dialect**

The **Dialect** translates the JPA’s database-agnostic queries (JQL/JPQL) into SQL syntax specific to your database.  
For example:

- MySQLDialect
    
- PostgreSQLDialect
    
- OracleDialect
    

If you write `SELECT s FROM Student s`, Hibernate converts it to:  
`SELECT * FROM student;` (using dialect-specific SQL syntax)

---

### 🔡 **7. JDBC Driver**

Once the dialect translates the query into SQL, the **JDBC driver** handles the actual communication with the database — sending SQL statements, receiving results, managing connections, etc.

---

### 🗄️ **8. Database (DB1)**

This is your physical database where your tables and data live.  
The final SQL query is executed here.

---

### 🧩 Putting It All Together (Flow Summary)

1. **Persistence Unit** defines your JPA configuration.
    
2. It creates an **EntityManagerFactory**.
    
3. That factory produces multiple **EntityManager** instances (each typically per request/transaction).
    
4. Each **EntityManager** controls a **Persistence Context**, which manages entities in memory.
    
5. Operations on entities (persist, update, delete) generate **JPQL (JPA Query Language)** queries.
    
6. The **Dialect** converts JPQL to SQL.
    
7. SQL passes through the **JDBC driver**.
    
8. Finally, the **Database** executes it and returns results.
    

---

### 🧭 Think of it like this:

```
PersistenceUnit (Configuration)
      ↓
EntityManagerFactory (Factory)
      ↓
EntityManager (Worker)
      ↓
PersistenceContext (Memory workspace)
      ↓
Entities (Objects being managed)
      ↓
Dialect → JDBC → Database

```

### ==**First level Caching==**

When you fetch an entity using the **EntityManager** (for example, `entityManager.find(User.class, 1)`), JPA doesn’t immediately go to the database every time you call it.  
Instead, it keeps a **cache of entities** within the current **Persistence Context** (basically, the current unit of work, usually tied to a single transaction).

That cache is called the **first-level cache**.

So, if you call:

```
User user1 = entityManager.find(User.class, 1);
User user2 = entityManager.find(User.class, 1);
```

Only the **first** call hits the database.  
The **second** call returns the same object (`user1 == user2` will be `true`) directly from memory.

---
### 2. When does it clear?

The first-level cache is **scoped to the Persistence Context**, meaning:

- It exists **only during the lifetime of an `EntityManager`**.
    
- When the transaction ends (commit or rollback), or when you explicitly call `entityManager.clear()` or `entityManager.close()`, the cache is gone.

---
### 3. Why is it important?

It ensures:

- **Performance**: avoids repeated database hits for the same entity within a transaction.
    
- **Consistency**: ensures you’re always working with the same in-memory instance of an entity — if you modify it, JPA knows and can synchronize (flush) it back to the database when needed.

---

### 4. Example to visualize

```
EntityManager em = entityManagerFactory.createEntityManager();
em.getTransaction().begin();

User userA = em.find(User.class, 1); // Hits DB
User userB = em.find(User.class, 1); // From first-level cache
System.out.println(userA == userB); // true

em.getTransaction().commit();
em.close(); // Cache cleared
```

---

### 5. Summary

- **Type:** Automatic, built-in cache.
    
- **Scope:** One `EntityManager` (one persistence context).
    
- **Goal:** Avoid duplicate database reads within the same transaction.
    
- **Cleared:** When EntityManager is closed or cleared.

## ==**Second Level Caching==**
[notes](https://notebook.zohopublic.in/public/notes/9wn9o30b391bbe74c408eb8c70d306be98258)
## 🧠 What is Second-Level Cache (L2 Cache)?

- The **second-level cache** is a **shared cache** maintained by the **JPA provider (like Hibernate)**, used to store entities, collections, or query results **beyond the scope of a single Persistence Context**.
    
- It allows entities to be reused **across multiple sessions (`EntityManager` instances)** without hitting the database repeatedly.
---
## ⚙️ How It Works

- When an entity is fetched from the database, Hibernate stores it in the **L2 cache region**.
    
- Next time any other `EntityManager` (in a new transaction) requests the same entity, Hibernate first checks the L2 cache:
    
    - If the entity is found → returned from cache.
        
    - If not → fetched from DB, then stored in cache for future use.

---
## 🧩 Difference Between L1 and L2 Cache

|Feature|First-Level Cache|Second-Level Cache|
|---|---|---|
|Scope|One `EntityManager` (per transaction)|Shared across multiple `EntityManager` instances|
|Enabled by default|✅ Yes|❌ No (must be enabled manually)|
|Lifetime|Till EntityManager is closed|Till application stops or region invalidates|
|Type|Built into JPA|Provided by Hibernate (with caching provider)|
|Goal|Avoid repeated DB calls within same session|Reuse data across sessions|

---

## ⚡ Configuration (Hibernate Example)

In `application.properties`:

```
spring.jpa.properties.hibernate.cache.use_second_level_cache=true
spring.jpa.properties.hibernate.cache.use_query_cache=true
spring.jpa.properties.hibernate.cache.region.factory_class=org.hibernate.cache.ehcache.EhCacheRegionFactory
```

Add dependency:

```
<dependency>
    <groupId>org.hibernate.orm</groupId>
    <artifactId>hibernate-ehcache</artifactId>
</dependency>
```

Annotate your entity:

```
@Entity
@Cacheable
@org.hibernate.annotations.Cache(usage = CacheConcurrencyStrategy.READ_WRITE)
public class User {
    @Id
    private Long id;
    private String name;
}
```

---

## 🧠 Cache Providers (Implementations)

Hibernate doesn’t implement caching itself — it integrates with providers like:

- **Ehcache**
    
- **Infinispan**
    
- **Hazelcast**
    
- **Caffeine**
    
- **JCache (JSR-107)** → Standard caching API (works like JPA for caching)
    

---

## 🧩 CacheConcurrencyStrategy Types

|Strategy|Description|Use Case|
|---|---|---|
|**READ_ONLY**|For immutable data (no updates allowed)|Reference data like countries, states|
|**NONSTRICT_READ_WRITE**|Allows updates but eventual consistency|Data rarely updated (e.g., product catalog)|
|**READ_WRITE**|Uses soft locks for consistency|Regular entities with moderate updates|
|**TRANSACTIONAL**|Fully transactional cache, needs special provider|Distributed or clustered systems|

---

## 🧩 How It Interacts with First-Level Cache

1. **Check L1 (Persistence Context)** → if found, return entity.
    
2. If not in L1 → check **L2 cache**.
    
3. If not in L2 → hit **database**, then store result in both caches.
    

When an entity is **updated or deleted**, Hibernate automatically **invalidates or updates** the corresponding cache entry based on the configured strategy.

---

## ⚙️ Query Cache (Optional)

You can also cache **query results**:

`spring.jpa.properties.hibernate.cache.use_query_cache=true`

Mark query as cacheable:

```
Query q = entityManager.createQuery("from User");
q.setHint("org.hibernate.cacheable", true);
```

> Query cache stores only **IDs of entities**, not the entities themselves — those are fetched from the L2 cache.

---

## 🧩 When to Use L2 Cache

✅ Best for:

- Data that is frequently read and rarely updated.
    
- Applications with many read-heavy transactions.
    
- Reducing database load and improving performance.
    

❌ Avoid for:

- Highly volatile data (frequent updates/deletes).
    
- Scenarios requiring always-fresh data (real-time systems).
    

---

## 🧩 Example Flow

1. Transaction A fetches User(1) → DB hit → stored in L1 + L2.
    
2. Transaction A closes → L1 cleared.
    
3. Transaction B fetches User(1) → found in L2 → no DB hit.
    

---

## 🧾 Summary

- **L2 cache = shared memory of Hibernate**, persistent beyond one session.
    
- **Must be enabled** manually and configured with a provider.
    
- **Improves read performance**, but must be carefully used to avoid stale data.
    
- Controlled through `CacheConcurrencyStrategy` to balance **speed** and **consistency**.

# ==Annotations and their subfields
==
[notes](https://notebook.zohopublic.in/public/notes/9wn9ob681f4fe22c8412db0729f618737a416)
## 🧩 1. `@Entity`
**Purpose:**  
Marks a Java class as a JPA entity — meaning JPA will manage its lifecycle (insert, update, delete, select) and map it to a table.

`@Entity(name = "UserEntity") public class User { ... }`

**How it works:**  
When Hibernate scans entities, it looks for `@Entity` classes and builds metadata — e.g., table name, columns, primary keys, relationships.  
Without this, the class is invisible to JPA.

**Parameter:**

- `name`: Logical entity name used in JPQL (not the table name).  
    Example:
    
    `@Entity(name = "EmployeeRecord")`
    
    Then in JPQL you can write:
    
    `SELECT e FROM EmployeeRecord e`
    
---
## 🏷️ 2. `@Table`

**Purpose:**  
Defines how this entity maps to a specific table in your database.

```
@Table(
    name = "users",
    schema = "public",
    catalog = "appdb",
    uniqueConstraints = @UniqueConstraint(columnNames = {"email"}),
    indexes = @Index(name = "idx_username", columnList = "username")
)

```

**Parameters:**

- `name`: The name of the table. If omitted, defaults to the entity class name.
    
- `schema`: Database schema where the table lives (common in PostgreSQL or Oracle).
    
- `catalog`: Database catalog name (in MySQL, this is the database name).
    
- `uniqueConstraints`: Ensures that specific columns are unique at the database level.
    
    `@UniqueConstraint(name = "uk_email", columnNames = {"email"})`
    
    ⇒ Adds a `UNIQUE` constraint in SQL.
    
- `indexes`: Adds indexes for faster queries.
    
    `@Index(name = "idx_username", columnList = "username")`
    

**Why use it?**

- When your DB table name doesn’t match your class name.
    
- To enforce database-level uniqueness.
    
- To define performance-related indexes.
---
## 🗝️ 3. `@Id`

**Purpose:**  
Defines the _primary key_ — a unique identifier for each entity record.

`@Id private Long id;`

**Why important:**  
JPA needs a unique key to track and identify each object in the persistence context.  
Without it, Hibernate can’t perform updates or deletes properly.

---
## 🔢 4. `@GeneratedValue`

**Purpose:**  
Defines _how_ the primary key is automatically generated when you insert new data.

```
@Id
@GeneratedValue(strategy = GenerationType.IDENTITY)
private Long id;

```

**Parameters:**

- `strategy`: Tells JPA which ID generation approach to use.
    
    1. `AUTO` → JPA chooses automatically based on the database dialect.  
        (e.g., sequence for PostgreSQL, identity for MySQL)
        
    2. `IDENTITY` → Uses the database’s auto-increment column.  
        SQL Example: `id BIGINT AUTO_INCREMENT`
        
    3. `SEQUENCE` → Uses a database sequence.  
        (You must define it or JPA creates one)
        
        `@SequenceGenerator(name = "seq_emp", sequenceName = "emp_seq", allocationSize = 1) @GeneratedValue(strategy = GenerationType.SEQUENCE, generator = "seq_emp")`
        
    4. `TABLE` → Uses a separate table to keep track of ID values (portable but slower).
        
        `@TableGenerator(name = "tab_gen", table = "id_table", pkColumnValue = "emp_id") @GeneratedValue(strategy = GenerationType.TABLE, generator = "tab_gen")`
        

**Why use it:**  
You rarely want to manually assign IDs — auto generation makes entity persistence smooth.

---

## 🧮 5. `@Column`

**Purpose:**  
Customizes how each field maps to its database column.

```
@Column(
    name = "user_email",
    nullable = false,
    unique = true,
    length = 100,
    insertable = true,
    updatable = true
)
private String email;

```

**Parameters:**

- `name`: Column name in the table. Defaults to field name.
    
- `nullable`: Whether column allows `NULL`. (adds `NOT NULL` in SQL)
    
- `unique`: Adds a unique constraint (though `@Table(uniqueConstraints = …)` is preferred).
    
- `length`: For `VARCHAR` columns (default = 255).
    
- `precision` / `scale`: For decimal numbers.  
    e.g. `@Column(precision = 10, scale = 2)` → `DECIMAL(10,2)`
    
- `insertable`: If false, this column is **not included in INSERT SQL**.
    
- `updatable`: If false, this column is **not updated** once inserted.
    
- `columnDefinition`: Custom SQL definition, like:
    
    `@Column(columnDefinition = "varchar(255) default 'N/A'")`
    

**Why use it:**  
You fine-tune the table schema and control what JPA actually includes in SQL.

---
## 🧮 6. `@Transient`

**Purpose:**  
Marks a field that shouldn’t be stored in the database at all.

`@Transient private int temporaryScore;`

**Why use it:**  
For computed fields or values used only in memory (not in DB).

---

## 🧩 7. `@Embedded` & `@Embeddable`

**Purpose:**  
Used to _reuse_ value objects across entities — the embedded fields share the same table.

```
@Embeddable
public class Address {
    private String city;
    private String zip;
}

@Entity
public class User {
    @Id
    private Long id;
    @Embedded
    private Address address;
}

```

**How it behaves:**  
`User` table will have columns `city` and `zip` — no separate Address table.

**Why use it:**  
When you have repeatable fields (like address, coordinates, etc.) reused across entities.

---
## 🧱 8. `@Enumerated`

**Purpose:**  
Defines how `enum` values are stored in the database.

`public enum Role { USER, ADMIN }  @Enumerated(EnumType.STRING) private Role role;`

**Parameter:**

- `EnumType.ORDINAL`: Saves the numeric index (0,1,2…)
    
- `EnumType.STRING`: Saves the name (`"USER"`, `"ADMIN"`)
    

**Recommendation:** Always use `STRING` (safer — avoids errors if enum order changes).

---
## 🕒 9. `@Temporal`

**Purpose:**  
Tells JPA how to store `java.util.Date` or `java.util.Calendar` types.

`@Temporal(TemporalType.TIMESTAMP) private Date createdAt;`

**Options:**

- `TemporalType.DATE`: Stores only date.
    
- `TemporalType.TIME`: Stores only time.
    
- `TemporalType.TIMESTAMP`: Stores both date and time.
    

_(For `LocalDate`, `LocalDateTime`, no need for @Temporal — JPA understands them directly.)_

---

## 🧮 10. `@Lob`

**Purpose:**  
For storing large objects: text or binary data.

`@Lob private String description; // CLOB`

or

`@Lob private byte[] image; // BLOB`

**Behavior:**

- Text → stored as `CLOB`
    
- Binary → stored as `BLOB`
    

---

## 🧠 11. `@Access`

**Purpose:**  
Specifies whether JPA accesses fields **directly** or via **getters/setters**.

`@Access(AccessType.FIELD)`

**Options:**

- `FIELD`: JPA reads/writes the actual class field.
    
- `PROPERTY`: JPA uses getter/setter methods.
    

Useful when you want strict control over which fields JPA manages.

---

## 🪪 12. `@Version`

**Purpose:**  
Implements **optimistic locking** — prevents overwriting changes made by another transaction.

`@Version private int version;`

**How it works:**  
Each time an entity updates, the version column increments.  
When updating, Hibernate includes a `WHERE version = ?` check.  
If the row was changed in the meantime, no row updates → triggers an `OptimisticLockException`.

**SQL Example:**

`UPDATE users SET name = ?, version = version + 1 WHERE id = ? AND version = ?`

# 📘 JPA `@OneToOne` Mapping

---
## 🔹 Definition

`@OneToOne` defines a **one-to-one relationship** between two entities.  
Each record in one table corresponds to **exactly one record** in another table.

**Example:**  
One `Person` ↔ One `Passport`

---
## 🔹 Basic Example

```
@Entity
public class Person {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToOne
    @JoinColumn(name = "passport_id")
    private Passport passport;
}

@Entity
public class Passport {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String number;
}
```

- `person` table → contains a `passport_id` foreign key.
    
- This represents a **unidirectional** one-to-one mapping.

---
## 🔹 Types of One-to-One Relationships

### 1. **Unidirectional**

- Only one entity knows about the other.
    
- Example: `Person` → `Passport`.
    
- Only `Person` has the `@JoinColumn`.

### 2. **Bidirectional**

- Both entities know about each other.
    
- One side owns the relationship (has `@JoinColumn`).
    
- Other side uses `mappedBy`.

**Example:**

```
@Entity
public class Passport {
    @Id
    private Long id;

    private String number;

    @OneToOne(mappedBy = "passport")
    private Person person;
}
```

---

## 🔹 `@OneToOne` Annotation — Key Attributes

### 1. `cascade`

Defines which operations are cascaded from parent to child.

**Options:**

- `PERSIST` → Save child when parent is saved.
    
- `MERGE` → Merge child when parent is merged.
    
- `REMOVE` → Delete child when parent is deleted.
    
- `REFRESH` → Refresh child when parent is refreshed.
    
- `DETACH` → Detach child when parent is detached.
    
- `ALL` → Applies all above.
    

**Example:**

```
@OneToOne(cascade = CascadeType.ALL)
@JoinColumn(name = "passport_id")
private Passport passport;
```

**Effect:**  
Persisting or removing `Person` also persists or removes `Passport`.

---

### 2. `fetch`

Defines when related entity should be loaded from the DB.

- `EAGER` (default) → Both entities are fetched together.
    
- `LAZY` → Related entity fetched only when accessed.
    

**Example:**

`@OneToOne(fetch = FetchType.LAZY)`

**Effect:**  
When you fetch `Person`, `Passport` data loads only when `getPassport()` is called.

---

### 3. `optional`

Specifies whether the relationship is required or not.

- `true` (default): Child can be null.
    
- `false`: Child must exist.
    

**Example:**

`@OneToOne(optional = false)`

**Effect:**  
Adds `NOT NULL` constraint on foreign key column.

---

### 4. `mappedBy`

Used on the **non-owning side** in bidirectional mapping.  
Tells JPA which field owns the relationship.

**Example:**

```
@OneToOne(mappedBy = "passport")
private Person person;
```

**Effect:**

- Prevents duplicate foreign key columns.
    
- Ownership remains on the entity that has `@JoinColumn`.
---
### 5. `orphanRemoval`

If true, removes the child when it’s no longer referenced by the parent.

**Example:**

```
@OneToOne(cascade = CascadeType.ALL, orphanRemoval = true)
private Passport passport;
```

**Effect:**  
If `person.setPassport(null)` → Hibernate deletes the old Passport automatically.

---

## 🔹 `@JoinColumn` Annotation — Foreign Key Details

Defines the **actual column** used to join both tables.

**Example:**

```
@OneToOne
@JoinColumn(
    name = "passport_id",
    referencedColumnName = "id",
    nullable = false,
    unique = true,
    insertable = true,
    updatable = true,
    foreignKey = @ForeignKey(name = "FK_PERSON_PASSPORT")
)
private Passport passport;
```

### Fields:

|Field|Default|Description|
|---|---|---|
|`name`|generated automatically|FK column name in owning table|
|`referencedColumnName`|"id"|Column in target table being referenced|
|`nullable`|true|Allows null or not|
|`unique`|false|Ensures one-to-one uniqueness|
|`insertable`|true|Whether column is included in INSERTs|
|`updatable`|true|Whether column is included in UPDATEs|
|`foreignKey`|auto|Define custom FK constraint name|

**Effect:**  
Creates a unique foreign key column (e.g. `passport_id`) in the owning table.

---

## 🔹 Database Behavior Summary

|Type|Foreign Key Location|Description|
|---|---|---|
|**Unidirectional**|On owning side (has `@JoinColumn`)|One entity links to another|
|**Bidirectional**|On owning side (the one without `mappedBy`)|Both can access each other|
|**Cascade**|On operations (persist, remove, etc.)|Child follows parent operations|
|**orphanRemoval**|Removes unreferenced child|Auto delete when set to null|

---

## 🔹 Typical SQL Generated (Example)

For the above `Person` ↔ `Passport` mapping:

```
CREATE TABLE passport (
  id BIGINT PRIMARY KEY,
  number VARCHAR(255)
);

CREATE TABLE person (
  id BIGINT PRIMARY KEY,
  name VARCHAR(255),
  passport_id BIGINT UNIQUE,
  CONSTRAINT FK_PERSON_PASSPORT FOREIGN KEY (passport_id)
    REFERENCES passport(id)
);

```

---

## 🔹 Common Real-Life Uses

- `User` ↔ `Profile`
    
- `Employee` ↔ `Laptop`
    
- `Person` ↔ `Passport`
    
- `Order` ↔ `Invoice`
    

---

## 🔹 Quick Summary Table

|Attribute|Default|Purpose|
|---|---|---|
|`cascade`|none|Propagates parent operations to child|
|`fetch`|EAGER|Defines fetch timing|
|`optional`|true|Relationship may be null|
|`mappedBy`|none|Defines inverse side in bidirectional mapping|
|`orphanRemoval`|false|Deletes child when unlinked|
|`@JoinColumn.name`|auto|Foreign key column name|
|`@JoinColumn.unique`|false|Ensures true 1-to-1 relationship|

## **JPA Relationships Notes**
---
### 1. @OneToOne

**Definition:** One entity is related to exactly one other entity.

**Example:** One `User` has one `Profile`.

```java
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String username;

    @OneToOne(cascade = CascadeType.ALL)
    @JoinColumn(name = "profile_id") // foreign key
    private Profile profile;
}

@Entity
public class Profile {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String bio;
}
```

**Bidirectional:** Add in `Profile.java`:

```java
@OneToOne(mappedBy = "profile")
private User user;
```

**Use Case:** Passport ↔ Person, User ↔ Profile

---

### 2. @OneToMany / @ManyToOne

**Definition:** One entity has many others; the “many” belongs to one “one.”

**Example:** One `Department` has many `Employees`.

```java
@Entity
public class Department {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "department", cascade = CascadeType.ALL)
    private List<Employee> employees = new ArrayList<>();
}

@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @ManyToOne
    @JoinColumn(name = "department_id")
    private Department department;
}
```

**Explanation:** Foreign key (`department_id`) exists in the Employee table.

**Use Case:** Department ↔ Employees, Category ↔ Products

---

### 3. @ManyToMany

**Definition:** Many entities relate to many others.

**Example:** A `Student` can enroll in many `Courses`, and a `Course` can have many `Students`.

```java
@Entity
public class Student {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;

    @ManyToMany
    @JoinTable(
        name = "student_course",
        joinColumns = @JoinColumn(name = "student_id"),
        inverseJoinColumns = @JoinColumn(name = "course_id")
    )
    private List<Course> courses = new ArrayList<>();
}

@Entity
public class Course {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String title;

    @ManyToMany(mappedBy = "courses")
    private List<Student> students = new ArrayList<>();
}
```

**Explanation:** JPA creates a join table `student_course`.

**Use Case:** Students ↔ Courses, Actors ↔ Movies

---

### 4. Self-Referencing Relationships

**Definition:** Entity relates to itself.

**Example:** An `Employee` has a `Manager` who is also an `Employee`.

```java
@Entity
public class Employee {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;

    @ManyToOne
    @JoinColumn(name = "manager_id")
    private Employee manager;

    @OneToMany(mappedBy = "manager")
    private List<Employee> subordinates = new ArrayList<>();
}
```

**Use Case:** Employee ↔ Manager, Category ↔ Subcategory

---

### 5. Relationship Summary Table

|Relationship Type|Description|Typical Use Case|Foreign Key Location|
|---|---|---|---|
|@OneToOne|One ↔ One|User ↔ Profile|One side’s table|
|@OneToMany|One ↔ Many|Department ↔ Employee|“Many” side|
|@ManyToOne|Many ↔ One|Employee ↔ Department|“Many” side|
|@ManyToMany|Many ↔ Many|Student ↔ Course|Separate join table|

---

**Directionality:**

- **Unidirectional:** Only one entity knows the relationship.
    
- **Bidirectional:** Both entities know each other using `mappedBy`.
    

**Cascade Types:** Control how operations (persist, merge, remove) apply to related entities.  
**orphanRemoval = true:** Deletes child if removed from parent collection.


## ==**1. Derived Queries**==

**Definition:**  
Derived queries are repository methods whose **names define the query**. Spring Data JPA automatically interprets the method name and generates the query.

---

### **Syntax**

`findBy<FieldName><Operator><Condition>`

**Examples:**

```
List<Employee> findByName(String name);                     // Find by exact name
List<Employee> findByAgeGreaterThan(int age);               // Find employees older than age
List<Employee> findByDepartmentAndAgeLessThan(String dept, int age);
boolean existsByName(String name);                          // Check if record exists
long countByDepartment(String dept);                        // Count employees by department
```

---

### **Operators & Keywords**

|Keyword / Operator|Description|Example|
|---|---|---|
|`Is`, `Equals`|Equality|findByNameIs / findByNameEquals|
|`GreaterThan`, `LessThan`|Numeric comparison|findByAgeGreaterThan(25)|
|`Between`|Range|findByAgeBetween(20, 30)|
|`Like`, `Containing`|String pattern match|findByNameContaining("Pat")|
|`StartingWith`, `EndingWith`|String prefix/suffix match|findByNameStartingWith("Pr")|
|`IsNull`, `IsNotNull`|Null checks|findByManagerIsNull()|
|`And`, `Or`|Combine multiple conditions|findByDeptAndAgeLessThan("IT", 30)|
|`OrderBy<Field>Asc/Desc`|Sorting|findByAgeLessThanOrderByNameAsc(40)|

---

### **Return Types**

- `List<Entity>` → Multiple records
    
- `Optional<Entity>` → Single or null record
    
- `boolean` → Exists check
    
- `long` → Count
    

---

### **Notes**

- Method names are **translated to queries automatically**.
    
- Works only with **entity fields**, not database columns.
    
- You can combine multiple fields and conditions in **one method**.
    

---

## **2. Pagination & Sorting**

**Purpose:**  
Retrieve subsets of data (“pages”) and sort results efficiently, instead of fetching all records at once.

---

### **Interfaces & Classes**

- **`Pageable`** → specifies page number, size, and sort order.
    
- **`Page<T>`** → contains page content and metadata.
    
- **`Sort`** → defines sorting rules.
    

---

### **Pagination Example**

```
Pageable pageable = PageRequest.of(0, 5, Sort.by("name").ascending());
Page<Employee> page = employeeRepository.findByDepartment("IT", pageable);

// Access page data
List<Employee> employees = page.getContent();
long totalRecords = page.getTotalElements();
int totalPages = page.getTotalPages();
int currentPage = page.getNumber();
boolean hasNext = page.hasNext();
boolean hasPrevious = page.hasPrevious();
```

---

### **Sorting Example**

```
List<Employee> employees = employeeRepository.findAll(Sort.by("age").descending());
Sort sort = Sort.by("department").ascending().and(Sort.by("age").descending());

```

---

### **Notes**

- Pagination and sorting can be combined:  
    `PageRequest.of(page, size, Sort.by("field").ascending())`
    
- Improves performance by **avoiding fetching all records**.
    
- Useful for **UI tables, reports, or APIs** that display large datasets.
    

---

## **3. JPQL (Java Persistence Query Language)**

**Definition:**  
JPQL is a query language for **entity objects**, not database tables. It works with **entity fields** and **relationships**.

---

### **Basic JPQL Example**

```
@Query("SELECT e FROM Employee e WHERE e.department = :dept")
List<Employee> findEmployeesByDepartment(@Param("dept") String department);
```

**Key Points:**

- `Employee` → entity class
    
- `e` → alias for entity (required)
    
- `department` → entity field
    
- Supports joins: `JOIN`, `LEFT JOIN`, `JOIN FETCH`
    
- Database-independent
    

---

### **JPQL vs SQL**

|JPQL|SQL|
|---|---|
|Uses entity classes|Uses tables|
|Uses entity fields|Uses columns|
|Returns objects|Returns rows|
|Supports object relationships|Manual joins required|

---

### **JPQL with Joins**

```
// Fetch employees with department using join
@Query("SELECT e FROM Employee e JOIN e.department d WHERE d.name = :dept")
List<Employee> findEmployeesInDepartment(@Param("dept") String dept);

```

**Fetch Join Example (Avoid N+1 Problem):**

```
@Query("SELECT d FROM Department d JOIN FETCH d.employees")
List<Department> findAllWithEmployees();
```

---

## ==**4. N+1 Problem**==

**Definition:**  
A performance issue where **fetching a parent entity triggers one query per child entity**, leading to N+1 queries.

---
### **Scenario**

```
List<Department> departments = departmentRepository.findAll();
for (Department d : departments) {
    d.getEmployees().size(); // triggers one query per department
}
```

**Queries executed:**

- 1 query for departments
    
- N queries for employees per department → Total = N+1
    
---
### **Causes**

- Lazy-loaded collections (`FetchType.LAZY`) accessed repeatedly.
    
- Often occurs in `@OneToMany` or `@ManyToOne` relationships.

---
### **Solutions**

1. **JPQL Fetch Join**
    

`@Query("SELECT d FROM Department d JOIN FETCH d.employees") List<Department> findAllWithEmployees();`

2. **EntityGraph**
    

`@NamedEntityGraph(     name = "Department.employees",     attributeNodes = @NamedAttributeNode("employees") )`

3. **EAGER Fetch**
    

> Use carefully, as it loads all associated entities immediately.

---
### **Notes**

- Always profile queries in production to detect N+1 issues.
    
- Use fetch joins or entity graphs instead of repeatedly accessing lazy associations.

---
## **5. Summary & Best Practices**

|Topic|Best Practices / Notes|
|---|---|
|Derived Queries|Simple, readable, auto-generated by method names|
|Pagination & Sorting|Always use for large datasets to avoid memory issues|
|JPQL|Flexible queries for entities and relationships; supports joins|
|N+1 Problem|Avoid lazy-loading traps; use fetch joins or entity graphs|
|Fetch Types|Know difference: `LAZY` vs `EAGER`|
|Combined Usage|Derived queries + pagination + sorting + JPQL = efficient repositories|
## ==🧩 **Native Query**==

### 🔹 Definition:

A **Native Query** in Spring Data JPA allows you to execute **raw SQL** directly on the database instead of JPQL.

Used when:

- You need **database-specific SQL features**
    
- You want to **optimize performance**
    
- You need **complex joins or aggregation**

---
### 🔹 Example:
```@Query(value = "SELECT * FROM employee WHERE department = :dept", nativeQuery = true)
List<Employee> findByDepartmentNative(@Param("dept") String department);
```
---

### 🔹 Important Points:

|Feature|Description|
|---|---|
|Query Type|Pure SQL|
|Keyword|`nativeQuery = true`|
|Parameter Binding|Using `@Param`|
|Return Type|Entity or DTO|
|Portability|Low (DB-specific)|
|Performance|High (manual optimization possible)|

---

### 🔹 Difference Between JPQL and Native Query

|Feature|JPQL|Native Query|
|---|---|---|
|Query Language|Entity-based|Table-based|
|Portability|High|Low|
|Use Case|Simple, abstracted queries|Complex SQL / DB-specific|
|Example|`SELECT e FROM Employee e`|`SELECT * FROM employee`|

---

### 🔹 Related Annotations

|Annotation|Usage|Description|
|---|---|---|
|`@Query(nativeQuery = true)`|Repository|Run raw SQL|
|`@NamedNativeQuery`|Entity|Define reusable SQL query|
|`@NamedNativeQueries`|Entity|Multiple named queries|
|`@SqlResultSetMapping`|Entity|Map result manually to Entity/DTO|
|`@EntityResult`|Inside `@SqlResultSetMapping`|Map SQL columns to entity fields|
|`@FieldResult`|Inside `@EntityResult`|Custom column-field mapping|
|`@ColumnResult`|Inside `@SqlResultSetMapping`|Map single column to DTO field|
|`@ConstructorResult`|Inside `@SqlResultSetMapping`|Map result to DTO constructor|

---

### 🔹 Example — DTO Mapping with @SqlResultSetMapping

```
@SqlResultSetMapping(
    name = "EmployeeDTOMap",
    classes = @ConstructorResult(
        targetClass = EmployeeDTO.class,
        columns = {
            @ColumnResult(name = "name"),
            @ColumnResult(name = "salary")
        }
    )
)
@NamedNativeQuery(
    name = "Employee.getEmployeeDTOs",
    query = "SELECT name, salary FROM employee",
    resultSetMapping = "EmployeeDTOMap"
)
@Entity
public class Employee {
    @Id
    private Long id;
}
```


### ⚙️ **1. @Query (nativeQuery = true)**

Used inside a **repository interface** to execute raw SQL.

```
public interface EmployeeRepository extends JpaRepository<Employee, Long> {

    @Query(value = "SELECT * FROM employee WHERE salary > :salary", nativeQuery = true)
    List<Employee> findBySalaryGreater(@Param("salary") Double salary);
}
```

**📘 Key Points:**

- `nativeQuery = true` → marks it as SQL (not JPQL).
    
- Automatically maps result columns to **entity fields** (by name).
    
- Supports parameters with `@Param`.
    

---

### 🧩 **2. @NamedNativeQuery**

You can define **named native queries** at the **entity level**.  
This helps reuse queries without repeating them in repositories.

```
@Entity
@NamedNativeQuery(
    name = "Employee.findByDepartment",
    query = "SELECT * FROM employee WHERE department = :dept",
    resultClass = Employee.class
)
public class Employee {
    @Id
    private Long id;
    private String name;
    private String department;
}

```

Then use in repository:

```
@Query(nativeQuery = true, name = "Employee.findByDepartment")
List<Employee> findByDepartment(@Param("dept") String dept);

```

✅ **When to use:**  
If you have complex or frequently reused queries.

---

### 🧱 **3. @SqlResultSetMapping**

Used to **map SQL query results** (which may not match your entity exactly)  
to either:

- An **entity**, or
    
- A **DTO (custom class)**.

---

#### **Example 1: Mapping to Entity**

```
@Entity
@SqlResultSetMapping(
    name = "EmployeeMapping",
    entities = @EntityResult(entityClass = Employee.class)
)
@NamedNativeQuery(
    name = "Employee.getAllEmployees",
    query = "SELECT * FROM employee",
    resultSetMapping = "EmployeeMapping"
)
public class Employee {
    @Id
    private Long id;
    private String name;
    private Double salary;
}
```
---

#### **Example 2: Mapping to DTO using ConstructorResult**

```
@SqlResultSetMapping(
    name = "EmployeeDTOMap",
    classes = @ConstructorResult(
        targetClass = EmployeeDTO.class,
        columns = {
            @ColumnResult(name = "name", type = String.class),
            @ColumnResult(name = "salary", type = Double.class)
        }
    )
)
@NamedNativeQuery(
    name = "Employee.getEmployeeDTOs",
    query = "SELECT name, salary FROM employee",
    resultSetMapping = "EmployeeDTOMap"
)
@Entity
public class Employee {
    @Id
    private Long id;
    private String name;
}

```

DTO class:

```
`public class EmployeeDTO {     private String name;     private Double salary;      public EmployeeDTO(String name, Double salary) {         this.name = name;         this.salary = salary;     } }`
```
**Usage in repository:**

`@Query(nativeQuery = true, name = "Employee.getEmployeeDTOs") List<EmployeeDTO> getEmployeeDTOs();`

✅ **When to use:**  
When your SQL returns **custom columns**, **aggregates**, or **join results** not matching a single entity.

---

### 🔍 **4. @EntityResult, @FieldResult, @ColumnResult**

These annotations help define **how to map SQL result columns** to entity fields.

#### Example:

```
@SqlResultSetMapping(
    name = "EmployeeDeptMap",
    entities = @EntityResult(
        entityClass = Employee.class,
        fields = {
            @FieldResult(name = "id", column = "emp_id"),
            @FieldResult(name = "name", column = "emp_name"),
            @FieldResult(name = "department", column = "dept_name")
        }
    )
)

```

✅ **Use when:** Column names differ from entity fields.

---

### 🧮 **5. @NamedNativeQueries (for multiple queries)**

If you want to define multiple named native queries in one entity:
```
@Entity
@NamedNativeQueries({
    @NamedNativeQuery(
        name = "Employee.findAll",
        query = "SELECT * FROM employee",
        resultClass = Employee.class
    ),
    @NamedNativeQuery(
        name = "Employee.findByDept",
        query = "SELECT * FROM employee WHERE department = :dept",
        resultClass = Employee.class
    )
})
public class Employee { ... }

```

---

### 🧠 **6. EntityManager + Native Query**

If you want **full control**, you can use `EntityManager` manually.

```
@Autowired
private EntityManager em;

public List<Employee> getEmployees() {
    Query query = em.createNativeQuery("SELECT * FROM employee", Employee.class);
    return query.getResultList();
}

```

✅ Useful for **dynamic** or **runtime-built** SQL queries.
---

## ⚙️ **2️⃣ Dynamic Native Query**

### 🔹 Definition:

A **Dynamic Native Query** is built **at runtime** using `EntityManager`.  
Useful when query filters depend on **user input or optional parameters**.

---

### 🔹 Example:

```
@PersistenceContext
private EntityManager entityManager;

public List<Employee> searchEmployees(String dept, Double minSalary, Double maxSalary) {
    StringBuilder sql = new StringBuilder("SELECT * FROM employee WHERE 1=1 ");

    if (dept != null) sql.append("AND department = :dept ");
    if (minSalary != null) sql.append("AND salary >= :minSalary ");
    if (maxSalary != null) sql.append("AND salary <= :maxSalary ");

    Query query = entityManager.createNativeQuery(sql.toString(), Employee.class);
    if (dept != null) query.setParameter("dept", dept);
    if (minSalary != null) query.setParameter("minSalary", minSalary);
    if (maxSalary != null) query.setParameter("maxSalary", maxSalary);

    return query.getResultList();
}

```

✅ Safe (uses parameter binding)  
✅ Flexible (build conditions dynamically)

---

### 🔹 Best Practices:

- Always use `setParameter()` (avoid SQL injection)
    
- Use `StringBuilder` for performance
    
- Keep conditions modular (add only if needed)
    
- Map result to entity or DTO manually
    

---

## 🧠 **3️⃣ Criteria API (JPA Standard)**

### 🔹 Definition:

The **Criteria API** is a **type-safe**, **programmatic**, and **dynamic** way to build JPQL queries at runtime.

It’s part of `javax.persistence.criteria`.

---

### 🔹 Steps:

1. Get `CriteriaBuilder` from `EntityManager`
    
2. Create `CriteriaQuery`
    
3. Define `Root` (entity)
    
4. Add conditions (`Predicate`)
    
5. Execute query
    

---

### 🔹 Example: Dynamic Query with Criteria API

```
CriteriaBuilder cb = entityManager.getCriteriaBuilder();
CriteriaQuery<Employee> cq = cb.createQuery(Employee.class);
Root<Employee> root = cq.from(Employee.class);

List<Predicate> predicates = new ArrayList<>();
if (dept != null) predicates.add(cb.equal(root.get("department"), dept));
if (minSalary != null) predicates.add(cb.greaterThanOrEqualTo(root.get("salary"), minSalary));

cq.select(root).where(cb.and(predicates.toArray(new Predicate[0])));
return entityManager.createQuery(cq).getResultList();
```

---

### 🔹 Common Operations

|Operation|Method|
|---|---|
|Equal|`cb.equal()`|
|Greater / Less|`cb.greaterThan()`, `cb.lessThan()`|
|Like|`cb.like()`|
|AND / OR|`cb.and()`, `cb.or()`|
|Join|`root.join("relation")`|
|Order By|`cq.orderBy(cb.asc(root.get("field")))`|
|Group By|`cq.groupBy(root.get("field"))`|

---

### 🔹 Advantages

✅ Type-safe (compile-time checking)  
✅ Dynamic (build on runtime)  
✅ No SQL injection  
✅ DB independent (JPQL-based)

🔸 **Downside:** verbose syntax

---

## 🌱 **4️⃣ Specification API (Spring Data JPA)**

### 🔹 Definition:

The **Specification API** is a **Spring abstraction** built **on top of Criteria API**, providing a cleaner way to build reusable dynamic filters.

---

### 🔹 Prerequisite:

Your repository must extend:

```
public interface EmployeeRepository
        extends JpaRepository<Employee, Long>,
                JpaSpecificationExecutor<Employee> {}
```
---

### 🔹 Basic Example:

```
public class EmployeeSpecification {
    public static Specification<Employee> hasDepartment(String dept) {
        return (root, query, cb) -> cb.equal(root.get("department"), dept);
    }

    public static Specification<Employee> salaryGreaterThan(Double salary) {
        return (root, query, cb) -> cb.greaterThan(root.get("salary"), salary);
    }
}
```

Usage:

```
Specification<Employee> spec = Specification
        .where(EmployeeSpecification.hasDepartment("HR"))
        .and(EmployeeSpecification.salaryGreaterThan(40000.0));

List<Employee> result = employeeRepo.findAll(spec);

```

---

### 🔹 Dynamic Example:

```
public List<Employee> search(String dept, Double minSalary, Double maxSalary) {
    Specification<Employee> spec = Specification.where(null);

    if (dept != null) spec = spec.and((r, q, cb) -> cb.equal(r.get("department"), dept));
    if (minSalary != null) spec = spec.and((r, q, cb) -> cb.greaterThanOrEqualTo(r.get("salary"), minSalary));
    if (maxSalary != null) spec = spec.and((r, q, cb) -> cb.lessThanOrEqualTo(r.get("salary"), maxSalary));

    return employeeRepo.findAll(spec);
}

```

---

### 🔹 With Pagination and Sorting:

```
Pageable pageable = PageRequest.of(0, 10, Sort.by("salary").descending());
Specification<Employee> spec = Specification.where(EmployeeSpecification.hasDepartment("IT"));
Page<Employee> page = employeeRepo.findAll(spec, pageable);

```

---

### 🔹 Joins Example:

```
public static Specification<Employee> hasDepartmentName(String deptName) {
    return (root, query, cb) -> cb.equal(root.join("department").get("name"), deptName);
}

```

---

### 🔹 Key Specification Methods:

|Method|Description|
|---|---|
|`where()`|Starting point|
|`and()`|Combine with AND|
|`or()`|Combine with OR|
|`not()`|Negate condition|
|`findAll(Specification, Pageable)`|Combine with pagination|
|`count(Specification)`|Count with filter|

---

### 🔹 Advantages:

✅ Cleaner than Criteria API  
✅ Type-safe  
✅ Reusable (each condition can be a method)  
✅ Works with Pagination & Sorting  
✅ Great for dynamic search filters

---

### 🔹 Comparison — Criteria vs Specification

|Feature|Criteria API|Specification API|
|---|---|---|
|Type|JPA Standard|Spring abstraction|
|Readability|Verbose|Cleaner|
|Reusability|Medium|High|
|Portability|High|High|
|Suitable for|Dynamic queries|Dynamic + reusable filters|

---

## 🧾 **Summary Chart**

|Query Type|Description|Example|Use When|
|---|---|---|---|
|**Derived Query**|Based on method name|`findByName()`|Simple filters|
|**JPQL Query**|Entity-based query|`@Query("SELECT e FROM Employee e")`|Complex but portable|
|**Native Query**|SQL directly|`@Query(nativeQuery=true)`|DB-specific or optimized SQL|
|**Criteria API**|Type-safe JPQL builder|via `CriteriaBuilder`|Dynamic, runtime-built|
|**Specification API**|Spring wrapper on Criteria|via `Specification`|Clean dynamic filtering|

## ==Common Attacks==
## **CSRF (Cross-Site Request Forgery)**

### **1. Definition**

**CSRF (Cross-Site Request Forgery)** is a type of web security vulnerability that tricks a **logged-in user’s browser** into sending **unauthorized requests** to a web application on behalf of that user.

In short, it **forges a request** from a trusted user without their consent.

---

### **2. Example in Simple Words**

Imagine:

- You’re logged into your **bank account** (`bank.com`).
    
- In another tab, you visit a **malicious website** (`evil.com`).
    
- That malicious site secretly sends a **POST request** to `bank.com/transfer?to=attacker&amount=50000`.
    

Because your **session cookie** is still valid (you’re logged in), the bank server **thinks it’s you** and transfers the money.  
You didn’t click “transfer” on the bank site — it was **forged**.

---

### **3. How CSRF Works (Step-by-Step Flow)**

1. **User Login**  
    User logs into a trusted site (e.g., `bank.com`) → browser stores session cookies.
    
2. **Malicious Site Visit**  
    User visits a malicious site (`evil.com`) while still logged into `bank.com`.
    
3. **Forged Request Sent**  
    The malicious page contains a hidden form or image tag like:
    
	  ```
	  <form action="https://bank.com/transfer" method="POST">
	  <input type="hidden" name="to" value="attacker123">
	  <input type="hidden" name="amount" value="10000">
	</form>
	<script>document.forms[0].submit();</script>
	
	  ```
	    
    Or it could even be a fake image:
    
    `<img src="https://bank.com/transfer?to=attacker&amount=10000">`
    
4. **Browser Automatically Sends Cookies**  
    Since the cookie for `bank.com` is valid, the request includes it automatically.
    
5. **Server Executes Request**  
    The server processes it as a legitimate user action — funds transferred!
    

---

### **4. Real-World Example**

**Scenario:**

- Website: `https://shop.com`
    
- Authenticated user: logged in as Alice.
    

If Alice clicks a link on `evil-site.com` that secretly executes:

`<img src="https://shop.com/api/deleteAccount">`

Then `shop.com` might delete Alice’s account if it doesn’t verify the source of the request — because her cookies are valid.

---

### **5. Prevention Techniques**

**a. CSRF Token (Synchronizer Token Pattern)**

- Server includes a **random token** in every form or request.
    
- Example:
    
    `<input type="hidden" name="csrf_token" value="a1b2c3d4e5">`
    
- When the request comes, the server validates this token.
    
- Attackers can’t know or guess this token because it’s stored server-side per session.
    

**b. SameSite Cookie Attribute**

- Adds protection at the browser level.
    
- Example:
    
    `Set-Cookie: session=abc123; SameSite=Strict`
    
- Prevents the browser from sending cookies when the request comes from another site.
    
**c. Double Submit Cookie Pattern**

- Token stored both in a cookie and a form field; server verifies they match.
    
**d. Checking Referer or Origin Header**

- Server checks that the request comes from the same domain.
    
**e. Avoiding GET for State-Changing Actions**

- Use `POST` or `PUT` for sensitive actions; GET should be **read-only**.

---
### **6. Real Framework Example**

#### **Spring Boot (Java)**

Spring Security automatically adds CSRF protection.

- In forms:
    
    `<form action="/transfer" method="post">     <input type="hidden" name="_csrf" value="${_csrf.token}"> </form>`
    
- In backend:  
    CSRF tokens are auto-generated and validated by Spring Security filters.

# What is XSS?

Cross-Site Scripting (XSS) is a client-side injection vulnerability where an attacker manages to get **their script or HTML executed in other users’ browsers** within the context (origin) of a vulnerable site. Execution happens with the site’s privileges — which means attackers can act as the victim in that site’s context.

# Types of XSS

1. **Stored (Persistent)**  
    Malicious payload is saved on the server (comment, profile, post). Every visitor who loads the page executes it.
    
2. **Reflected (Non-persistent)**  
    Payload is sent in a request (query, form) and reflected immediately in the response. Attacker must trick victim to open a crafted URL.
    
3. **DOM-based**  
    The vulnerability exists in client-side JS manipulating DOM with untrusted input (e.g., `location`, `hash`, `search`). The server may never see the payload.
    

# Attack flow (simple)

1. Attacker injects payload (stored/reflected/DOM).
    
2. Victim loads a page that includes the payload.
    
3. Browser executes script as the vulnerable origin.
    
4. Script can read accessible storage, perform actions, alter UI, or exfiltrate data.
    

# Real-world consequences

- Steal session tokens (if accessible), credentials, or sensitive UI data.
    
- Perform actions on behalf of users (change settings, transfer funds).
    
- Insert phishing overlays or keyloggers.
    
- Self-propagating worms (e.g., Samy/MySpace-style).
    

# Dangerous sinks (where code gets executed)

- `innerHTML`, `outerHTML`, `document.write`, `insertAdjacentHTML`
    
- `eval()`, `new Function()`, `setTimeout(string)`
    
- Event attributes (`onerror`, `onclick` inserted unsafely)
    
- Template or string concatenation into HTML or JS contexts

## **CORS (Cross-Origin Resource Sharing)**

### **1. Definition**

**CORS** is a **browser security mechanism** that controls **how a web page running on one origin** (domain, protocol, and port) can **request resources from another origin**.

It’s like a bouncer at a club checking IDs — even if two sites look friendly, the browser won’t let them mingle unless one explicitly says, “It’s okay, this one’s with me.”

---

### **2. Why CORS Exists**

Modern browsers enforce the **Same-Origin Policy (SOP)** for security.  
**Same-Origin Policy** says:

> A web page can only request data from the same origin (same domain + port + protocol).

Without this rule, any malicious site could secretly fetch your bank data while you’re logged in.

But — sometimes cross-origin requests are legitimate (e.g., a frontend on `frontend.com` calling an API at `api.backend.com`).  
That’s where **CORS** comes in — it allows _controlled relaxation_ of the same-origin policy.

---

### **3. What Is an Origin?**

An **origin** is defined as:

`protocol + domain + port`

Examples:

- `https://example.com` → Origin: `https://example.com:443`
    
- `http://example.com:8080` → Different origin (different protocol/port)
    
- `https://api.example.com` → Different origin (different subdomain)
    

---

### **4. How CORS Works (Step-by-Step)**

Let’s say:

- Frontend runs on `https://app.com`
    
- Backend API runs on `https://api.app.com`
    

When the frontend JavaScript tries:

`fetch("https://api.app.com/data")`

The browser checks:  
“Different origin? Yup → let’s enforce CORS.”

#### **Step 1: The Request**

Browser sends an HTTP request with an **Origin** header:

`Origin: https://app.com`

#### **Step 2: The Server’s Response**

If the server allows it, it must reply with:

`Access-Control-Allow-Origin: https://app.com`

Now the browser knows it’s allowed.  
If that header is missing or doesn’t match, the browser **blocks the response** (even though the network request technically succeeded).

# 🧱 SPRING SECURITY ARCHITECTURE
---
[Notes](https://onedrive.live.com/personal/6b364628c29feb52/_layouts/15/Doc.aspx?sourcedoc={b06d0b4b-3c6e-4388-8c56-0d8ed130ea41}&action=view&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0Vrc0xiYkJ1UEloRGpGWU5qdEV3NmtFQjd3UnhlNXdkMm9XWFJFTDlnS3BoRWc&wd=target%28SpringBoot.one%7C80d0b2b8-f2e3-1b4b-baff-c5631c171a8d%2FSpringBoot%20Security%20-%201%7C80fb6cd7-a41f-df43-8d97-d0b74d90e1d6%2F%29&wdorigin=NavigationUrl)
## 🔹 1. Overview

Spring Security is a **powerful filter-based security framework** used to protect applications through:

- **Authentication** → verifying _who_ the user is
    
- **Authorization** → verifying _what_ the user can do
    

All HTTP requests flow through a **chain of filters** before reaching your controller.

---

![[Pasted image 20251105164033.png]]

---
## 🔹 3. Security Filter Chain (Core of Spring Security)

Spring Security’s magic starts with the **`FilterChainProxy`**,  
which maintains a list of security filters (called the **Security Filter Chain**).

Each filter performs a specific step in authentication/authorization.

Example of key filters:

1. **SecurityContextPersistenceFilter** – Loads security context (if user is logged in).
    
2. **UsernamePasswordAuthenticationFilter** – Handles form login.
    
3. **BasicAuthenticationFilter** – Handles Basic Auth.
    
4. **BearerTokenAuthenticationFilter** – Handles JWT/OAuth tokens.
    
5. **ExceptionTranslationFilter** – Handles access denied or authentication errors.
    
6. **FilterSecurityInterceptor** – Final access check (authorization).
    

All these are automatically registered when you add:

`<dependency>     <groupId>org.springframework.boot</groupId>     <artifactId>spring-boot-starter-security</artifactId> </dependency>`

---
## 🔹 4. Step-by-Step Architecture Flow

Let’s break the entire **security flow** down from request to controller:

---
### 🧩 **Step 1: Incoming HTTP Request**

A client (browser, Postman, mobile app, etc.) sends a request to your app (e.g., `/login` or `/api/users`).

Before reaching Spring MVC, the request passes through the **Servlet Filter chain** managed by Spring Security.

---
### 🧩 **Step 2: FilterChainProxy Invokes Security Filters**

The request enters the **Security Filter Chain** (via `FilterChainProxy`).

Each filter gets a chance to process or inspect the request.  
For example:

- Extract username/password from the body.
    
- Extract JWT token from headers.
    
- Validate sessions or cookies.

---
### 🧩 **Step 3: Authentication Filter Creates an Authentication Object**

A filter like `UsernamePasswordAuthenticationFilter` (for login)  
or `JwtAuthenticationFilter` (for token-based login)  
creates an **Authentication object** that contains the user’s credentials.

Example:

`new UsernamePasswordAuthenticationToken("john", "1234");`

This token is passed to the **AuthenticationManager** for verification.

---
### 🧩 **Step 4: AuthenticationManager Delegates to AuthenticationProviders**

The **AuthenticationManager** (implemented by `ProviderManager`)  
is the coordinator that doesn’t authenticate itself — it just delegates.

It loops through a list of **AuthenticationProviders**:

```
for (AuthenticationProvider provider : providers) {
    if (provider.supports(authentication.getClass())) {
        return provider.authenticate(authentication);
    }
}
```

Each provider specializes in authenticating a specific type of token (e.g. DB, LDAP, JWT).

---
### 🧩 **Step 5: AuthenticationProvider Performs Real Authentication**

The chosen **AuthenticationProvider**:

- Validates credentials (password match, token validity, etc.)
    
- Uses a `UserDetailsService` (for DB users) or token logic (for JWT)
    
- Returns an authenticated `Authentication` object if successful
    

Example:  
`DaoAuthenticationProvider` uses `UserDetailsService` and `PasswordEncoder`.

---
### 🧩 **Step 6: SecurityContextHolder Stores Authentication**

Once authentication succeeds:

- Spring Security creates an `Authentication` object with user info and roles.
    
- This is stored in the **SecurityContext**, via **`SecurityContextHolder`** (ThreadLocal storage).
    

`SecurityContextHolder.getContext().setAuthentication(auth);`

Now any part of the app (controller, service, etc.) can access:

`Authentication auth = SecurityContextHolder.getContext().getAuthentication();`

---
### 🧩 **Step 7: Authorization Check (Access Control)**

After authentication, before the controller runs, authorization checks occur:

- **URL-level authorization** via `HttpSecurity` config:
    
    ```
    http.authorizeHttpRequests(auth -> 
     auth.requestMatchers("/admin/**").hasRole("ADMIN")
         .anyRequest().authenticated());

    ```
    
- **Method-level authorization** via annotations:
    
    `@PreAuthorize("hasRole('ADMIN')")`
    

Spring verifies if the user’s roles/authorities allow access to the requested resource.

If denied → `AccessDeniedException` handled by `ExceptionTranslationFilter`.

---

### 🧩 **Step 8: Controller Executes**

If authentication and authorization pass successfully:

- The request proceeds to your controller.
    
- Your business logic executes normally.
    
---
### 🧩 **Step 9: Response Returned**

After controller processing:

- The `SecurityContext` remains valid for the session or until logout.
    
- Filters may again modify or clean up the response before it’s returned.
    

For stateless apps (JWT-based):

- No session — token must be re-sent on every request.

---
## 🔹 5. Internal Components Overview

|Component|Role|
|---|---|
|**SecurityFilterChain**|Group of security filters applied to requests|
|**FilterChainProxy**|Delegates incoming requests to the right filter chain|
|**AuthenticationManager (ProviderManager)**|Delegates to providers for authentication|
|**AuthenticationProvider**|Authenticates a specific type of request (DB, JWT, LDAP)|
|**UserDetailsService**|Loads user info from DB|
|**PasswordEncoder**|Validates password encryption|
|**SecurityContextHolder**|Stores Authentication info for current thread/request|
|**AccessDecisionManager**|Makes authorization decisions|
|**ExceptionTranslationFilter**|Handles auth-related exceptions|
|**FilterSecurityInterceptor**|Performs final access control check|

---

## 🔹 6. End-to-End Authentication Flow Summary

```
1️⃣ Client sends login or secured request
2️⃣ FilterChainProxy triggers appropriate AuthenticationFilter
3️⃣ AuthenticationFilter builds Authentication object
4️⃣ AuthenticationManager delegates to AuthenticationProvider
5️⃣ AuthenticationProvider validates user/token
6️⃣ On success → SecurityContextHolder stores Authentication
7️⃣ Authorization checks are applied
8️⃣ Controller executes business logic
9️⃣ Response returned to client

```

---

## 🔹 7. Analogy — Real World Example

|Spring Component|Real World Equivalent|
|---|---|
|**FilterChainProxy**|Building security gate system|
|**AuthenticationManager**|Security desk supervisor|
|**AuthenticationProvider**|Guards specialized for ID check, badge scan, etc.|
|**UserDetailsService**|Employee database lookup|
|**SecurityContextHolder**|Visitor entry log|
|**AccessDecisionManager**|Guard verifying if visitor can access a specific floor|
|**Controller**|Office room the visitor wants to enter|

---

## 🔹 8. Summary Diagram (Text Representation)

```
Client
 ↓
SecurityFilterChain
    ↓
  UsernamePasswordAuthenticationFilter
    ↓
  AuthenticationManager (ProviderManager)
    ↓
  AuthenticationProvider (e.g., DaoAuthenticationProvider)
    ↓
  UserDetailsService + PasswordEncoder
    ↓
  SecurityContextHolder (store auth info)
    ↓
Authorization checks
    ↓
Controller → Service → DB
    ↓
Response to client
```

## 📘 **Form-Based Authentication

### 🔹 1. Overview

Form-based authentication is a **stateful login mechanism** used in web applications.  
It authenticates users via an **HTML login form** and maintains login state using an **HTTP session**.

When a user tries to access a protected resource:

- Spring Security intercepts the request.
    
- Redirects to a login page (`/login` by default).
    
- After successful authentication, creates a **session** and stores the **SecurityContext**.
    

---

### 🔹 2. Core Flow

1. **User requests** a protected URL.
    
2. **Spring Security** detects user is unauthenticated → redirects to login page.
    
3. **User submits** credentials (POST to `/login` by default).
    
4. **AuthenticationManager** validates credentials using:
    
    - `UserDetailsService` → loads user details.
        
    - `PasswordEncoder` → validates password.
        
5. On success:
    
    - A session is created.
        
    - `SecurityContextHolder` stores the authenticated user.
        
    - User is redirected to the original URL (or default page).
        
6. On failure:
    
    - Redirects back to `/login?error`.
        

---

### 🔹 3. Default Behavior (Auto Configuration)

When you add:

`<dependency>   <groupId>org.springframework.boot</groupId>   <artifactId>spring-boot-starter-security</artifactId> </dependency>`

Spring Boot automatically:

- Generates a **default login form**.
    
- Creates a **default user** (`user`) with a random password (printed in console).
    
- Protects all routes by default.
    

---

### 🔹 4. Custom Configuration Example

```
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/login", "/register").permitAll()
                .requestMatchers("/admin/**").hasRole("ADMIN")
                .anyRequest().authenticated()
            )
            .formLogin(form -> form
                .loginPage("/my-login")
                .loginProcessingUrl("/process-login")
                .defaultSuccessUrl("/home", true)
                .failureUrl("/my-login?error=true")
                .permitAll()
            )
            .logout(logout -> logout
                .logoutUrl("/logout")
                .logoutSuccessUrl("/my-login?logout=true")
                .permitAll()
            );

        return http.build();
    }
}

```

**Custom HTML Login Form**

```
<form action="/process-login" method="post">
  <input type="text" name="username" placeholder="Username" required>
  <input type="password" name="password" placeholder="Password" required>
  <button type="submit">Login</button>
</form>

```

---

### 🔹 5. Session Handling

- Session is created **after successful login**.
    
- Authentication info (`SecurityContext`) is stored in the session.
    
- Default session timeout: **30 minutes** (configurable).
    

**Configuration:**

`server.servlet.session.timeout=20m`

**Session invalidation:**

`request.getSession().invalidate();`

---

### 🔹 6. Components Involved

|Component|Description|
|---|---|
|**`UsernamePasswordAuthenticationFilter`**|Handles form POST request for login|
|**`UserDetailsService`**|Loads user data (username, password, roles)|
|**`PasswordEncoder`**|Validates hashed passwords|
|**`AuthenticationManager`**|Coordinates authentication|
|**`SecurityContextHolder`**|Stores authentication object in session|
|**`SecurityContextPersistenceFilter`**|Saves/restores SecurityContext between requests|

---
### 🔹 7. Route Management

Control access using `.authorizeHttpRequests()`:

```
.requestMatchers("/admin/**").hasRole("ADMIN")
.requestMatchers("/user/**").hasAnyRole("USER", "ADMIN")
.requestMatchers("/public/**").permitAll()
.anyRequest().authenticated();

```

Or use annotations:

`@PreAuthorize("hasRole('ADMIN')") public String adminPage() { ... }`

Enable with:

`@EnableMethodSecurity`

---
### 🔹 8. Key Properties

|Property|Description|
|---|---|
|`loginPage("/url")`|Custom login page|
|`loginProcessingUrl("/url")`|Endpoint that handles form POST|
|`defaultSuccessUrl("/url", true)`|Redirect after login|
|`failureUrl("/url?error")`|Redirect on login failure|
|`logoutUrl("/url")`|Custom logout endpoint|
|`logoutSuccessUrl("/url")`|Redirect after logout|

---
### 🔹 9. Security Notes

- Always use **HTTPS** for form-based auth.
    
- Protect session cookies:  
    `server.servlet.session.cookie.secure=true`  
    `server.servlet.session.cookie.http-only=true`
    
- Enable CSRF protection (on by default).
    
- Use strong password hashing (`BCryptPasswordEncoder` recommended).
    
---
### 🔹 10. Summary

|Feature|Form-Based Auth|
|---|---|
|Type|Stateful|
|Credentials|Sent via HTML form|
|Session|Created after successful login|
|Best for|Web applications (UI-based)|
|Security|HTTPS + session timeout + CSRF protection|
|UX|Customizable login/logout flow|
## 📘 **Basic Authentication 
### 🔹 1. Overview

**Basic Authentication** is a **stateless** authentication mechanism defined by the HTTP standard (RFC 7617).

It sends the user’s credentials (username and password) with **every request** using the HTTP header:

`Authorization: Basic <Base64Encoded(username:password)>`

Unlike form-based auth, there is **no session** — the server verifies credentials on every request.

---

### 🔹 2. Core Flow

1. **Client** sends a request to a protected resource.
    
2. **Server (Spring Security)** responds with `401 Unauthorized` and a `WWW-Authenticate` header.
    
3. **Browser or client** prompts the user for credentials.
    
4. On next request, client sends:
    
    `Authorization: Basic dXNlcm5hbWU6cGFzc3dvcmQ=`
    
    (Base64 encoding of `username:password`)
    
5. **Spring Security** decodes credentials and authenticates via:
    
    - `UserDetailsService` → loads user info
        
    - `PasswordEncoder` → checks password
        
6. If valid → access granted.  
    If invalid → 401 response again.
    

---

### 🔹 3. Configuration in Spring Boot

**Example using Spring Security 6+ (Spring Boot 3.x):**

```
@Configuration
@EnableWebSecurity
public class SecurityConfig {

    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
        http
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
            )
            .httpBasic(withDefaults())     // Enables Basic Auth
            .csrf(csrf -> csrf.disable()); // Often disabled for APIs

        return http.build();
    }

    @Bean
    public UserDetailsService userDetailsService(PasswordEncoder encoder) {
        UserDetails user = User.builder()
            .username("admin")
            .password(encoder.encode("password"))
            .roles("ADMIN")
            .build();
        return new InMemoryUserDetailsManager(user);
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

---

### 🔹 4. How Credentials Are Sent

Each request must include:

`Authorization: Basic <Base64(username:password)>`

Example:

`Authorization: Basic YWRtaW46cGFzc3dvcmQ=`

Decoded: `admin:password`

This happens automatically in most tools:

- Browser login popup (native)
    
- Postman → “Basic Auth” tab
    
- `curl` → `curl -u admin:password http://localhost:8080/api`
    

---

### 🔹 5. Characteristics

|Feature|Description|
|---|---|
|**State**|Stateless — no session or cookies|
|**Transport**|Credentials sent with each request|
|**Encryption**|None (Base64 ≠ encryption, must use HTTPS)|
|**Authentication**|Done per request|
|**Authorization**|Uses roles from `UserDetailsService`|
|**Best for**|APIs, microservices, internal tools|

---

### 🔹 6. Advantages

✅ Simple and standard (built into HTTP)  
✅ Easy to test via Postman, curl, etc.  
✅ Stateless — ideal for REST APIs  
✅ No session storage overhead

---

### 🔹 7. Disadvantages

❌ Credentials are sent every time (risk without HTTPS)  
❌ No session = no “remember me” or custom login page  
❌ Not user-friendly (browser popup)  
❌ Can’t easily customize login/logout flows  
❌ Password exposed if intercepted without TLS

## ==JWT Auth==
[Notes](https://notebook.zohopublic.in/public/notes/bietvcd2cffdd8c7d449c839c007fecf8d562)
## ⚙️ What is JWT?

**JWT (JSON Web Token)** is a compact, stateless, URL-safe way of securely transmitting information between two parties (usually client ↔ server) as a **digitally signed JSON object**.

It’s widely used in **authentication and authorization** for APIs, microservices, and web apps.

---

## 🧩 Structure of JWT

A JWT has **three Base64URL-encoded parts**, separated by dots (`.`):

`Header.Payload.Signature`

### 1. **Header**

Specifies metadata about the token.

Example:

`{   "alg": "HS256",   "typ": "JWT" }`

- `alg`: algorithm used for signing (e.g. HS256, RS256)
    
- `typ`: token type (always “JWT”)
    

Encoded form:

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9`

---

### 2. **Payload**

Contains **claims** — statements about the user and token metadata.

Example:

```
{
  "sub": "pratik",
  "role": "ADMIN",
  "iat": 1731036720,
  "exp": 1731040320
}

```

Types of claims:

- **Registered**: predefined (`iss`, `sub`, `exp`, `iat`, `aud`)
    
- **Public**: custom claims shared publicly
    
- **Private**: app-specific claims (roles, permissions, etc.)
    

Encoded:

`eyJzdWIiOiJwcmF0aWsiLCJyb2xlIjoiQURNSU4iLCJleHAiOjE3MzEwNDAzMjB9`

---

### 3. **Signature**

Ensures the token wasn’t tampered with.

For HMAC (HS256):

`HMACSHA256(base64UrlEncode(header) + "." + base64UrlEncode(payload), secret)`

Example:

`SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`

Complete JWT:

`<Header>.<Payload>.<Signature>`

---

## 🔐 JWT Types

1. **Unsigned JWT** → Just header + payload (rare, insecure).
    
2. **JWS (JSON Web Signature)** → Signed JWT (most common).
    
3. **JWE (JSON Web Encryption)** → Encrypted JWT (used when payload must be confidential).
    

---

## 🧠 JWT vs JWE vs JWK

|Concept|Meaning|Purpose|
|---|---|---|
|**JWT**|JSON Web Token|The container for claims (data).|
|**JWS**|JSON Web Signature|A **signed JWT** ensuring integrity.|
|**JWE**|JSON Web Encryption|An **encrypted JWT** ensuring confidentiality.|
|**JWK**|JSON Web Key|JSON representation of cryptographic keys.|

### 🧩 How They Interrelate

```
JWT → JWS (signed)
JWT → JWE (encrypted)
JWS/JWE ← uses → JWK (keys)

```

---

### **Example JWK (Public RSA Key)**

```
{
  "kty": "RSA",
  "use": "sig",
  "kid": "12345",
  "n": "oahUI...W2c",
  "e": "AQAB"
}

```

- `kty`: Key type (`RSA`, `EC`, `oct`)
    
- `use`: Key purpose (`sig` = signing, `enc` = encryption)
    
- `kid`: Key ID
    
- `n`, `e`: RSA key parameters
    

JWK Sets (`JWKS`) are often published at:

`https://your-auth-server/.well-known/jwks.json`

and used by Spring Security to validate JWT signatures.

---

## ⚙️ How JWT Authentication Works in **Spring Security**

Here’s the **complete lifecycle** from login to authorization:

---

### 1. **User Login**

Client sends credentials:

```
POST /api/auth/login
{
  "username": "pratik",
  "password": "12345"
}
```

---

### 2. **Spring Authentication Flow**

1. Controller calls:
    
    `authManager.authenticate(new UsernamePasswordAuthenticationToken(username, password))`
    
2. `AuthenticationManager` delegates to `DaoAuthenticationProvider`.
    
3. `DaoAuthenticationProvider` calls your `UserDetailsService`.
    
4. `UserDetailsService` loads user from DB.
    
5. Password verified with `PasswordEncoder` (e.g., BCrypt).
    
6. On success, Spring creates an `Authentication` object.
    

---

### 3. **JWT Token Generation**

After successful authentication:

```
String token = Jwts.builder()
    .setSubject(username)
    .claim("roles", roles)
    .setIssuedAt(new Date())
    .setExpiration(new Date(System.currentTimeMillis() + 3600000)) // 1 hour
    .signWith(secretKey, SignatureAlgorithm.HS256)
    .compact();
```

Returned to client in the response:

`{   "token": "eyJhbGciOiJIUzI1NiIsInR..." }`

---

### 4. **Client Stores the Token**

The client stores it in `localStorage`, cookies, or memory.

All future requests include:

`Authorization: Bearer <JWT>`

---
### 5. **JWT Filter Intercepts Future Requests**

A `OncePerRequestFilter` validates tokens:

```
String jwt = authHeader.substring(7);
String username = jwtService.extractUsername(jwt);
UserDetails userDetails = userDetailsService.loadUserByUsername(username);
if (jwtService.isTokenValid(jwt, userDetails)) {
    UsernamePasswordAuthenticationToken authToken =
        new UsernamePasswordAuthenticationToken(userDetails, null, userDetails.getAuthorities());
    SecurityContextHolder.getContext().setAuthentication(authToken);
}
```

- Extracts token
    
- Verifies signature and expiration
    
- Loads user details
    
- Sets authentication in `SecurityContext`
    

---
### 6. **Authorization**

Spring checks access rules:

```
.authorizeHttpRequests(auth -> auth
    .requestMatchers("/admin/**").hasRole("ADMIN")
    .anyRequest().authenticated()
)
```

If the token’s roles match → request proceeds.

---
### 7. **No Session, Stateless**

- Spring **does not** maintain a session.
    
- Each request revalidates the JWT.
    
- Server remains **stateless** and scalable.
    

---
### 8. **Logout (Optional)**

- JWTs can’t be “invalidated” unless blacklisted.
    
- Usually just deleted on the client side.
    
- Short expiration times mitigate risk.
    
---
## ⚔️ **Production Reality**

|Concept|Used in Production|Why / Why Not|
|---|---|---|
|**JWS (signed JWT)**|✅ Yes|Most common, stateless, integrity via signature|
|**JWE (encrypted JWT)**|⚠️ Sometimes|Only if payload has sensitive info (e.g., PII)|
|**JWK/JWKS**|✅ Yes|Used for key distribution and verification|
|**Plain JWT (unsigned)**|❌ Never|No integrity or security|

Typical setup:

- JWT is **signed (JWS)** using RS256 or HS256.
    
- Transmitted via **HTTPS**.
    
- Verified using **JWKS endpoint** (Auth0, Keycloak, Cognito).
    
- Encrypted JWT (JWE) only in high-security environments (banks, healthcare).
    

---
## 🔑 Advantages

- Stateless (no session storage)
    
- Scalable and fast
    
- Integrity via cryptographic signature
    
- Easy to integrate with OAuth2 and SSO
    
---

## ⚠️ Limitations

- Tokens can’t be revoked (unless manually blacklisted)
    
- Payload visible (unless using JWE)
    
- Requires secure storage on client side
    
- If leaked → attacker has full access until expiry
    
---
## 🧬 Analogy

|Term|Analogy|
|---|---|
|JWT|Your passport|
|JWS|Signature on passport verifying authenticity|
|JWE|Passport sealed in an envelope for privacy|
|JWK|The government’s public key used to verify the signature|

---

## 🧾 Summary Flow Diagram

```
[Client] → POST /login (username, password)
     ↓
[AuthenticationManager]
     ↓
[DaoAuthenticationProvider]
     ↓
[UserDetailsService] → loads user from DB
     ↓
[PasswordEncoder] → verifies password
     ↓
[JWT Generated] → returned to client
     ↓
(Client stores JWT)
     ↓
(Client → API call with Bearer token)
     ↓
[JWT Filter] → validates token
     ↓
[SecurityContext] → user authenticated
     ↓
[Authorization checks → Controller executes ✅]
```

---

## OAUTH
[Notes](https://notebook.zohopublic.in/public/notes/bietv949cfd82a5804e0ea1d18400d3ff6fa3)


# 🧩 ROLE-BASED AUTHENTICATION 
---
## 1️⃣ What is Role-Based Authentication (RBAC)?

**Role-Based Authentication (or Authorization)** means:

- Once a user is authenticated (identity verified),
    
- Access is granted or denied based on **roles** assigned to that user.
    

Roles represent **job functions or privilege levels** — e.g., `ROLE_USER`, `ROLE_ADMIN`.

---

## 2️⃣ Authentication vs Authorization

|Concept|Meaning|Example|
|---|---|---|
|**Authentication**|Verifying identity (who you are)|Username/password check|
|**Authorization**|Determining access rights (what you can do)|Can this user access `/admin`?|

Spring Security handles both via the `SecurityFilterChain`.

---

## 3️⃣ Basic Role Flow in Spring Security

1. User logs in (via form, JWT, OAuth2, etc.)
    
2. Spring authenticates the credentials using a provider (e.g., `UserDetailsService`)
    
3. If valid:
    
    - Spring creates an `Authentication` object containing username + roles
        
    - Stores it in the `SecurityContext`
        
4. When you hit a protected endpoint, Spring checks if the user’s roles match the required ones.
    

---

## 4️⃣ Common Role Models

|Type|Example|Best for|
|---|---|---|
|**Simple Role Model**|`ROLE_USER`, `ROLE_ADMIN`|Small apps|
|**Permission Model**|`order_read`, `order_write`|Fine-grained control|
|**Hybrid (Role + Permission)**|`ROLE_ADMIN` → {`user_read`, `user_write`}|Enterprise-level|

---
## 1️⃣ What They Are

Both annotations belong to **Spring Method Security**, used for **method-level authorization** — deciding access **before or after** a method executes.

They work with Spring Expression Language (**SpEL**) and require:

`@EnableMethodSecurity(prePostEnabled = true)`

in your `@Configuration` class.

---

## 2️⃣ `@PreAuthorize`

Runs **before the method executes**.  
If the expression evaluates to `false`, the method is **never called** and an `AccessDeniedException` is thrown.

### ✅ Common Use Cases

- Restricting access based on **roles** or **authorities**
    
- Allowing users to access **their own data only**
    
### ✅ Examples

#### Role-based

```
@PreAuthorize("hasRole('ADMIN')")
public void deleteUser(Long id) {
    // Only admins can delete users
}
```

#### Authority-based

```
@PreAuthorize("hasAuthority('order_read')")
public List<Order> getOrders() {
    return orderRepository.findAll();
}
```

#### Conditional (user-specific access)

```
@PreAuthorize("#username == authentication.name or hasRole('ADMIN')")
public Account getAccount(String username) {
    // User can view their own account or if they’re an admin
    return accountRepository.findByUsername(username);
}
```

### 🧠 How it works

- Spring evaluates the SpEL expression before method call.
    
- Uses `authentication` (current user) and method parameters (`#paramName`).
    
- If false → access denied immediately.
    
---
## 3️⃣ `@PostAuthorize`

Runs **after the method executes**, but **before returning the result**.  
The expression is evaluated against the **return object** using the keyword `returnObject`.

### ✅ Common Use Cases

- When you need to inspect the **returned object** to decide if access should be granted.
    
- Often used for **ownership checks** on fetched data.

### ✅ Examples

#### Ownership check

```
@PostAuthorize("returnObject.owner == authentication.name")
public Document getDocument(Long id) {
    return documentRepository.findById(id).get();
}
```

→ Method runs, retrieves the document,  
→ then checks if the logged-in user owns it.  
If not → `AccessDeniedException`.

#### Role-based return check

```
@PostAuthorize("hasRole('ADMIN') or returnObject.public == true")
public Report getReport(Long id) {
    return reportService.findById(id);
}

```

→ Only admins or users requesting public reports can receive the response.

---
## 5️⃣ Setting Up Role-Based Auth

### Dependencies (Maven)

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

```

---

## 6️⃣ Basic In-Memory Role Setup

```
@Configuration
@EnableMethodSecurity // enables @PreAuthorize etc.
public class SecurityConfig {

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .csrf(csrf -> csrf.disable())
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/admin/**").hasRole("ADMIN")
                .requestMatchers("/user/**").hasAnyRole("USER", "ADMIN")
                .requestMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
            )
            .formLogin(Customizer.withDefaults()); // default login page
        return http.build();
    }

    @Bean
    public UserDetailsService userDetailsService(PasswordEncoder passwordEncoder) {
        UserDetails admin = User.withUsername("alice")
                .password(passwordEncoder.encode("admin123"))
                .roles("ADMIN")
                .build();

        UserDetails user = User.withUsername("bob")
                .password(passwordEncoder.encode("user123"))
                .roles("USER")
                .build();

        return new InMemoryUserDetailsManager(admin, user);
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

---

## 7️⃣ Controllers with Role Restrictions

```
@RestController
public class AppController {

    @GetMapping("/public/welcome")
    public String publicPage() {
        return "Welcome! Anyone can access this.";
    }

    @GetMapping("/user/dashboard")
    public String userPage() {
        return "Hello USER or ADMIN!";
    }

    @GetMapping("/admin/panel")
    public String adminPage() {
        return "Hello ADMIN!";
    }
}

```

- `/public/welcome` → no auth
    
- `/user/dashboard` → USER or ADMIN
    
- `/admin/panel` → only ADMIN
    

---

## 8️⃣ Method-Level Authorization

Spring Security allows **annotations** for per-method access using `@EnableMethodSecurity`.

### Enable it:

`@EnableMethodSecurity(prePostEnabled = true) public class SecurityConfig { }`

### Use annotations:

```
@Service
public class AccountService {

    @PreAuthorize("hasRole('ADMIN')")
    public void deleteAccount(Long id) {
        // Only admins can do this
    }

    @PreAuthorize("#username == authentication.name or hasRole('ADMIN')")
    public Account getAccount(String username) {
        // Users can see their own account; admins can see all
        return repo.findByUsername(username);
    }

    @PostAuthorize("returnObject.owner == authentication.name")
    public Order getOrder(Long id) {
        // After execution, check ownership
        return orderRepo.findById(id).orElseThrow();
    }
}

```

---

## 9️⃣ Authorities vs Roles

|Concept|Example|Access Check|
|---|---|---|
|**Role**|`ROLE_ADMIN`|`hasRole('ADMIN')`|
|**Authority**|`order_read`, `order_write`|`hasAuthority('order_read')`|

Roles are just special authorities prefixed with `"ROLE_"`.  
`hasRole('ADMIN')` → internally checks `hasAuthority('ROLE_ADMIN')`.

---

## 🔟 Using Permissions (`order_read` style)

```
UserDetails user = User.withUsername("john")
    .password(passwordEncoder.encode("password"))
    .authorities("order_read", "product_read")
    .build();

@PreAuthorize("hasAuthority('order_read')")
@GetMapping("/orders")
public List<Order> getOrders() {
    return orderService.findAll();
}

```

Now, your access control can be _action-based_, not just _role-based_.

---

## 1️⃣1️⃣ Combining Roles + Permissions (Enterprise Approach)

Typical schema:

```
users(id, username, password)
roles(id, name)
permissions(id, name)
user_roles(user_id, role_id)
role_permissions(role_id, permission_id)

```

At login:

- Load user → find roles → find all permissions of those roles → merge into `GrantedAuthority`
    
- Spring Security uses these authorities to enforce access.
    

---

## 1️⃣2️⃣ JWT Integration (Stateless Role-Based Auth)

In production, roles and authorities are often stored inside JWT claims.

**Example JWT payload:**

```
{
  "sub": "alice",
  "roles": ["ROLE_ADMIN"],
  "permissions": ["order_read", "order_write"],
  "exp": 1731081600
}

```

Then configure Spring Security to extract and convert those claims into authorities.

---

### Example Token Filter (simplified)

```
@Component
public class JwtAuthFilter extends OncePerRequestFilter {

    @Autowired
    private JwtService jwtService;

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain)
        throws ServletException, IOException {

        String token = jwtService.extractToken(request);
        if (token != null && jwtService.validateToken(token)) {
            String username = jwtService.extractUsername(token);
            List<GrantedAuthority> authorities = jwtService.extractRoles(token);
            Authentication auth = new UsernamePasswordAuthenticationToken(username, null, authorities);
            SecurityContextHolder.getContext().setAuthentication(auth);
        }
        filterChain.doFilter(request, response);
    }
}

```

JWT carries your user’s **roles** → you enforce them using `@PreAuthorize` or `hasRole()` like before.

---
## 1️⃣3️⃣ Refresh Tokens (for JWT)

- Access token = short-lived (e.g., 15 min)
    
- Refresh token = longer-lived (used to get new access token)
    
- Both can carry role info.
    

Spring Security can regenerate tokens transparently during re-authentication.

---
## 1️⃣4️⃣ Common Mistakes

❌ Forgetting `@EnableMethodSecurity` → `@PreAuthorize` won’t work  
❌ Mixing `hasRole("ROLE_ADMIN")` → should be `hasRole("ADMIN")`  
❌ Using plain text passwords → always `BCrypt`  
❌ Forgetting `.csrf().disable()` in stateless JWT APIs  
❌ Returning same response for all users without checking `SecurityContextHolder`

---
## 1️⃣5️⃣ Quick Reference Table

|Feature|Used For|Annotation / Method|
|---|---|---|
|URL-level access|Endpoint restriction|`.requestMatchers().hasRole()`|
|Method-level access|Service/controller logic|`@PreAuthorize`, `@PostAuthorize`|
|Authority-based|Fine-grained permissions|`hasAuthority()`|
|Role-based|Broad privileges|`hasRole()`|
|Enable method security|Activate annotations|`@EnableMethodSecurity`|
|JWT + roles|Stateless access control|`JwtAuthFilter`|
|Custom DB roles|Real-world mapping|`UserDetailsService`|

---
## ==🧩 What Are Microservices?==
[notes](https://onedrive.live.com/personal/6b364628c29feb52/_layouts/15/Doc.aspx?sourcedoc={92637273-69a9-4fcd-83cb-ce0c0db8053c}&action=view&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New%20Section%201.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FRestTemplate%7Ca363d75e-8180-4e4e-a0bc-3eef156936a4%2F%29&wdorigin=NavigationUrl)

A **microservices architecture** is a design pattern where a large application is divided into **multiple small, independent services**, each responsible for a specific functionality.

Each service:

- Runs in its **own process**
    
- Has its **own database** (data isolation)
    
- Communicates with others via **network calls (HTTP or messaging)**
    
- Can be **developed, deployed, and scaled independently**
    

---

### 🏗️ Core Principles

|Principle|Description|
|---|---|
|**Single Responsibility**|Each microservice focuses on one business capability (e.g., "Order Processing").|
|**Loose Coupling**|Services communicate via contracts (APIs), not shared memory.|
|**High Cohesion**|Each service owns its logic and data.|
|**Independent Deployment**|Teams can update or redeploy one service without impacting others.|
|**Decentralized Data Management**|No shared database — each service manages its own persistence layer.|

---

### 🧠 Why Microservices?

- **Scalability:** You can scale the heavy service only (e.g., “Search Service”).
    
- **Fault Isolation:** One failure doesn’t crash the whole system.
    
- **Technology Freedom:** Each service can use different stacks (Java, Go, Python, etc.).
    
- **Faster CI/CD:** Independent build and deployment pipelines.
    

---

### ⚠️ Challenges

- **Distributed complexity:** Debugging and tracing are harder.
    
- **Data consistency:** No cross-service transactions (need Saga, event-driven consistency).
    
- **Network overhead:** Calls between services add latency.
    
- **DevOps complexity:** You now manage tens or hundreds of deployables.
    

---

## 🧭 Communication Between Microservices

---

### 🧩 1. **Synchronous Communication (Request–Response)**

- Real-time interaction — service A calls service B and waits.
    
- Typically implemented with **HTTP (REST)** or **gRPC**.
    

**Example:**

`OrderService → ProductService → returns product details`

**Pros:**

- Simple request/response model.
    
- Easy to debug.
    

**Cons:**

- Tight coupling — if ProductService is down, OrderService fails.
    
- Adds latency (network + serialization).
    

---

### 🧩 2. **Asynchronous Communication (Event-Driven)**

- Service A doesn’t wait for a response.
    
- Communicates via **message brokers** (Kafka, RabbitMQ, etc.).
    
- Ideal for background tasks, notifications, and decoupled systems.
    

**Example:**

`OrderService → publishes "OrderCreatedEvent" → Kafka InventoryService → consumes event → updates stock NotificationService → consumes event → sends email`

**Pros:**

- Loose coupling between services.
    
- Better performance and fault tolerance.
    

**Cons:**

- More complex — eventual consistency.
    
- Debugging message flows is harder.
    

---

## ⚙️ Typical Spring Cloud Microservices Architecture
```             ┌──────────────────────────┐
             │        Client (UI)       │
             └────────────┬─────────────┘
                          │
                          ▼
                ┌───────────────────┐
                │  API Gateway       │
                └───────────────────┘
                          │
                          ▼
        ┌──────────┬──────────────┬──────────┐
        ▼           ▼              ▼          ▼
  User Service  Order Service  Product Service  Payment Service
        │           │              │          │
        └──────────► internal communication ◄─┘
                          │
                          ▼
                     Database(s)

```

### Components:

- **API Gateway (Spring Cloud Gateway):** Routes requests to backend services.
    
- **Eureka Server:** Service discovery (keeps track of registered microservices).
    
- **Config Server:** Central configuration management.
    
- **FeignClient:** Simplifies REST communication.
    
- **Resilience4j:** Adds retries, rate-limiting, and circuit breakers.
    
- **Zipkin/Sleuth:** Distributed tracing.
    

---

# ⚙️ **INTER-SERVICE COMMUNICATION METHODS**

---

## 1️⃣ **RestTemplate (Legacy, Blocking)**

---

### 📖 Definition

`RestTemplate` is a **synchronous (blocking)** HTTP client provided by Spring.  
Used to make HTTP requests (GET, POST, PUT, DELETE) between microservices.

---

### 🧱 Basic Example

```
RestTemplate restTemplate = new RestTemplate();
Product product = restTemplate.getForObject(
    "http://localhost:8081/api/products/1",
    Product.class
);

```

---

### 🧠 Internal Working (Detailed)

When you call `restTemplate.getForObject()`:

1. **Builds the HTTP request**
    
    - Uses a `ClientHttpRequestFactory` (default: `SimpleClientHttpRequestFactory`)
        
2. **Sends the request** via HTTP
    
    - Opens a blocking connection to the target service
        
3. **Receives the response**
    
    - Blocks until data is returned
        
4. **Handles errors**
    
    - Invokes `ResponseErrorHandler` for 4xx/5xx responses
        
5. **Converts response body**
    
    - Uses `HttpMessageConverter` (Jackson, XML, etc.) to map JSON → Java object
        

---

### 🧩 Internal Components

|Component|Role|
|---|---|
|**ClientHttpRequestFactory**|Creates HTTP requests (`HttpURLConnection`, Apache HttpClient, etc.)|
|**HttpMessageConverter**|Converts request/response bodies (JSON ↔ Java)|
|**ResponseErrorHandler**|Handles HTTP errors|
|**ClientHttpRequestInterceptor**|Adds headers, logging, authentication|

---

### ⚡ Example with Configuration

```
@Configuration
public class RestTemplateConfig {
    @Bean
    public RestTemplate restTemplate() {
        return new RestTemplate();
    }
}
```

With custom timeout:

`HttpComponentsClientHttpRequestFactory factory = new HttpComponentsClientHttpRequestFactory(); factory.setConnectTimeout(3000); factory.setReadTimeout(5000); restTemplate.setRequestFactory(factory);`

---
### ✅ Advantages

- Simple to use
    
- Great for small systems or internal APIs
    
- Mature and widely supported
    
### ❌ Disadvantages

- **Blocking I/O** — one thread per request
    
- **Not scalable** for high concurrency
    
- Deprecated in favor of **`RestClient`**
    
---
## 2️⃣ **RestClient (Spring 6+, Modern Replacement)**

---

### 📖 Definition

`RestClient` is the **modern, fluent, synchronous HTTP client** introduced in **Spring Framework 6** and **Spring Boot 3**.  
It’s built on the **new HttpExchange API**, providing a cleaner, safer design.

---

### ⚙️ Example

```
RestClient restClient = RestClient.create();
Product product = restClient.get()
    .uri("http://localhost:8081/api/products/{id}", 1)
    .retrieve()
    .body(Product.class);

```

---

### ⚙️ Configuration Example

```
@Bean
public RestClient restClient() {
    return RestClient.builder()
            .baseUrl("http://product-service/api")
            .build();
}

```

---

### 🧠 Internal Working

- Uses new **`HttpExchange` layer** (shared with `WebClient`)
    
- Uses **`HttpMessageConverters`** for serialization
    
- Provides **builder-based configuration** (`.baseUrl()`, `.defaultHeader()`, `.onStatus()`)
    

---

### ⚡ Error Handling Example

```
restClient.get()
    .uri("/products/{id}", id)
    .retrieve()
    .onStatus(HttpStatusCode::is4xxClientError,
        (req, res) -> { throw new RuntimeException("Not Found"); })
    .body(Product.class);

```

---

### ✅ Advantages

- Modern and clean syntax
    
- Easier configuration (base URL, headers)
    
- Inline error handling
    
- Future-proof replacement for `RestTemplate`
    

### ❌ Disadvantages

- Still **blocking**
    
- Requires Spring 6+
    

---

### ⚔️ RestTemplate vs RestClient

|Feature|RestTemplate|RestClient|
|---|---|---|
|Introduced|Spring 3|Spring 6|
|Blocking|Yes|Yes|
|API Style|Verbose|Fluent|
|Underlying Engine|Legacy HTTP stack|New HttpExchange|
|Error Handling|External|Inline|
|Status|Deprecated|Recommended|

---

## 3️⃣ **WebClient (Reactive, Non-blocking)**

---

### 📖 Definition

`WebClient` is part of **Spring WebFlux** — a **non-blocking, asynchronous** HTTP client.  
It’s designed for reactive programming and scalable I/O operations.

---

### ⚙️ Example — Non-blocking

```
WebClient webClient = WebClient.create("http://localhost:8081/api/products");

Mono<Product> productMono = webClient.get()
    .uri("/{id}", 1)
    .retrieve()
    .bodyToMono(Product.class);

```

To block synchronously:

`Product product = productMono.block();`

---

### ⚙️ Configuration

```
@Bean
public WebClient.Builder webClientBuilder() {
    return WebClient.builder()
        .baseUrl("http://product-service/api")
        .defaultHeader(HttpHeaders.CONTENT_TYPE, MediaType.APPLICATION_JSON_VALUE);
}

```

---

### 🧠 Internal Working

- Uses **reactor-netty** (asynchronous event loops)
    
- Doesn’t block threads — registers callbacks
    
- Operates with **Reactor types**:
    
    - `Mono<T>` → single result
        
    - `Flux<T>` → multiple results (stream)
        

---

### ⚡ Error Handling

```
webClient.get()
    .uri("/{id}", id)
    .retrieve()
    .onStatus(HttpStatusCode::is4xxClientError,
        response -> Mono.error(new RuntimeException("Client Error")))
    .onStatus(HttpStatusCode::is5xxServerError,
        response -> Mono.error(new RuntimeException("Server Error")))
    .bodyToMono(Product.class);
```

---

### ✅ Advantages

- Non-blocking & scalable
    
- High performance under heavy load
    
- Ideal for reactive pipelines (Project Reactor)
    
- Supports streaming and backpressure
    
### ❌ Disadvantages

- More complex (requires Reactor understanding)
    
- Debugging reactive flow is harder
    
---
## 4️⃣ **FeignClient (Declarative, Spring Cloud)**

---

### 📖 Definition

`FeignClient` is a **declarative REST client** provided by **Spring Cloud OpenFeign**.  
You define an interface, and Feign auto-generates the HTTP request logic.

---

### ⚙️ Example

```
@FeignClient(name = "product-service", url = "http://localhost:8081")
public interface ProductClient {
    @GetMapping("/api/products/{id}")
    Product getProductById(@PathVariable Long id);
}

```

Use it:

```
@Service
public class OrderService {
    private final ProductClient productClient;

    public OrderService(ProductClient productClient) {
        this.productClient = productClient;
    }

    public Product getProduct(Long id) {
        return productClient.getProductById(id);
    }
}
```

---

### ⚙️ Setup

`@SpringBootApplication @EnableFeignClients public class OrderServiceApplication { }`

---

### 🧠 Internal Working

1. Spring creates a **proxy** for each Feign interface.
    
2. When you call a method, the proxy:
    
    - Resolves the service name via **Eureka** (if registered)
        
    - Builds an HTTP request
        
    - Serializes parameters (to JSON)
        
    - Sends the request via **HTTP client (Apache/OkHttp)**
        
    - Deserializes response to return type
        

---

### ⚡ Fallback Example (Resilience4j)

```
@FeignClient(name = "product-service", fallback = ProductFallback.class)
public interface ProductClient {
    @GetMapping("/api/products/{id}")
    Product getProductById(@PathVariable Long id);
}

@Component
class ProductFallback implements ProductClient {
    public Product getProductById(Long id) {
        return new Product(id, "Unavailable", 0);
    }
}
```

---

### ✅ Advantages

- **Declarative** — no manual HTTP code
    
- Integrates with **Eureka**, **Resilience4j**, **LoadBalancer**
    
- Clean and simple for microservices
    

### ❌ Disadvantages

- Blocking (uses synchronous HTTP)
    
- Requires Spring Cloud setup
    
- Less flexible for custom HTTP behavior
    

---
# 🧩 **FeignClient — Method Handlers**

A Feign client interface looks like this:

`@FeignClient(name = "product-service") public interface ProductClient {      @GetMapping("/api/products/{id}")     Product getProductById(@PathVariable Long id); }`

Spring Cloud OpenFeign automatically translates each annotated method into an HTTP request — using the same annotation semantics as in `@RestController`.

Let’s go through **each method handler** one by one, with clear examples.

---

## 🟢 1️⃣ `@GetMapping` — GET Request

**Purpose:**  
Fetch data (no body) from another service.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @GetMapping("/api/products/{id}")
    Product getProductById(@PathVariable Long id);
}

```

**Equivalent HTTP Request:**

`GET /api/products/5`

**Usage:**  
Used for read operations — fetching a single record or list.

**Example Use Case:**  
OrderService calls ProductService to fetch product details before creating an order.

---

## 🟠 2️⃣ `@PostMapping` — POST Request

**Purpose:**  
Send data (request body) to create a new resource.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @PostMapping("/api/products")
    Product createProduct(@RequestBody Product product);
}

```

**Equivalent HTTP Request:**

`POST /api/products Content-Type: application/json Body: {   "name": "Laptop",   "price": 1200 }`

**Usage:**  
Used for create operations — creating new entities or sending structured data.

**Example Use Case:**  
AdminService sends a new product to ProductService to add it to inventory.

---

## 🔵 3️⃣ `@PutMapping` — PUT Request

**Purpose:**  
Update an existing resource (replace or modify).

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @PutMapping("/api/products/{id}")
    Product updateProduct(@PathVariable Long id, @RequestBody Product product);
}

```

**Equivalent HTTP Request:**

`PUT /api/products/10 Body: {   "name": "Updated Laptop",   "price": 999 }`

**Usage:**  
Used for updating existing data.

**Example Use Case:**  
ProductAdminService updates product pricing or details.

---

## 🔴 4️⃣ `@DeleteMapping` — DELETE Request

**Purpose:**  
Remove an existing resource.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @DeleteMapping("/api/products/{id}")
    void deleteProduct(@PathVariable Long id);
}

```

**Equivalent HTTP Request:**

`DELETE /api/products/15`

**Usage:**  
Used for delete operations.

**Example Use Case:**  
AdminService calls ProductService to remove discontinued products.

---

## 🟣 5️⃣ `@PatchMapping` — PATCH Request

**Purpose:**  
Partially update an existing resource (modify some fields).

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @PatchMapping("/api/products/{id}")
    Product updatePartialProduct(@PathVariable Long id, @RequestBody Map<String, Object> updates);
}

```

**Equivalent HTTP Request:**

`PATCH /api/products/12 Body: {   "price": 899 }`

**Usage:**  
Used for partial updates where you don’t want to send the whole object.

**Example Use Case:**  
DiscountService updates only the price of products during sale.

---

## ⚙️ 6️⃣ `@RequestMapping` — Generic (All HTTP Methods)

**Purpose:**  
If you want to explicitly define the method (GET, POST, etc.) without using the shorthand annotations.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @RequestMapping(method = RequestMethod.GET, value = "/api/products")
    List<Product> getAllProducts();
}

```

**Usage:**  
Older syntax, but still supported for flexibility.

---

## ⚡ 7️⃣ `@RequestParam` — Query Parameters

**Purpose:**  
Send query parameters in a request.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @GetMapping("/api/products/search")
    List<Product> searchProducts(@RequestParam String category, @RequestParam Double minPrice);
}

```

**Equivalent HTTP Request:**

`GET /api/products/search?category=Electronics&minPrice=1000`

**Usage:**  
Used for filtered queries or searches.

---

## 🧩 8️⃣ `@RequestHeader` — Custom Headers

**Purpose:**  
Send headers along with the HTTP request (like tokens, API keys, etc.)

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @GetMapping("/api/products/{id}")
    Product getProductById(@PathVariable Long id,
                           @RequestHeader("Authorization") String token);
}

```

**Equivalent HTTP Request:**

`GET /api/products/5 Authorization: Bearer <JWT_TOKEN>`

**Usage:**  
For authenticated calls between microservices.

---

## ⚙️ 9️⃣ `@RequestBody` — Send Data in Body

**Purpose:**  
Attach a request body (usually JSON) for POST/PUT/PATCH requests.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @PostMapping("/api/products")
    Product addProduct(@RequestBody Product product);
}

```

**Usage:**  
Whenever the receiving service expects a JSON object or DTO.

---

## 🧠 10️⃣ `@PathVariable` — Dynamic URL Segments

**Purpose:**  
Inject variables into URLs dynamically.

**Example:**

```
@FeignClient(name = "product-service")
public interface ProductClient {

    @GetMapping("/api/products/{id}")
    Product findById(@PathVariable("id") Long productId);
}

```

**Equivalent URL:**

`GET /api/products/5`

---

## ⚡ 11️⃣ `@RequestPart` — File Uploads (Multipart)

**Purpose:**  
Send multipart data (like images or files) via Feign.

**Example:**

```
@FeignClient(name = "file-service")
public interface FileClient {

    @PostMapping(value = "/upload", consumes = "multipart/form-data")
    String uploadFile(@RequestPart("file") MultipartFile file);
}


```

**Usage:**  
For file uploads between microservices.

---

# 🧠 **Internal Behavior of FeignClient**

When you call a Feign method (say `getProductById(1)`):

1. Spring creates a proxy implementation of your interface at runtime.
    
2. That proxy builds an HTTP request based on:
    
    - Mapping annotation (`@GetMapping`, etc.)
        
    - URL path and parameters
        
    - Headers and body (if any)
        
3. Feign uses the configured HTTP client (Apache/OkHttp) to send the request.
    
4. It deserializes the response into your return type (`Product`).
    
5. Optionally integrates with:
    
    - **Eureka** for service discovery
        
    - **Resilience4j** for circuit breaking
        
    - **Sleuth** for distributed tracing
        

---

# ✅ **Quick Summary Table**

|Annotation|HTTP Method|Purpose|Example|
|---|---|---|---|
|`@GetMapping`|GET|Fetch data|Fetch products|
|`@PostMapping`|POST|Create resource|Add new product|
|`@PutMapping`|PUT|Update resource|Update product info|
|`@PatchMapping`|PATCH|Partial update|Change product price|
|`@DeleteMapping`|DELETE|Remove resource|Delete product|
|`@RequestParam`|-|Add query params|`/products?category=Electronics`|
|`@PathVariable`|-|Path variables|`/products/{id}`|
|`@RequestHeader`|-|Custom headers|Add JWT token|
|`@RequestBody`|-|JSON payload|Send object data|
|`@RequestPart`|-|Multipart form|File upload|
|`@RequestMapping`|All|Generic handler|Legacy or flexible use|
# ⚙️ **Summary Comparison**

|Feature|RestTemplate|RestClient|WebClient|FeignClient|
|---|---|---|---|---|
|Introduced|Spring 3|Spring 6|Spring 5|Spring Cloud|
|Blocking|Yes|Yes|No|Yes|
|Style|Imperative|Fluent|Reactive|Declarative|
|Ideal for|Legacy apps|Modern sync apps|Reactive APIs|Microservices|
|Service Discovery|Manual|Manual|Manual|Built-in (Eureka)|
|Load Balancing|Manual|Manual|Manual|Built-in|
|Resilience4j|Manual|Manual|Manual|Built-in fallback|
|Status|Deprecated|Recommended|Recommended|Recommended|

---

# 🧩 **Communication Type Summary**

|Type|Example|Tools|
|---|---|---|
|**Synchronous**|OrderService → ProductService|RestTemplate, RestClient, WebClient, FeignClient|
|**Asynchronous**|OrderService → Kafka → InventoryService|Kafka, RabbitMQ, ActiveMQ|

---
# ==🧭 **Service Discovery==

---
[notes](https://onedrive.live.com/personal/6b364628c29feb52/_layouts/15/Doc.aspx?sourcedoc={92637273-69a9-4fcd-83cb-ce0c0db8053c}&action=view&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New%20Section%201.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FService%20Discovery%7Cbe9efdfc-f515-344f-b765-9b58c71e6cdb%2F%29&wdorigin=NavigationUrl)
## 🔹 **1. What is Service Discovery**

**Definition:**  
Service Discovery is the mechanism that allows microservices to **automatically register themselves** and **discover each other’s locations (IP + port)** dynamically, without hardcoding URLs.

It enables services to find each other in distributed systems where IPs and ports frequently change due to scaling, restarts, or containerization.

---
### **Without Service Discovery:**

Each service manually knows others’ URLs:

`User-Service → http://localhost:8081/order-service`

If any port or host changes, communication breaks.

### **With Service Discovery:**

Each service only knows the _service name_:

`User-Service → “order-service”`

The system dynamically resolves it to the correct instance using a **Service Registry**.

---

## 🔹 **2. Core Components**

|Component|Role|Description|
|---|---|---|
|**Service Registry**|Directory|Central registry storing all service names and network locations.|
|**Service Provider**|Register|A microservice that registers itself to the registry (e.g., Order-Service).|
|**Service Consumer**|Discover|A microservice that queries the registry to locate another service (e.g., User-Service).|

---

## 🔹 **3. Eureka Overview**

**Eureka** (part of Spring Cloud Netflix) is the most common implementation of Service Discovery in Spring Boot.

It has two parts:

- **Eureka Server** → Service Registry
    
- **Eureka Client** → Microservices that register and discover services
    

---

## 🔹 **4. How Eureka Works – Flow**

### **Step-by-step Communication Flow**

1. **Eureka Server Starts**
    
    - Central registry (empty initially).
        
    - Accessible at `http://localhost:8761`.
        
2. **Service Provider Registers**
    
    - Example: `order-service` starts.
        
    - It reads config:
```eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/
spring:
  application:
    name: order-service

```
    - Sends registration info to Eureka (IP, port, name).
        
3. **Eureka Updates Registry**
    
    `Registered Services:   - order-service → 192.168.1.10:8081`
    
4. **Provider Sends Heartbeats**
    
    - Every 30 seconds: “I’m alive.”
        
    - If no heartbeat after 90 seconds → Eureka evicts it.
        
5. **Consumer Fetches Registry**
    
    - Example: `user-service` downloads registry info.
        
    - Maintains a **local cache** for resilience.
        
6. **Consumer Calls Provider**
    
    - Uses Feign or WebClient:
```
@FeignClient(name = "order-service")
public interface OrderClient {
    @GetMapping("/orders/{id}")
    Order getOrder(@PathVariable Long id);
}
```
    - The name `"order-service"` is resolved via Eureka.
        
7. **Load Balancer Chooses Instance**
    
    - If multiple instances exist, Spring Cloud LoadBalancer picks one (Round Robin by default).
        

---

## 🔹 **5. Eureka Server Configuration**

```
@SpringBootApplication
@EnableEurekaServer
public class ServiceRegistryApplication {
    public static void main(String[] args) {
        SpringApplication.run(ServiceRegistryApplication.class, args);
    }
}

```

**application.yml**

```
server:
  port: 8761
eureka:
  client:
    register-with-eureka: false  # server doesn’t register itself
    fetch-registry: false        # server doesn’t fetch registry

```

---

## 🔹 **6. Eureka Client Configuration**

```
@SpringBootApplication
@EnableEurekaClient
public class OrderServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(OrderServiceApplication.class, args);
    }
}

```

**application.yml**

```
server:
  port: 8081
spring:
  application:
    name: order-service
eureka:
  client:
    serviceUrl:
      defaultZone: http://localhost:8761/eureka/

```

---

## 🔹 **7. Load Balancing**

Spring Cloud LoadBalancer automatically balances requests across multiple instances registered under the same name.

Example:

`order-service:   - 192.168.1.10:8081  - 192.168.1.11:8082`

Requests to `order-service` will be distributed evenly.

---

## 🔹 **8. Eureka Internals (Heartbeats & Self-Healing)**

|Setting|Description|Default|
|---|---|---|
|`lease-renewal-interval-in-seconds`|How often client sends heartbeat|30s|
|`lease-expiration-duration-in-seconds`|Time after which instance is removed|90s|

Eureka auto-removes dead or disconnected services — ensuring stale data doesn’t break communication.

---

## 🔹 **9. High Availability (HA Eureka Cluster)**

For production, use **multiple Eureka servers** that replicate data.

Example:

**Eureka Server 1 (8761)**

`eureka:   client:     serviceUrl:       defaultZone: http://eureka2:8762/eureka/`

**Eureka Server 2 (8762)**

`eureka:   client:     serviceUrl:       defaultZone: http://eureka1:8761/eureka/`

They sync service info with each other → fault tolerance.

---

## 🔹 **10. Local Cache and Fault Tolerance**

- Each Eureka client **caches** the registry locally.
    
- If the Eureka server goes down, services still communicate using cached data.
    
- Once the server is back, it resyncs automatically.
    

This gives Eureka an **AP (Available + Partition-tolerant)** nature in the **CAP theorem**.

---

## 🔹 **11. Manual Discovery (without Feign)**

`@Autowired private DiscoveryClient discoveryClient;  public List<ServiceInstance> getInstances() {     return discoveryClient.getInstances("order-service"); }`

This returns all live instances for a service — used in custom routing or diagnostics.

---

## 🔹 **12. Alternatives to Eureka**

|Tool|Description|Common Use|
|---|---|---|
|**Consul**|Key-Value based registry, health checks built-in|Multi-language systems|
|**Zookeeper**|Strong consistency, used in Kafka|Coordination-heavy systems|
|**Kubernetes DNS**|Native service discovery in K8s|Cloud-native apps|
|**AWS Cloud Map**|AWS service registry|AWS-based microservices|

---

## 🔹 **13. Security and Best Practices**

- Protect Eureka dashboard with **Spring Security** or network ACLs.
    
- Use **service-specific names** (`inventory-service`, `payment-service`) for clarity.
    
- Configure proper **heartbeat intervals** for faster fail detection.
    
- Use **HA setup** in production (2+ Eureka servers).
    
- Monitor registry with **Actuator endpoints** (`/actuator/eureka`).
    

---

## 🔹 **14. Summary (At a Glance)**

|Step|Action|Actor|
|---|---|---|
|1|Start Eureka Server|Registry|
|2|Service registers itself|Provider|
|3|Service sends heartbeats|Provider|
|4|Consumer fetches registry|Consumer|
|5|Consumer calls service via name|Feign/WebClient|
|6|LoadBalancer picks instance|Client|
|7|Eureka evicts dead services|Server|

---

## **==Load Balacing==**
[notes](https://onedrive.live.com/personal/6b364628c29feb52/_layouts/15/Doc.aspx?sourcedoc={92637273-69a9-4fcd-83cb-ce0c0db8053c}&action=view&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New%20Section%201.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FClient%20Side%20Load%20Balancer%7Ca0e35fce-9ab3-774d-a9a5-1a83bcd9e0f9%2F%29&wdorigin=NavigationUrl)
### ⚙️ **Definition**

Client-side load balancing means **the client itself distributes traffic** among multiple instances of a service.  
It fetches service instance details (from **Eureka** or another registry) and decides **which instance** to send the request to.

---

### 🧠 **Flow of Client-Side Load Balancing**

1. Each microservice (e.g., `ORDER-SERVICE`) registers with **Eureka Server**.
    
2. A client service (e.g., `PAYMENT-SERVICE`) requests instance info for `ORDER-SERVICE` from Eureka.
    
3. The **Spring Cloud LoadBalancer** (or old Netflix Ribbon) selects one instance using a load-balancing algorithm.
    
4. The client sends the request directly to the chosen instance.
    

---

### 🧩 **Example Setup**

**1. Eureka Server**

```
@EnableEurekaServer
@SpringBootApplication
public class EurekaServerApp {
  public static void main(String[] args) {
    SpringApplication.run(EurekaServerApp.class, args);
  }
}
```

**2. Client-Side Load Balancer Config**

```
@Configuration
public class Config {
  @Bean
  @LoadBalanced
  public RestTemplate restTemplate() {
    return new RestTemplate();
  }
}

```

**3. REST Call**

```
@RestController
public class PaymentController {
  @Autowired
  private RestTemplate restTemplate;

  @GetMapping("/pay")
  public String makePayment() {
    return restTemplate.getForObject("http://ORDER-SERVICE/order", String.class);
  }
}

```

---

## ⚙️ **Types of Load Balancers**

|Type|Where It Works|Example|Description|
|---|---|---|---|
|**Client-Side Load Balancer**|Inside client microservice|Spring Cloud LoadBalancer, Ribbon|Client selects target instance|
|**Server-Side Load Balancer**|Gateway/proxy|Spring Cloud Gateway, Zuul, NGINX|Gateway routes requests to instances|
|**Infrastructure Load Balancer**|Network/Cloud Layer|AWS ELB, HAProxy|Distributes external traffic to gateways/services|
|**DNS Load Balancer**|DNS level|AWS Route53, Cloudflare|Distributes requests globally by DNS resolution|
### ⚖️ **Common Load Balancing Algorithms**

|Algorithm|Description|Use Case|
|---|---|---|
|**Round Robin**|Sequentially routes requests to each instance|Default, equal servers|
|**Random**|Chooses an instance randomly|Light-weight, simple|
|**Weighted Round Robin**|Gives higher weight to stronger servers|Uneven capacity|
|**Least Connections**|Routes to instance with fewest connections|Long-lived sessions|
|**Response Time Based**|Routes to fastest instance|Dynamic systems|
|**IP Hash (Sticky Session)**|Same client always hits same instance|Stateful services|

---
## **==Fault tolerance==** 
[notes](https://onedrive.live.com/personal/6b364628c29feb52/_layouts/15/Doc.aspx?sourcedoc={92637273-69a9-4fcd-83cb-ce0c0db8053c}&action=view&redeem=aHR0cHM6Ly8xZHJ2Lm1zL28vYy82YjM2NDYyOGMyOWZlYjUyL0VuTnlZNUtwYWMxUGc4dk9EQTI0QlR3Qk5seWhEdlJlRWctS0RWWjdNZV9aWkE&wd=target%28New%20Section%201.one%7C1c705580-121a-3746-9837-b97f7646a06a%2FRateLimiter%20Fault-Tolerant%20Microservice%20%28Part-1%5C%29%7Ca0095666-1317-4f4c-b672-a8915839634d%2F%29&wdorigin=NavigationUrl)
in microservices (including Spring Boot) is the ability of a system to continue functioning even when some part of it fails — without crashing the entire application.

Think of it as _“graceful degradation”_ — instead of collapsing like a house of cards, the system limps along until repairs are made.

---
### ⚙️ Why It Matters

In distributed systems, **failures are inevitable**:

- a service might go down,
    
- a network call might time out,
    
- a dependency might return junk data.
    

Without fault tolerance, one bad microservice can cause a domino effect of crashes across your architecture.

---
### 🧩 Fault Tolerance in Spring Boot (via Spring Cloud)

Spring Boot itself doesn’t directly provide fault tolerance — it comes through **Spring Cloud** components (like **Resilience4j**, previously **Hystrix**).

## 🔁 1. RETRY

### 🧠 What It Does

If a request fails (like a timeout or network error), the system **automatically retries** it a few times before giving up.  
It’s useful when failures are _temporary_ (e.g. service momentarily down, flaky network).

---

### ⚙️ How It Works Internally

- Resilience4j wraps your method call inside a **proxy**.
    
- When the call fails (throws a retryable exception), the proxy retries it.
    
- It waits for a given **delay** before each retry (can use exponential backoff).
    
- If all retries fail → fallback method executes (if defined).
    

All retries happen **on the same thread** — it doesn’t spawn new threads.

---

### 🧾 Example

```
@Retry(name = "inventoryService", fallbackMethod = "fallbackInventory")
public String getInventory() {
    System.out.println("Calling inventory service...");
    return restTemplate.getForObject("http://inventory-service/items", String.class);
}

public String fallbackInventory(Exception e) {
    return "Default inventory data (service down)";
}

```

### 🧰 Config

```
resilience4j.retry:
  instances:
    inventoryService:
      maxAttempts: 3
      waitDuration: 2s
      retryExceptions:
        - java.io.IOException

```

**Flow:**  
Call → Failure → Retry 1 → Retry 2 → Success OR Fallback

---

### ⚡ Key Points

- Best for temporary, recoverable errors.
    
- Don’t use it on **non-idempotent** operations (like “make payment”).
    
- Add **exponential backoff** to avoid retry storms.
    

---

## ⚡ 2. CIRCUIT BREAKER

### 🧠 What It Does

Prevents your service from **continuously calling** a failing downstream service.  
It “opens the circuit” — blocking calls for a while — so your app doesn’t hang or crash repeatedly.

---

### ⚙️ How It Works Internally

Circuit breaker has 3 states:

|State|Meaning|Behavior|
|---|---|---|
|**Closed**|Normal|All calls allowed, failures counted|
|**Open**|Failing|All calls blocked for a cooldown period|
|**Half-Open**|Testing|Allows few test calls to check if service recovered|

Internally, Resilience4j stores recent results (success/failure) in an **in-memory ring buffer**.  
If failure % exceeds threshold → breaker goes **Open**.  
After a timeout → **Half-Open** → allows test calls → if OK → **Closed** again.

---

### 🧾 Example

```
@CircuitBreaker(name = "paymentService", fallbackMethod = "paymentFallback")
public String makePayment() {
    System.out.println("Calling payment service...");
    return restTemplate.getForObject("http://payment-service/pay", String.class);
}

public String paymentFallback(Throwable t) {
    return "Payment service unavailable — please try later.";
}
```

### 🧰 Config

```
resilience4j.circuitbreaker:
  instances:
    paymentService:
      failureRateThreshold: 50
      waitDurationInOpenState: 10s
      slidingWindowSize: 10
```

**Flow:**  
Success calls → OK  
50%+ fail → Circuit opens → All calls blocked for 10s → After 10s → Half-Open → test calls

---

### ⚡ Key Points

- Failure data stored **in-memory**.
    
- Protects from cascading failures.
    
- Combine with fallback to return safe responses.
    

---

## 🧰 3. FALLBACK

### 🧠 What It Does

If a main operation fails (due to circuit breaker, timeout, retry failure, etc.),  
the **fallback method** gives a **default safe response** instead of crashing the system.

---

### ⚙️ How It Works Internally

- The fallback method is defined alongside the main one.
    
- When a failure occurs, Resilience4j looks up a fallback with the same arguments + an optional `Throwable` parameter.
    
- It’s invoked via **reflection** instead of throwing the error.
    

---

### 🧾 Example

```
@CircuitBreaker(name = "shippingService", fallbackMethod = "defaultShipping")
public String getShippingDetails() {
    System.out.println("Calling shipping service...");
    return restTemplate.getForObject("http://shipping-service/details", String.class);
}

public String defaultShipping(Throwable t) {
    return "Shipping details not available — please try later.";
}

```

---

### ⚡ Key Points

- Fallback should be **fast and reliable**.
    
- Avoid complex logic in fallback.
    
- Perfect for cached or static responses.
    

---

## 🧱 4. BULKHEAD

### 🧠 What It Does

Limits **how many requests can run concurrently** for a given service.  
Prevents one slow service from consuming all threads in your app.

Think of a ship with sealed compartments — if one floods, others stay dry.

---

### ⚙️ Types

#### A. Semaphore Bulkhead

- Uses a fixed number of **permits (slots)**.
    
- Each call must acquire a slot.
    
- If all slots full → request rejected immediately (throws `BulkheadFullException`).
    
- Caller thread is used directly — no new threads created.
    

#### B. ThreadPool Bulkhead

- Each service gets its own **thread pool** + optional queue.
    
- Calls are submitted as tasks to that pool.
    
- If pool full → request rejected.
    
- Useful for **blocking** operations (e.g., slow REST calls, DB I/O).
    

---

### 🧾 Example (Semaphore)

```
@Bulkhead(name = "orderService", type = Bulkhead.Type.SEMAPHORE)
public String placeOrder() {
    System.out.println("Placing order...");
    return restTemplate.getForObject("http://order-service/place", String.class);
}

```

### 🧾 Example (ThreadPool)

```
@Bulkhead(name = "fileService", type = Bulkhead.Type.THREADPOOL)
public CompletableFuture<String> uploadFile() {
    return CompletableFuture.supplyAsync(() ->
        restTemplate.postForObject("http://file-service/upload", null, String.class)
    );
}

```

### 🧰 Config

```
resilience4j.bulkhead:
  instances:
    orderService:
      maxConcurrentCalls: 5
    fileService:
      maxThreadPoolSize: 10
      queueCapacity: 20

```

---

### ⚡ Key Points

|Type|Uses Thread Pool|Behavior When Full|Best For|
|---|---|---|---|
|Semaphore|❌ No|Reject immediately|Fast methods|
|ThreadPool|✅ Yes|Queue or reject|Blocking calls|

---

## ⏱ 5. TIME LIMITER

### 🧠 What It Does

Cancels slow-running operations if they take longer than a configured duration.  
Prevents threads from getting stuck waiting forever.

---

### ⚙️ How It Works Internally

- Works with **async operations** (`CompletableFuture`, `Mono`, `Flux`).
    
- Starts a **timer** when the call begins.
    
- If the call exceeds timeout → cancels it + triggers fallback.
    
- Uses an internal scheduler to track timeouts.
    

---

### 🧾 Example

```
@TimeLimiter(name = "shippingService")
@CircuitBreaker(name = "shippingService", fallbackMethod = "fallbackShipping")
public CompletableFuture<String> getShippingDetails() {
    return CompletableFuture.supplyAsync(() ->
        restTemplate.getForObject("http://shipping-service/details", String.class)
    );
}

public String fallbackShipping(Throwable t) {
    return "Shipping service slow — please retry later.";
}

```

### 🧰 Config

```
resilience4j.timelimiter:
  instances:
    shippingService:
      timeoutDuration: 2s

```

---

### ⚡ Key Points

- Cancels long-running tasks.
    
- Only works with **async code**.
    
- Combine with Circuit Breaker + Retry for maximum protection.
    

---

## 🚦 6. RATE LIMITER

### 🧠 What It Does

Limits how many requests are allowed per time period (e.g., 5 per second).  
Prevents abuse or overload of a service.

---

### ⚙️ How It Works Internally

Implements the **token bucket** algorithm:

- Each service instance has a “bucket” with limited tokens.
    
- Every request consumes 1 token.
    
- Tokens refill after a certain time.
    
- If no tokens → new request rejected until refill.
    

---

### 🧾 Example

```
@RateLimiter(name = "userService", fallbackMethod = "rateLimitFallback")
public String getUser() {
    return restTemplate.getForObject("http://user-service/user", String.class);
}

public String rateLimitFallback(RequestNotPermitted e) {
    return "Too many requests — please try later.";
}

```

### 🧰 Config

```
resilience4j.ratelimiter:
  instances:
    userService:
      limitForPeriod: 5
      limitRefreshPeriod: 1s
      timeoutDuration: 0

```

---

### ⚡ Key Points

- Local per-instance limit.
    
- Combine with fallback for graceful messages.
    
- Useful to protect APIs or rate-limit third-party calls.
    

---

## 🔄 How All Work Together

You can layer them together like armor:

```
@Retry(name = "inventoryService")
@CircuitBreaker(name = "inventoryService", fallbackMethod = "inventoryFallback")
@Bulkhead(name = "inventoryService", type = Bulkhead.Type.SEMAPHORE)
@TimeLimiter(name = "inventoryService")
public CompletableFuture<String> getInventory() {
    return CompletableFuture.supplyAsync(() ->
        restTemplate.getForObject("http://inventory-service/items", String.class)
    );
}

```

### Execution order:

**Retry → CircuitBreaker → Bulkhead → TimeLimiter → Actual Call**

If something fails, fallback is executed.

---

## 🧾 Quick Summary Table

|Type|Purpose|Failure Handling|Uses|Example Annotation|
|---|---|---|---|---|
|**Retry**|Reattempt failed calls|Retries few times|Temporary errors|`@Retry`|
|**Circuit Breaker**|Stop calling failing service|Opens after threshold|Unstable services|`@CircuitBreaker`|
|**Fallback**|Return default response|On any failure|Graceful degradation|`fallbackMethod`|
|**Bulkhead**|Limit concurrent requests|Reject when full|Prevent overload|`@Bulkhead`|
|**TimeLimiter**|Cancel slow calls|Timeout reached|Long-running tasks|`@TimeLimiter`|
|**RateLimiter**|Limit request rate|Reject over limit|Throttle requests|`@RateLimiter`|

---

## ⚡ Best Practice Tips

- Combine **CircuitBreaker + Retry + TimeLimiter** → strong trio.
    
- Keep fallbacks simple and fast.
    
- Use **Bulkhead** to isolate heavy services.
    
- Tune parameters slowly — test under real load.
    
- Add **Micrometer metrics** → monitor breaker states, retries, etc.

---
# ==🧠 API Gateway==

---
## 🔍 1. What is API Gateway?

An **API Gateway** is the **entry point** for all client requests in a microservice architecture.  
Instead of each microservice talking directly to the client, the client communicates with **one centralized gateway**, which then routes, filters, secures, and manages those requests.

Think of it as the **front desk** of a building — every visitor passes through it before reaching any internal department (microservice).

---

## ⚙️ 2. Why Use an API Gateway?

Without it, clients would have to:

- Know addresses of all microservices
    
- Handle multiple network calls
    
- Implement authentication and rate limiting for each service
    

With a gateway, you get:

- A **single endpoint** for all APIs
    
- Centralized **security, logging, and monitoring**
    
- **Dynamic routing** using service discovery (Eureka)
    
- **Load balancing** and **fault tolerance** at the edge
    

---

## 🧩 3. Popular Gateways in Spring Boot

### **1. Spring Cloud Gateway (Reactive)**

- Built on **Spring WebFlux** (non-blocking, reactive model)
    
- Official and modern gateway
    
- Supports filters, predicates, and integration with **Eureka** and **Resilience4j**
    
- Can handle thousands of concurrent requests efficiently
    

### **2. Netflix Zuul (Legacy)**

- Older version (Servlet blocking model)
    
- Replaced by Spring Cloud Gateway in modern systems
    

---

## ⚙️ 4. Internal Working of Spring Cloud Gateway

Let's trace what happens when a client sends:

`GET http://localhost:8080/order/123`

### Step 1: **Client → Gateway**

- Client sends request to the **API Gateway** (`localhost:8080`)
    
- Gateway receives it as a **ServerWebExchange** (reactive request wrapper)
    

---

### Step 2: **Route Matching**

The Gateway checks your route configuration (from `application.yml`):

```
spring:
  cloud:
    gateway:
      routes:
        - id: order-service
          uri: lb://ORDER-SERVICE
          predicates:
            - Path=/order/**

```

- Predicate `Path=/order/**` matches `/order/123`
    
- Gateway knows it must route to `ORDER-SERVICE`
    

---

### Step 3: **Eureka Lookup**

`lb://ORDER-SERVICE` → means “load-balanced service named ORDER-SERVICE”

Gateway communicates with **Eureka Server** (`localhost:8761`) and asks:

> “Give me the active instances of ORDER-SERVICE.”

Eureka responds:

`ORDER-SERVICE → localhost:8081`

So Gateway now knows where to send your request.

---

### Step 4: **Apply Filters**

Before forwarding, Gateway applies **filters** (pre or post):

Example:

```
filters:
  - AddRequestHeader=X-Gateway, SpringCloudGateway
  - StripPrefix=1

```

- `AddRequestHeader` → Adds custom header before forwarding  
    `X-Gateway: SpringCloudGateway`
    
- `StripPrefix=1` → Removes `/order` from the path, so `/order/123` → `/123`
    

---

### Step 5: **Forward Request**

Now the Gateway forwards the request **asynchronously** (non-blocking I/O) to:

`GET http://localhost:8081/123 Header: X-Gateway: SpringCloudGateway`

This uses an internal **WebClient** (reactive HTTP client) — not servlet forwarding.

---

### Step 6: **Target Service Handles Request**

The Order Service (running on port 8081) processes the request:

```
@RestController
@RequestMapping("/order")
public class OrderController {
    @GetMapping("/{id}")
    public String getOrder(@PathVariable String id) {
        return "Order details for ID: " + id;
    }
}

```

It responds:

`200 OK Body: "Order details for ID: 123"`

---

### Step 7: **Gateway Returns Response**

- Gateway receives the response
    
- Applies **post-filters** (logging, response headers)
    
- Sends the response back to the client
    

---

### 🔄 Flow Summary Diagram

```
Client
 │
 ▼
[ API Gateway :8080 ]
 │
 ├─ Route Predicate (/order/**)
 │
 ├─ Eureka lookup (ORDER-SERVICE → localhost:8081)
 │
 ├─ Filters applied (Add Header, Strip Prefix)
 │
 ▼
[ ORDER-SERVICE :8081 ]
 │
 └─ Response → Gateway → Client

```

---

## 🧱 5. Example Configuration

### `pom.xml`

```
<dependencies>
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-gateway</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-netflix-eureka-client</artifactId>
    </dependency>
</dependencies>

```

### `application.yml`

```
server:
  port: 8080

spring:
  application:
    name: api-gateway
  cloud:
    gateway:
      routes:
        - id: order-service
          uri: lb://ORDER-SERVICE
          predicates:
            - Path=/order/**
          filters:
            - AddRequestHeader=X-Gateway, SpringCloudGateway
            - StripPrefix=1

eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka/

```

---

## 🧩 6. What is `X-Gateway` Header?

### Meaning:

`X-Gateway` is a **custom header** added by you (not default).

It’s used to **tag or trace** requests that pass through the gateway.

Example header:

`X-Gateway: SpringCloudGateway`

### Purpose:

|Use Case|Description|
|---|---|
|**Tracing & Debugging**|Identify if the request came via the gateway|
|**Analytics**|Record which gateway handled the request|
|**Multi-Gateway setup**|Differentiate between internal and external traffic|
|**Request Auditing**|Prove a request passed through the correct path|

---

### Example: Accessing in Controller

```
@GetMapping("/{id}")
public ResponseEntity<String> getOrder(
        @PathVariable String id,
        @RequestHeader(value = "X-Gateway", required = false) String header) {
    return ResponseEntity.ok("Came via: " + header);
}

```

Response:

`Came via: SpringCloudGateway`

---

## ⚡ 7. Core Features of Spring Cloud Gateway

|Feature|Description|
|---|---|
|**Routing**|Sends request to the correct service|
|**Predicates**|Match request conditions (path, method, headers, etc.)|
|**Filters**|Modify requests/responses globally or per-route|
|**Load Balancing**|Distributes requests across service instances|
|**Circuit Breakers**|Gracefully handle service failures|
|**Security Integration**|Validate JWT, OAuth2 before forwarding|
|**Rate Limiting**|Throttle excessive traffic|
|**Monitoring**|Centralized logging and metrics collection|

---

## 🧭 8. Final Request Lifecycle (Simplified)

```
Client → API Gateway
    → Route Predicate
    → Pre-Filters (Auth, Add Header)
    → Eureka Lookup
    → Forward to Target Service
    → Post-Filters (Logging)
    → Response → Client
```
---
# ==🧭Centralized Configuration Management==

## 1. Why We Need It

In a microservices architecture, each service has its own configuration (ports, DB URLs, feature flags, etc.). Managing these separately becomes chaotic.

**Spring Cloud Config** solves this by:

- Centralizing configuration in one place (e.g., Git repo)
    
- Serving configurations to all services
    
- Allowing dynamic reload of configuration **without restarting apps**
    

---

## 2. Core Components

|Component|Description|
|---|---|
|**Config Server**|Reads config from Git and serves via REST API|
|**Config Client**|Fetches and applies configuration from the server|
|**Git Repository**|Stores all configuration files (central source of truth)|

---

## 3. Basic Architecture

```
 ┌─────────────────────┐
 │  Git Repository     │
 │ (Config Files)      │
 └──────────┬──────────┘
            │
            ▼
 ┌─────────────────────┐
 │ Spring Cloud Config │
 │      Server         │
 │  (port 8888)        │
 └──────────┬──────────┘
            │
 ┌──────────┴───────────┐
 │                      │
 ▼                      ▼
┌────────────┐      ┌────────────┐
│ user-svc   │      │ order-svc  │
│ (Client)   │      │ (Client)   │
└────────────┘      └────────────┘
```

---

## 4. Config Server Setup

**Dependencies:**

```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-config-server</artifactId>
</dependency>
```

**Main Class:**

```java
@SpringBootApplication
@EnableConfigServer
public class ConfigServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(ConfigServerApplication.class, args);
    }
}
```

**application.yml:**

```yaml
server:
  port: 8888
spring:
  cloud:
    config:
      server:
        git:
          uri: https://github.com/your-org/config-repo
          clone-on-start: true
```

---

## 5. Config Client Setup

**Dependencies:**

```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-config</artifactId>
</dependency>
```

**bootstrap.yml:**

```yaml
spring:
  application:
    name: order-service
  cloud:
    config:
      uri: http://localhost:8888
```

> The client fetches configuration **before** Spring Boot’s normal `application.yml` loads.

---

## 6. File Naming Convention in Git Repo

|File|Purpose|
|---|---|
|`application.yml`|Global defaults (shared by all services)|
|`application-dev.yml`|Shared configuration for dev environment|
|`application-prod.yml`|Shared configuration for prod environment|
|`order-service.yml`|Service-specific configuration|
|`order-service-dev.yml`|Service and environment-specific configuration|

**Hierarchy:**

```
order-service-dev.yml
application-dev.yml
order-service.yml
application.yml
```

---

## 7. Spring Profiles

Profiles (`dev`, `test`, `prod`) define environments.

Activate using:

```bash
--spring.profiles.active=dev
```

or inside YAML:

```yaml
spring:
  profiles:
    active: dev
```

**Example:**

```yaml
# application-dev.yml
logging.level.root=DEBUG

# application-prod.yml
logging.level.root=INFO
```

---

## 8. Property Precedence

|Priority|Source|Example|
|---|---|---|
|1|Command-line args|`--server.port=9090`|
|2|Environment variables|`SPRING_DATASOURCE_URL`|
|3|Config Server (remote)|Git repo config|
|4|Local `application.yml`|In microservice|
|5|Defaults in code|`@Value("${x:default}")`|

Control with:

```yaml
spring:
  cloud:
    config:
      allowOverride: true
      overrideNone: false
```

---

## 9. Spring Boot Actuator

Provides runtime insight and control.

**Dependency:**

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

**Endpoints:**

|Endpoint|Description|
|---|---|
|`/actuator/health`|App health status|
|`/actuator/env`|Shows environment props|
|`/actuator/refresh`|Reloads configuration|
|`/actuator/busrefresh`|Broadcasts global refresh|

**Enable:**

```yaml
management:
  endpoints:
    web:
      exposure:
        include: "*"
```

---

## 10. Reloading Configuration

Spring doesn’t auto-refresh configs. You must trigger it manually or globally.

### A. Manual Refresh (Single Service)

```
POST /actuator/refresh
```

Reloads only one service.

### B. Global Refresh (All Services)

```
POST /actuator/busrefresh
```

Broadcasts refresh using **Spring Cloud Bus** (via RabbitMQ/Kafka).

---

## 11. Spring Cloud Bus — The Global Refresh System

**Purpose:** Notify all microservices when configuration updates.

**Dependency:**

```xml
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-bus-amqp</artifactId>
</dependency>
```

**Flow:**

```
[1] Dev updates config in Git
     ↓
[2] POST /actuator/busrefresh on Config Server
     ↓
[3] Config Server publishes event to RabbitMQ/Kafka
     ↓
[4] All microservices receive event via Cloud Bus
     ↓
[5] Each service fetches latest config
     ↓
[6] Spring updates @RefreshScope beans
     ↓
[7] New config active instantly
```

**Broker’s role:** Only passes “refresh now” messages — doesn’t store configs.

---

## 12. `@RefreshScope`

Annotate beans to refresh dynamically:

```java
@RefreshScope
@Component
public class FeatureConfig {
    @Value("${feature.newUI:false}")
    private boolean newUI;
}
```

Beans without this annotation won’t reload until app restart.

---

## 13. Full Reload Flow (End-to-End)

|Step|Action|Component|
|---|---|---|
|1|Config updated|Git repo|
|2|`/actuator/busrefresh` triggered|Config Server|
|3|Refresh event sent|RabbitMQ/Kafka|
|4|All services receive event|Cloud Bus|
|5|Each service re-fetches config|Client|
|6|Spring updates environment|Framework|
|7|Beans reloaded|@RefreshScope|

---

## 14. Local vs Production Setup

|Environment|Config Server URI|Description|
|---|---|---|
|Local|`http://localhost:8888`|Config Server on your PC|
|Staging|`http://staging-config.company.net`|Shared test server|
|Production|`https://config.company.com`|Enterprise config server|

---

## 15. Key Takeaways

- Profiles (`dev`, `prod`) decide environment.
    
- Config Server centralizes everything.
    
- Property precedence decides override order.
    
- Actuator exposes control endpoints.
    
- Spring Cloud Bus uses a broker for global refresh.
    
- `@RefreshScope` enables dynamic bean reload.
    

---

## 16. Visual Recap — Global Refresh

```
Developer → Git Repo
   │
   ▼
Config Server (pulls latest config)
   │
POST /actuator/busrefresh
   │
   ▼
RabbitMQ/Kafka (message broadcast)
   │
   ▼
All microservices receive event
   │
   ▼
Each calls Config Server → fetch latest config
   │
   ▼
@RefreshScope beans recreated → new config live
```

---
