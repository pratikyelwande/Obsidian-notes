## ==🧱 Types of Programming Paradigms==
### 🔹 A. **Procedural Programming**

|Feature|Description|
|---|---|
|Structure|Step-by-step instructions using functions/procedures.|
|Data Handling|Separate from functions.|
|Use Case|Simple to moderate programs.|

**Languages**: C, Pascal, Fortran  
**Example**:
`int add(int a, int b) {   return a + b; }`

---
### 🔹 B. **Object-Oriented Programming (OOP)**

|Feature|Description|
|---|---|
|Structure|Uses **objects** that contain data and methods.|
|Key Concepts|Encapsulation, Inheritance, Polymorphism, Abstraction|
|Use Case|Large, modular, reusable codebases.|

**Languages**: Java, Python, C++, C#  
**Example**:

`class Car:     def drive(self):         print("Driving")`

---
### 🔹 C. **Functional Programming**

|Feature|Description|
|---|---|
|Structure|Uses pure functions, immutability, no side effects.|
|Concepts|First-class functions, recursion, function composition.|
|Use Case|Data processing, concurrency, transformations.|

**Languages**: Haskell, Lisp, Elixir, JavaScript (partial)  
**Example**:

`const square = x => x * x;`

---
### 🔹 D. **Other Paradigms**

|Type|Description|Example Languages|
|---|---|---|
|**Declarative**|Describes _what_ to do, not _how_.|SQL, HTML|
|**Logic-Based**|Based on rules and logic.|Prolog|
|**Event-Driven**|Reacts to events.|JavaScript, VB.NET|

---
## ==🔁Static vs Dynamic Typing==

| Feature              | **Static Typing**          | **Dynamic Typing**           |
| -------------------- | -------------------------- | ---------------------------- |
| Type Checking        | At **compile-time**        | At **runtime**               |
| Variable Declaration | Types declared or inferred | No type declaration          |
| Flexibility          | Less flexible              | Very flexible                |
| Error Detection      | Early (before execution)   | Late (during execution)      |
| Performance          | Generally faster           | Slower due to runtime checks |
| Example Languages    | C, C++, Java, Rust         | Python, JavaScript, Ruby     |
|                      |                            |                              |

---
### 🔍 Examples

**Static (Java):**

`int num = 10;      // Must be an integer`

**Dynamic (Python):**

`num = 10 num = "hello"      // Allowed`

# ==🧠 Memory Management==
---

**Memory Management** is the process of:

- Allocating memory to programs and variables.
    
- Using memory efficiently.
    
- Releasing memory when it’s no longer needed.

It is handled either:

- **Manually** by the programmer (e.g., in C/C++).
    
- **Automatically** by the runtime or language (e.g., Python, Java).

---
## 🧱 Types of Memory in a Program

|Memory Type|Description|
|---|---|
|**Stack**|Stores local variables and function call info. Fast and auto-managed.|
|**Heap**|Stores dynamically allocated memory. Slower, but flexible.|
|**Static/Global**|Stores global/static variables that persist throughout the program.|
|**Code (Text)**|Stores compiled program instructions.|
|**Read-Only Data**|Stores constants, string literals.|

---
## ⚙️ Memory Management Techniques

### 1. **Manual Memory Management**

- Programmer manually allocates and deallocates memory.
    
- Found in: **C, C++**

`int* ptr = malloc(sizeof(int));  // allocation *ptr = 42; free(ptr);                       // deallocation`

#### Common Problems:

- Memory leak
    
- Dangling pointer
    
- Double free

---
### 2. **Automatic Memory Management (Garbage Collection)**

- The language/runtime tracks memory and frees unused memory automatically.
    
- Found in: **Python, Java, JavaScript**

#### ✅ Key Point:

> **Garbage collector cleans objects when reference variable is no longer pointing to the object.**

`a = [1, 2, 3] a = None   # Now the list object is eligible for garbage collection`
#### Methods used:

- **Reference Counting**: Objects are deleted when reference count becomes zero.
    
- **Tracing (Mark & Sweep)**: Finds all reachable objects and deletes the rest

# ==JAVA Architecture-==
![[Java Intro.png]]

==**public static void main(String[] args)` is the entry point of a program.**==

- **`public` → accessible to JVM from anywhere**
    
- **`static` → JVM can call it without creating an object**
    
- **`void` → does not return any value**
    
- **`main` → the starting point recognized by JVM**
    
- **`String[] args` → used to take command-line arguments.”**

### ==What is package ?==

a package is a way of organizing related classes and interfaces into a single namespace. It works like a folder in a file system and helps to avoid name conflicts, makes code modular, and easier to maintain.


|Feature|**Type Conversion** (Implicit)|**Type Casting** (Explicit)|
|---|---|---|
|**Definition**|Automatic conversion done by compiler|Manual conversion done by programmer|
|**Other Name**|Widening / Implicit Casting / Type Promotion|Narrowing / Explicit Casting|
|**Syntax**|Happens automatically|Needs `(type)` operator|
|**Direction**|Smaller → Larger data type|Larger → Smaller data type|
|**Data Loss**|No (safe)|Possible (fractional/truncation)|
|**Example**|`int x = 10; double y = x;`|`double d = 9.8; int i = (int) d; // 9`|
![[First_Java_Program_Notes.pdf]]

## ==**Variable Shadowing in Java**==
Shadowing happens when a **local variable** (like in a method or block) has the **same name** as an **instance variable (or class variable)**.  
👉 The local variable **“shadows”** (hides) the instance variable inside that scope.

---
### ✅ Example:

`class ShadowExample {     int x = 10;  // instance variable      void display() {         int x = 20;  // local variable shadows instance variable         System.out.println("Local x = " + x);       // prints 20         System.out.println("Instance x = " + this.x); // prints 10     }      public static void main(String[] args) {         ShadowExample obj = new ShadowExample();         obj.display();     } }`

### ✅ Output:

`Local x = 20 Instance x = 10`

## ==**What is Varargs in Java?**==

- **Varargs** allows you to pass a **variable number of arguments** to a method.
    
- Introduced in **Java 5** using **ellipsis `...`**.
    
- Instead of defining multiple overloaded methods, we can use one method with varargs.
    

---

### ✅ Syntax:

`returnType methodName(type... variableName) {     // code }`

---

### ✅ Example:

`class VarArgsExample {     static void printNumbers(int... numbers) {         for (int n : numbers) {             System.out.print(n + " ");         }         System.out.println();     }      public static void main(String[] args) {         printNumbers(1);              // one argument         printNumbers(1, 2, 3, 4, 5); // multiple arguments         printNumbers();              // even zero arguments     } }`

### ✅ Output:

`1  1 2 3 4 5` 

---

### ✅ Rules of Varargs:

1. Only **one varargs parameter** per method.
    
2. It must be the **last parameter** in the method.
    
    `void example(String msg, int... nums) { }`
    
3. Inside the method, varargs is treated as an **array**.

## ==Access Modifiers==

They control **who can access them** same class, same package, subclass, or anywhere.

![[{E0FC2687-63D9-4BF4-AF4C-D03755011CD7}.png]]

## ==1. What is a Method?==

A **method** (sometimes called a function in other languages) is a **block of code** that performs a specific task, runs only when called, and may return a value.

**Syntax:**

`modifier returnType methodName(parameters) {     // body     return value; // optional }`

---

## 🔹 2. Parts of a Method

1. **Access Modifier** → `public`, `private`, `protected`, or default.
    
2. **Return Type** → `void` (no return) or a type (`int`, `String`, etc.).
    
3. **Method Name** → must follow Java naming rules.
    
4. **Parameters (Arguments)** → values passed into the method.
    
5. **Method Body** → the actual code.
---
## 🔹 3. Arguments & Parameters

- **Parameter** = variable defined in method declaration.
    
- **Argument** = actual value passed when calling the method.

`class Example {     // parameter: int a, int b     static int add(int a, int b) {         return a + b;     }      public static void main(String[] args) {         // arguments: 5, 7         System.out.println(add(5, 7)); // 12     } }`

---

## 🔹 4. Types of Methods

1. **Predefined Methods** (from Java libraries)
    
    - Example: `Math.sqrt(25)`, `System.out.println()`.
        
2. **User-defined Methods**
    
    - Example: `int add(int a, int b) { return a + b; }`.
        

---
## 🔹 5. Method Overloading

- Same method name, different parameter list.
    
- Compile-time polymorphism.
    

`class Overload {     int add(int a, int b) { return a + b; }     double add(double a, double b) { return a + b; } }`

---
## 🔹 6. Method Parameters Types

1. **Pass by Value (default in Java)**
    
    - Copies of values are passed.
        
    - Original values remain unchanged.
        
2. **Varargs (Variable-length Arguments)**
    
    `void display(String... names) {     for (String n : names) {         System.out.println(n);     } }`
    

---

## 🔹 7. Static vs Instance Methods

- **Static Method**: belongs to the class, can be called without creating an object.
    
    `static void greet() { System.out.println("Hello"); }`
    
- **Instance Method**: belongs to an object.
    
    `void show() { System.out.println("Hi"); }`   

---
## 🔹 8. Return Statement
- `void` → no return.
    
- Non-void → must return a value of the declared type.

`int square(int n) {     return n * n; }`

---
## 🔹 9. Recursion
- A method that calls itself.
`int factorial(int n) {     if (n == 1) return 1;     return n * factorial(n - 1); }`

---
## 🔹 10. Access Modifiers with Methods

- **public** → accessible everywhere.
    
- **private** → accessible only within the same class.
    
- **protected** → accessible in same package + subclasses.
    
- **default** → package-private (same package only).


## 🔹 1. What is ==Inheritance==?

- Inheritance in Java is the process where one class (child) **acquires properties and methods** of another class (parent).
    
- It enables **code reusability** and supports **runtime polymorphism** (method overriding).
    

---

## 🔹 2. Syntax

`class Parent {    // fields and methods }  class Child extends Parent {    // child-specific fields and methods }`

---

## 🔹 3. Types of Inheritance in Java

✔ Supported:

1. **Single Inheritance** – One class extends another.
    
2. **Multilevel Inheritance** – Child → Parent → Grandparent chain.
    
3. **Hierarchical Inheritance** – Multiple classes extend the same parent.
    

❌ Not Supported:

- **Multiple Inheritance (via classes)** → avoided to solve **Diamond Problem**.  
    ✅ Achieved using **interfaces**.
    

---

## 🔹 4. Example (Parent & Child in Two Files)

### File: `Parent.java`

`public class Parent {     String familyName = "Smith";      public void displayFamilyName() {         System.out.println("Family Name: " + familyName);     } }`

### File: `Child.java`

`public class Child extends Parent {     String childName = "John";      public void displayChildName() {         System.out.println("Child Name: " + childName);     }      public static void main(String[] args) {         Child obj = new Child();         obj.displayFamilyName();   // Parent method         obj.displayChildName();    // Child method     } }`

✅ Output:

`Family Name: Smith Child Name: John`

---

## 🔹 5. Why `extends` when we can just use objects?

- Without `extends`: Access parent class methods using **composition** (`Parent p = new Parent();`).
    
- With `extends`:
    
    - Automatic availability of parent members.
        
    - Supports **method overriding** (polymorphism).
        
    - Enables **super** keyword.
        
    - Models **Is-A relationship** (`Dog is an Animal`).
        

👉 **Rule of Thumb**: Use `extends` when the relationship is naturally **Is-A**, otherwise use composition (`Has-A`).

---

## 🔹 6. Constructors in Inheritance

- **Constructors are not inherited**, but child always calls parent constructor (implicitly or explicitly).
    
- If parent has only parameterized constructor → child must call it using `super(args)`.
    

### Example

`class Parent {     Parent(String msg) {         System.out.println("Parent: " + msg);     } }  class Child extends Parent {     Child(String msg) {         super(msg);  // must be first line         System.out.println("Child constructor");     } }  public class Main {     public static void main(String[] args) {         Child c = new Child("Hello");     } }`

✅ Output:

`Parent: Hello Child constructor`

---

## 🔹 7. ==`super` Keyword==

Three main uses:

1. **Access parent variable** → `super.varName`
    
2. **Access parent method** → `super.methodName()`
    
3. **Call parent constructor** → `super(args)`
    

⚠️ `super(...)` must be the **first line** in the child constructor.

---

## 🔹 8. Method Overriding

- When child provides new implementation of a parent method.
    
- Achieves **runtime polymorphism**.
    

`class Parent {     void greet() { System.out.println("Hello from Parent"); } }  class Child extends Parent {     @Override     void greet() { System.out.println("Hello from Child"); } }  public class Main {     public static void main(String[] args) {         Parent p = new Child(); // polymorphism         p.greet(); // Hello from Child     } }`

---

## 🔹 9. Access Modifiers in Inheritance

- **public** → accessible everywhere.
    
- **protected** → accessible in same package + subclasses.
    
- **default** → package-level only.
    
- **private** → not accessible in child class.
    

---

## 🔹 10. `final` with Inheritance

- `final class` → cannot be inherited.
    
- `final method` → cannot be overridden.
    
- `final variable` → cannot be reassigned.
    

---

## 🔹 11. Object Class

- Every class in Java implicitly inherits from `Object`.
    
- Common methods: `toString()`, `equals()`, `hashCode()`.
    

---

# 🔑 Interview Q&A

### Q1. Why doesn’t Java support multiple inheritance with classes?

👉 To avoid **Diamond Problem** (ambiguity when two parent classes have same method).  
Instead, Java uses **interfaces** for multiple inheritance.

---

### Q2. Difference between **method overloading** and **method overriding**?

- **Overloading** → Same method name, different parameter list (Compile-time).
    
- **Overriding** → Same method name/signature, child modifies parent method (Runtime).
    

---

### Q3. What happens if parent has only parameterized constructor?

👉 Child must explicitly call it using `super(args)`. Otherwise, compilation error.

---

### Q4. Can a constructor be inherited?

👉 No, constructors are **never inherited**, but are **always executed** in inheritance chain.

---

### Q5. What is the difference between `Has-A` and `Is-A` relationship?

- **Has-A** → Composition (e.g., Car has Engine).
    
- **Is-A** → Inheritance (e.g., Car is a Vehicle).
    

---

# ✅ Summary

- Use **inheritance** (`extends`) when you need **Is-A** relationship.
    
- Use **composition** (object reference) when it’s **Has-A**.
    
- Always remember **super**, **method overriding**, and **constructor chaining** – favorite interview areas.
    
- **Multiple inheritance** not supported via classes → use interfaces.
    
- Inheritance enables **polymorphism**, which is a major OOP feature.

## 1. What is ==Polymorphism==?

👉 **Polymorphism** = _Poly (many) + morphism (forms)_  
It allows the **same thing** (method/operation) to behave differently based on the context.

### Types in Java:

1. **Compile-time (Static) Polymorphism** → Method Overloading
    
2. **Runtime (Dynamic) Polymorphism** → Method Overriding

---

## 🔹 2. Compile-time Polymorphism (Method Overloading)

- Same method name, **different parameter list** (number/type/order).
    
- Decided by **compiler** which method to call.
    

`class Calculator {     int add(int a, int b) {         return a + b;     }      double add(double a, double b) {         return a + b;     } }  public class Main {     public static void main(String[] args) {         Calculator c = new Calculator();         System.out.println(c.add(2, 3));       // calls int version         System.out.println(c.add(2.5, 3.5));   // calls double version     } }`

✅ Output:

`5 6.0`

---
## 🔹 3. Runtime Polymorphism (Method Overriding)

- Same method name, **same signature** in parent and child.
    
- Which method is called is decided **at runtime** based on object type.

`class Animal {     void sound() {         System.out.println("Animal makes a sound");     } }  class Dog extends Animal {     @Override     void sound() {         System.out.println("Dog barks");     } }  class Cat extends Animal {     @Override     void sound() {         System.out.println("Cat meows");     } }  public class Main {     public static void main(String[] args) {         Animal a1 = new Dog();  // runtime decides → Dog         Animal a2 = new Cat();  // runtime decides → Cat          a1.sound(); // Dog barks         a2.sound(); // Cat meows     } }`

✅ Output:

`Dog barks Cat meows`

---
## 🔹 4. `super` with Polymorphism

When overriding, you can still call parent’s version with `super.method()`.

`class Parent {     void greet() {         System.out.println("Hello from Parent");     } }  class Child extends Parent {     @Override     void greet() {         super.greet(); // call parent         System.out.println("Hello from Child");     } }  public class Main {     public static void main(String[] args) {         Child c = new Child();         c.greet();     } }`

✅ Output:

`Hello from Parent Hello from Child`

---
## 🔹 5. Polymorphism with Interfaces

Interfaces are also used for polymorphism (different classes implement the same interface).

`interface Shape {     void draw(); }  class Circle implements Shape {     public void draw() { System.out.println("Drawing Circle"); } }  class Square implements Shape {     public void draw() { System.out.println("Drawing Square"); } }  public class Main {     public static void main(String[] args) {         Shape s1 = new Circle();         Shape s2 = new Square();          s1.draw(); // Drawing Circle         s2.draw(); // Drawing Square     } }`

---
## 🔹 6. Polymorphism and Casting

- **Upcasting** → Parent reference, child object. (Allowed, supports runtime polymorphism)
    
- **Downcasting** → Converting parent reference back to child (needs explicit cast).
    

`Animal a = new Dog();   // Upcasting Dog d = (Dog) a;        // Downcasting`

---
## 🔹 7. Important Rules

- Overloading → **Compile-time**, different method signatures.
    
- Overriding → **Runtime**, same method signature.
    
- Constructors **cannot** be overridden, but can be overloaded.
    
- Static methods → **can be overloaded but not overridden** (they are hidden).
    
- Final methods → cannot be overridden.
    
---
# 🔑 Interview Q&A

### Q1. Difference between overloading and overriding?

- **Overloading** → Compile-time, different parameter list.
    
- **Overriding** → Runtime, same signature in parent and child.

---
### Q2. Can static methods be overridden?

👉 No. They can only be **hidden**. (Child static method with same signature hides parent’s one.)

---
### Q3. What is runtime polymorphism in Java?

👉 Runtime polymorphism is **method overriding**, where the method call is resolved by JVM at runtime based on the object’s type.

---
### Q4. Why is overriding called runtime polymorphism?

👉 Because the decision of which method to call is made by the **JVM at runtime**, not at compile time.

---
### Q5. Can private methods be overridden?

👉 No. Private methods are not inherited, so they cannot be overridden.

---
# ✅ Summary

- **Polymorphism** → One name, many forms.
    
- **Overloading (compile-time)** → Same name, different params.
    
- **Overriding (runtime)** → Same name, same params, different class.
    
- Enables **flexibility + reusability** in code.
    
- Used heavily with **inheritance** and **interfaces**.


# **Abstract Class vs Interface (Easy Table)**

|Feature|Abstract Class|Interface|
|---|---|---|
|**Keyword**|`abstract class`|`interface`|
|**Methods**|Can have **abstract + normal methods**|Only **abstract methods** (till Java 7), plus **default & static** (Java 8+)|
|**Variables**|Can have normal variables|All are **public static final** (constants)|
|**Constructor**|✔️ Can have constructor|❌ Cannot have constructor|
|**Inheritance**|A class can **extend only one** abstract class|A class can **implement many** interfaces|
|**Access Modifiers (methods)**|Can be `public`, `protected`, `default`|Always `public`|
|**Use Case**|When classes are **closely related** and share code|When classes are **unrelated** but need same behavior|
|**Object Creation**|❌ Cannot create object directly|❌ Cannot create object directly|

# ==Multithreading== 
> **_Process_**

A process is an instance of a program that is being executed. When a program runs, the operating system creates a process to manage its execution.

When we open Microsoft Word, it becomes a process in the operating system.

> **_Thread_**

==A thread is the smallest unit of execution within a process.== A process can have multiple threads, which share the same resources but can run independently.

==A web browser like Google Chrome might use multiple threads for different tabs, with each tab running as a separate thread.==

> **_Multitasking_**

Multitasking allows an operating system to run multiple processes simultaneously. On single-core CPUs, this is done through time-sharing, rapidly switching between tasks. On multi-core CPUs, true parallel execution occurs, with tasks distributed across cores. The OS scheduler balances the load, ensuring efficient and responsive system performance.

_Example: We are browsing the internet while listening to music and downloading a file._

Multitasking utilizes the capabilities of a CPU and its cores. When an operating system performs multitasking, it can assign different tasks to different cores. This is more efficient than assigning all tasks to a single core.

> **==_Multithreading_==**

Multithreading refers to the ability to ==execute multiple threads within a single process concurrently.==

A web browser can use multithreading by having separate threads for rendering the page, running JavaScript, and managing user inputs. This makes the browser more responsive and efficient.

Multithreading enhances the efficiency of multitasking by breaking down individual tasks into smaller sub-tasks or threads. These threads can be processed simultaneously, making better use of the CPU’s capabilities.

**In a single-core system:**

Both threads and processes are managed by the OS scheduler through time slicing and context switching to create the illusion of simultaneous execution.

**In a multi-core system:**

Both threads and processes can run in true parallel on different cores, with the OS scheduler distributing tasks across the cores to optimize performance.

> **_Time Slicing_**

- **Definition:** Time slicing divides CPU time into small intervals called time slices or quanta.
- **Function:** The OS scheduler allocates these time slices to different processes and threads, ensuring each gets a fair share of CPU time.
- **Purpose:** This prevents any single process or thread from monopolizing the CPU, improving responsiveness and enabling concurrent execution.

> **_Context Switching_**

- **Definition:** Context switching is the process of saving the state of a currently running process or thread and loading the state of the next one to be executed.
- **Function:** When a process or thread’s time slice expires, the OS scheduler performs a context switch to move the CPU’s focus to another process or thread.
- **Purpose:** This allows multiple processes and threads to share the CPU, giving the appearance of simultaneous execution on a single-core CPU or improving parallelism on multi-core CPUs.

_Multitasking can be achieved through multithreading where each task is divided into threads that are managed concurrently._

_While multitasking typically refers to the running of multiple applications, multithreading is more granular, dealing with multiple threads within the same application or process._

## Multithreading in Java

Java provides robust support for multithreading, allowing developers to create applications that can perform multiple tasks simultaneously, improving performance and responsiveness.

In Java, multithreading is the concurrent execution of two or more threads to maximize the utilization of the CPU. Java’s multithreading capabilities are part of the java.lang package, making it easy to implement concurrent execution.

In a single-core environment, Java’s multithreading is managed by the JVM and the OS, which switch between threads to give the illusion of concurrency.

The threads share the single core, and time-slicing is used to manage thread execution.

In a multi-core environment, Java’s multithreading can take full advantage of the available cores.

The JVM can distribute threads across multiple cores, allowing true parallel execution of threads.

A thread is a lightweight process, the smallest unit of processing. Java supports multithreading through its java.lang.Thread class and the java.lang.Runnable interface.

When a Java program starts, one thread begins running immediately, which is called the main thread. This thread is responsible for executing the main method of a program.

public class Test {  
    public static void main(String[] args) {  
        System.out.println("Hello world !");  
    }  
}

To create a new thread in Java, you can either extend the Thread class or implement the Runnable interface.

## ==Method 1: extend the Thread class==

1. A new class World is created that extends Thread.
2. The run method is overridden to define the code that constitutes the new thread.
3. start method is called to initiate the new thread.

public class Test {  
    public static void main(String[] args) {  
        World world = new World();  
        world.start();  
        for (; ; ) {  
            System.out.println("Hello");  
        }  
    }  
}

public class World extends Thread {  
    @Override  
    public void run() {  
        for (; ; ) {  
            System.out.println("World");  
        }  
    }  
}

## ==Method 2: Implement Runnable interface==

1. A new class World is created that implements Runnable.
2. The run method is overridden to define the code that constitutes the new thread.
3. A Thread object is created by passing an instance of World.
4. start method is called on the Thread object to initiate the new thread.

public class Test {  
    public static void main(String[] args) {  
        World world = new World();  
        Thread thread = new Thread(world);  
        thread.start();  
        for (; ; ) {  
            System.out.println("Hello");  
        }  
    }  
}

public class World implements Runnable {  
    @Override  
    public void run() {  
        for (; ; ) {  
            System.out.println("World");  
        }  
    }  
}

## ==**Thread Lifecycle**==

The lifecycle of a thread in Java consists of several states, which a thread can move through during its execution.

- **New:** A thread is in this state when it is created but not yet started.
- **Runnable:** After the start method is called, the thread becomes runnable. It’s ready to run and is waiting for CPU time.
- **Running:** The thread is in this state when it is executing.
- **Blocked/Waiting:** A thread is in this state when it is waiting for a resource or for another thread to perform an action.
- **Terminated:** A thread is in this state when it has finished executing.

```
public class MyThread extends Thread{  
    @Override  
    public void run() {  
        System.out.println("RUNNING"); // RUNNING  
        try {  
            Thread.sleep(2000);  
        } catch (InterruptedException e) {  
            System.out.println(e);  
        }  
    }  
```
  
```
    public static void main(String[] args) throws InterruptedException {  
        MyThread t1 = new MyThread();  
        System.out.println(t1.getState()); // NEW  
        t1.start();  
        System.out.println(t1.getState()); // RUNNABLE  
        Thread.sleep(100);  
        System.out.println(t1.getState()); // TIMED_WAITING  
        t1.join();  
        System.out.println(t1.getState()); // TERMINATED  
    }  
}
```

## ==Thread methods==

1. **start( ):** Begins the execution of the thread. The Java Virtual Machine (JVM) calls the `run()` method of the thread.
2. **run**( ): The entry point for the thread. When the thread is started, the `run()` method is invoked. If the thread was created using a class that implements `Runnable`, the `run()` method will execute the `run()` method of that `Runnable` object.
3. **sleep(long millis):** Causes the currently executing thread to sleep (temporarily cease execution) for the specified number of milliseconds.
4. **join( ):** ==Waits for this thread to die==. When one thread calls the `join()` method of another thread, it pauses the execution of the current thread until the thread being joined has completed its execution.
5. **setPriority(int newPriority):** Changes the priority of the thread. The priority is a value between `Thread.MIN_PRIORITY` (1) and `Thread.MAX_PRIORITY` (10).

```
public class MyThread extends Thread {  
    public MyThread(String name) {  
        super(name);  
    }  
  
    @Override  
    public void run() {  
        System.out.println("Thread is Running...");  
        for (int i = 1; i <= 5; i++) {  
            for (int j = 0; j < 5; j++) {  
                System.out.println(Thread.currentThread().getName() + " - Priority: " + Thread.currentThread().getPriority() + " - count: " + i);  
                try {  
                    Thread.sleep(1000);  
                } catch (InterruptedException e) {  
                    e.printStackTrace();  
  
                }  
            }  
        }  
    }  
```
  
 
    public static void main(String[] args) throws InterruptedException {  
  
        MyThread l = new MyThread("Low Priority Thread");  
        MyThread m = new MyThread("Medium Priority Thread");  
        MyThread n = new MyThread("High Priority Thread");  
        l.setPriority(Thread.MIN_PRIORITY);  
        m.setPriority(Thread.NORM_PRIORITY);  
        n.setPriority(Thread.MAX_PRIORITY);  
        l.start();  
        m.start();  
        n.start();  
  
    }  
}

**6. ==interrupt==():** Interrupts the thread. If the thread is blocked in a call to `wait()`, `sleep()`, or `join()`, it will throw an `InterruptedException`.

7. **==yield==():** `Thread.yield()` is a static method that suggests the current thread temporarily pause its execution to allow other threads of the same or higher priority to execute. It’s important to note that `yield()` is just a hint to the thread scheduler, and the actual behavior may vary depending on the JVM and OS.

public class MyThread extends Thread {  
    @Override  
    public void run() {  
        for (int i = 0; i < 5; i++) {  
            System.out.println(Thread.currentThread().getName() + " is running...");  
            Thread.yield();  
        }  
    }  
  
    public static void main(String[] args) {  
        MyThread t1 = new MyThread();   
        MyThread t2 = new MyThread();  
        t1.start();  
        t2.start();  
    }  
}

**8. ==Thread==.==setDaemon==(boolean)**: Marks the thread as either a daemon thread or a user thread. When the JVM exits, all daemon threads are terminated.

public class MyThread extends Thread {  
    @Override  
    public void run() {  
        while (true) {  
            System.out.println("Hello world! ");  
        }  
    }  
  
    public static void main(String[] args) {  
        MyThread myThread = new MyThread();  
        myThread.setDaemon(true); // myThread is daemon thread ( like Garbage collector ) now  
        MyThread t1 = new MyThread();  
        t1.start(); // t1 is user thread  
        myThread.start();  
        System.out.println("Main Done");  
    }  
}

## ==Synchronisation==

Let’s see an example where two threads are incrementing same couter.

class Counter {  
    private int count = 0; // shared resource  
  
    public void increment() {  
        count++;  
    }  
  
    public int getCount() {  
        return count;  
    }  
}  
  
public class MyThread extends Thread {  
    private Counter counter;  
  
    public MyThread(Counter counter) {  
        this.counter = counter;  
    }  
  
    @Override  
    public void run() {  
        for (int i = 0; i < 1000; i++) {  
            counter.increment();  
        }  
    }  
  
    public static void main(String[] args) {  
        Counter counter = new Counter();  
        MyThread t1 = new MyThread(counter);  
        MyThread t2 = new MyThread(counter);  
        t1.start();  
        t2.start();  
        try {  
            t1.join();  
            t2.join();  
        }catch (Exception e){  
  
        }  
        System.out.println(counter.getCount()); // Expected: 2000, Actual will be random <= 2000  
    }  
}

The output of the code is not 2000 because the increment method in the Counter class is not synchronized. This results in a race condition when both threads try to increment the count variable concurrently.

Without synchronization, one thread might read the value of `count` before the other thread has finished writing its incremented value. This can lead to both threads reading the same value, incrementing it, and writing it back, effectively losing one of the increments.

We can fix this by using `synchronized` keyword

class Counter {  
    private int count = 0; // shared resource  
  
    public synchronized void increment() {  
        count++;  
    }  
  
    public int getCount() {  
        return count;  
    }  
}

By synchronizing the `increment` method, you ensure that only one thread can execute this method at a time, which prevents the race condition. With this change, the output will consistently be 2000.

## ==Locks==

The `synchronized` keyword in Java provides basic thread-safety but has limitations: it locks the entire method or block, leading to potential performance issues. It lacks a try-lock mechanism, causing threads to block indefinitely, increasing the risk of deadlocks. Additionally, `synchronized` doesn't support multiple condition variables, offering only a single monitor per object with basic wait/notify mechanisms. In contrast, explicit locks (`Lock` interface) offer finer-grained control, try-lock capabilities to avoid blocking, and more sophisticated thread coordination through multiple condition variables, making them more flexible and powerful for complex concurrency scenarios.

import java.util.concurrent.TimeUnit;  
import java.util.concurrent.locks.Lock;  
import java.util.concurrent.locks.ReentrantLock;  
  
public class BankAccount {  
    private int balance = 100;  
    private final Lock lock = new ReentrantLock();  
  
    public void withdraw(int amount) {  
        System.out.println(Thread.currentThread().getName() + " attempting to withdraw " + amount);  
        try {  
            if (lock.tryLock(1000, TimeUnit.MILLISECONDS)) {  
                if (balance >= amount) {  
                    try {  
                        System.out.println(Thread.currentThread().getName() + " proceeding with withdrawal");  
                        Thread.sleep(3000); // Simulate time taken to process the withdrawal  
                        balance -= amount;  
                        System.out.println(Thread.currentThread().getName() + " completed withdrawal. Remaining balance: " + balance);  
                    } catch (Exception e) {  
                        Thread.currentThread().interrupt();  
                    } finally {  
                        lock.unlock();  
                    }  
                } else {  
                    System.out.println(Thread.currentThread().getName() + " insufficient balance");  
                }  
            } else {  
                System.out.println(Thread.currentThread().getName() + " could not acquire the lock, will try later");  
            }  
        } catch (Exception e) {  
            Thread.currentThread().interrupt();  
        }  
    }  
}

public class Main {  
    public static void main(String[] args) {  
        BankAccount sbi = new BankAccount();  
        Runnable task = new Runnable() {  
            @Override  
            public void run() {  
                sbi.withdraw(50);  
            }  
        };  
        Thread t1 = new Thread(task, "Thread 1");  
        Thread t2 = new Thread(task, "Thread 2");  
        t1.start();  
        t2.start();  
    }  
}

## ==Reentrant Lock==

A Reentrant Lock in Java is a type of lock that allows a thread to acquire the same lock multiple times without causing a deadlock. If a thread already holds the lock, it can re-enter the lock without being blocked. This is useful when a thread needs to repeatedly enter synchronized blocks or methods within the same execution flow. The ReentrantLock class from the `java.util.concurrent.locks` package provides this functionality, offering more flexibility than the `synchronized` keyword, including try-locking, timed locking, and multiple condition variables for advanced thread coordination.

public class ReentrantExample {  
    private final Lock lock = new ReentrantLock();  
  
    public void outerMethod() {  
        lock.lock();  
        try {  
            System.out.println("Outer method");  
            innerMethod();  
        } finally {  
            lock.unlock();  
        }  
    }  
  
    public void innerMethod() {  
        lock.lock();  
        try {  
            System.out.println("Inner method");  
        } finally {  
            lock.unlock();  
        }  
    }  
  
    public static void main(String[] args) {  
        ReentrantExample example = new ReentrantExample();  
        example.outerMethod();  
    }  
}

## ==Methods of ReentrantLock==

`lock()`

- Acquires the lock, blocking the current thread until the lock is available. It would block the thread until the lock becomes available, potentially leading to situations where a thread waits indefinitely.
- If the lock is already held by another thread, the current thread will wait until it can acquire the lock.

`tryLock()`

- Tries to acquire the lock without waiting. Returns `true` if the lock was acquired, `false` otherwise.
- This is non-blocking, meaning the thread will not wait if the lock is not available.

`tryLock(long timeout, TimeUnit unit)`

- Attempts to acquire the lock, but with a timeout. If the lock is not available, the thread waits for the specified time before giving up. It is used when you want to attempt to acquire the lock without waiting indefinitely. It allows the thread to proceed with other work if the lock isn't available within the specified time. This approach is useful to avoid deadlock scenarios and when you don't want a thread to block forever waiting for a lock.
- Returns `true` if the lock was acquired within the timeout, `false` otherwise.

`unlock()`

- Releases the lock held by the current thread.
- Must be called in a `finally` block to ensure that the lock is always released even if an exception occurs.

`lockInterruptibly()`

- Acquires the lock unless the current thread is interrupted. This is useful when you want to handle interruptions while acquiring a lock.

## ==Read Write Lock==

A Read-Write Lock is a concurrency control mechanism that allows multiple threads to read shared data simultaneously while restricting write access to a single thread at a time. This lock type, provided by the `ReentrantReadWriteLock` class in Java, optimizes performance in scenarios with frequent read operations and infrequent writes. Multiple readers can acquire the read lock without blocking each other, but when a thread needs to write, it must acquire the write lock, ensuring exclusive access. This prevents data inconsistency while improving read efficiency compared to traditional locks, which block all access during write operations.

import java.util.concurrent.locks.Lock;  
import java.util.concurrent.locks.ReadWriteLock;  
import java.util.concurrent.locks.ReentrantReadWriteLock;  
  
public class ReadWriteCounter {  
    private int count = 0;  
    private final ReadWriteLock lock = new ReentrantReadWriteLock();  
    private final Lock readLock = lock.readLock();  
    private final Lock writeLock = lock.writeLock();  
  
    public void increment() {  
        writeLock.lock();  
        try {  
            count++;  
            Thread.sleep(50);  
        } catch (InterruptedException e) {  
            throw new RuntimeException(e);  
        } finally {  
            writeLock.unlock();  
        }  
    }  
  
    public int getCount() {  
        readLock.lock();  
        try {  
            return count;  
        } finally {  
            readLock.unlock();  
        }  
    }  
  
    public static void main(String[] args) throws InterruptedException {  
        ReadWriteCounter counter = new ReadWriteCounter();  
  
        Runnable readTask = new Runnable() {  
            @Override  
            public void run() {  
                for (int i = 0; i < 10; i++) {  
                    System.out.println(Thread.currentThread().getName() + " read: " + counter.getCount());  
                }  
            }  
        };  
  
        Runnable writeTask = new Runnable() {  
            @Override  
            public void run() {  
                for (int i = 0; i < 10; i++) {  
                    counter.increment();  
                    System.out.println(Thread.currentThread().getName() + " incremented");  
                }  
            }  
        };  
  
        Thread writerThread = new Thread(writeTask);  
        Thread readerThread1 = new Thread(readTask);  
        Thread readerThread2 = new Thread(readTask);  
  
        writerThread.start();  
        readerThread1.start();  
        readerThread2.start();  
  
        writerThread.join();  
        readerThread1.join();  
        readerThread2.join();  
  
        System.out.println("Final count: " + counter.getCount());  
    }  
}

## ==Fairness of Locks==

Fairness in the context of locks refers to the order in which threads acquire a lock. A fair lock ensures that threads acquire the lock in the order they requested it, preventing thread starvation. With a fair lock, if multiple threads are waiting, the longest-waiting thread is granted the lock next. However, fairness can lead to lower throughput due to the overhead of maintaining the order. Non-fair locks, in contrast, allow threads to “cut in line,” potentially offering better performance but at the risk of some threads waiting indefinitely if others frequently acquire the lock.

import java.util.concurrent.locks.Lock;  
import java.util.concurrent.locks.ReadWriteLock;  
import java.util.concurrent.locks.ReentrantReadWriteLock;  
  
public class FairnessLockExample {  
    private final Lock lock = new ReentrantLock(true);  
  
    public void accessResource() {  
        lock.lock();  
        try {  
            System.out.println(Thread.currentThread().getName() + " acquired the lock.");  
            Thread.sleep(1000);  
        } catch (InterruptedException e) {  
            Thread.currentThread().interrupt();  
        } finally {  
            System.out.println(Thread.currentThread().getName() + " released the lock.");  
            lock.unlock();  
        }  
    }  
  
    public static void main(String[] args) {  
        FairnessLockExample example = new FairnessLockExample();  
  
        Runnable task = new Runnable() {  
            @Override  
            public void run() {  
                example.accessResource();  
            }  
        };  
  
        Thread thread1 = new Thread(task, "Thread 1");  
        Thread thread2 = new Thread(task, "Thread 2");  
        Thread thread3 = new Thread(task, "Thread 3");  
  
        thread1.start();  
        thread2.start();  
        thread3.start();  
    }  
}
## 🔹 Comparison Table

|Feature|`synchronized`|`ReentrantLock`|`ReentrantReadWriteLock`|
|---|---|---|---|
|Read concurrency|❌ Only one thread|❌ Only one thread|✅ Multiple readers allowed|
|Write concurrency|❌ One thread only|✅ One thread only|✅ One thread only|
|Fairness option|❌ No|✅ Yes|✅ Yes|
|Try lock with timeout|❌ No|✅ Yes|✅ Yes|
|Reentrant|✅ Yes|✅ Yes|✅ Yes|
# 🧵 Deadlock in Java

---
## 1. 🔹 What is Deadlock?

- **Deadlock** is a situation in multithreading where two or more threads are permanently blocked, waiting for each other to release resources.
    
- No thread can proceed → program freezes.
    
- Common in synchronized code and when multiple locks are used.

👉 Example analogy:  
Two people are crossing a narrow bridge from opposite ends. Both refuse to step back → both stuck forever.

---
## 2. 🔹 Conditions for Deadlock (Coffman’s Conditions)

Deadlock occurs if **all 4 conditions** are true:

1. **Mutual Exclusion** → Resource can be held by only one thread at a time.
    
2. **Hold and Wait** → A thread is holding one resource and waiting for another.
    
3. **No Preemption** → Resource cannot be forcibly taken; must be released voluntarily.
    
4. **Circular Wait** → A set of threads are waiting for each other in a cycle.

---
## 3. 🔹 Example of Deadlock in Java
class A {}
class B {}

public class DeadlockDemo {
    public static void main(String[] args) {
        final A a = new A();
        final B b = new B();

        Thread t1 = new Thread(() -> {
            synchronized (a) {
                System.out.println("Thread1 locked A");
                try { Thread.sleep(100); } catch (Exception e) {}
                synchronized (b) {
                    System.out.println("Thread1 locked B");
                }
            }
        });

        Thread t2 = new Thread(() -> {
            synchronized (b) {
                System.out.println("Thread2 locked B");
                try { Thread.sleep(100); } catch (Exception e) {}
                synchronized (a) {
                    System.out.println("Thread2 locked A");
                }
            }
        });

        t1.start();
        t2.start();
    }
}

### Output:

`Thread1 locked A Thread2 locked B // now both waiting forever -> DEADLOCK`

# 🧵 Inter-Thread Communication in Java

---
## 🔹 What is it?

- It is a way for threads to **communicate and coordinate** with each other while sharing resources.
    
- Achieved using the methods of `Object` class:
    
    1. **`wait()`** → makes a thread pause until another thread notifies.
        
    2. **`notify()`** → wakes up **one** waiting thread.
        
    3. **`notifyAll()`** → wakes up **all** waiting threads.
        

👉 These methods must be called inside a **synchronized block/method** because they require the monitor (lock) of the object.

---
## 🔹 Why needed?

Imagine a **Producer-Consumer problem**:

- Producer creates data.
    
- Consumer uses data.
    
- If producer produces too fast → overflow.
    
- If consumer consumes too fast → underflow.
    
- They must **coordinate** → this is where `wait()`/`notify()` help.
---
## 🔹 Simple Example – Producer Consumer
class Shared {
    private int data;
    private boolean available = false;

    public synchronized void produce(int value) throws InterruptedException {
        while (available) {
            wait();  // wait if data is not consumed yet
        }
        data = value;
        System.out.println("Produced: " + value);
        available = true;
        notify(); // wake up consumer
    }

    public synchronized void consume() throws InterruptedException {
        while (!available) {
            wait();  // wait until data is produced
        }
        System.out.println("Consumed: " + data);
        available = false;
        notify(); // wake up producer
    }
}

public class InterThreadDemo {
    public static void main(String[] args) {
        Shared shared = new Shared();

        // Producer Thread
        Thread producer = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                try { shared.produce(i); } catch (Exception e) {}
            }
        });

        // Consumer Thread
        Thread consumer = new Thread(() -> {
            for (int i = 1; i <= 5; i++) {
                try { shared.consume(); } catch (Exception e) {}
            }
        });

        producer.start();
        consumer.start();
    }
}
## output

	Produced: 1
	Consumed: 1
	Produced: 2
	Consumed: 2
	...

## 🔹 Interview Notes

- Difference between `sleep()` and `wait()`?
    
    - `sleep()` does not release lock, `wait()` releases lock.
        
- Can we call `wait()` outside synchronized? → ❌ No.
    
- What’s the difference between `notify()` and `notifyAll()`?
    
    - `notify()` wakes one, `notifyAll()` wakes all.
        
- Is `wait()` in `Thread` class? → ❌ No, it’s in `Object` class (because every object has a lock).

# 🧵 Thread Pool in Java

---
## 🔹 What is a Thread Pool?

- A **Thread Pool** is a group of reusable threads managed by the JVM
    
- Instead of creating a new thread every time, we **reuse** threads from the pool.
    
- The pool manages a **queue of tasks** → assigns each task to an available thread.
    
- If no thread is free, tasks wait in the queue.

👉 Think of it like:

- You have **10 workers (threads)** in a company.
    
- Jobs (tasks) keep coming.
    
- You don’t hire a new worker for every job → you assign jobs to existing workers.

---

## 🔹 Why use Thread Pool?

1. **Performance** → Creating/destroying threads repeatedly is expensive.
    
2. **Resource control** → Too many threads can crash JVM. A pool limits max threads.
    
3. **Reusability** → Threads are reused for multiple tasks.
    
4. **Scalability** → Good for servers (like Tomcat, Spring Boot), where thousands of requests come in.
### Example

`import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class WithThreadPool {
    public static void main(String[] args) {
        ExecutorService pool = Executors.newFixedThreadPool(3); // 3 threads in pool

        for (int i = 1; i <= 5; i++) {
            int taskId = i;
            pool.execute(() -> {
                System.out.println("Task " + taskId + " executed by " + Thread.currentThread().getName());
            });
        }

        pool.shutdown();
    }
}
`
OP-

Task 1 executed by pool-1-thread-1
Task 2 executed by pool-1-thread-2
Task 3 executed by pool-1-thread-3
Task 4 executed by pool-1-thread-1   // thread reused
Task 5 executed by pool-1-thread-2   // thread reused

## ==Executor Framework==

   ## **1. What is Executor Framework in Java?**

**Answer:**

- Part of `java.util.concurrent` (Java 5+).
    
- Manages **thread creation, execution, and lifecycle**.
    
- Separates **task submission** from **thread management**.
    
- Supports **thread pools, scheduled tasks, and async result handling**.

---
## **2. Why do we use Executor Framework?**

**Answer:**

- Avoid manually creating threads → reduces overhead.
    
- Reuse threads via **thread pool** → better performance.
    
- Submit tasks without worrying about thread lifecycle.
    
- Supports **Callable + Future** for results.
    
- Allows **scheduling tasks** (delayed/periodic).
---
## **3. What is the difference between Runnable and Callable?**

|Feature|Runnable|Callable|
|---|---|---|
|Return value|No (`void`)|Yes (`V`)|
|Can throw checked exception|No|Yes|
|Method|`run()`|`call()`|
|Used with|Executor / Thread|ExecutorService|

---
## **4. What is ExecutorService?**

**Answer:**

- Sub-interface of `Executor`.
    
- Manages thread lifecycle.
    
- Can submit tasks with **Runnable or Callable**.
    
- Provides methods: `submit()`, `invokeAll()`, `invokeAny()`, `shutdown()`, `shutdownNow()`.
---
## **5. What is ScheduledExecutorService?**

**Answer:**

- Extends ExecutorService.
    
- Supports **delayed and periodic task execution**.
    
- Methods:
    
    - `schedule()` → execute once after delay
        
    - `scheduleAtFixedRate()` → fixed interval execution
        
    - `scheduleWithFixedDelay()` → fixed delay after previous execution
---

## **6. What is Future in Java?**

**Answer:**

- Represents result of **asynchronous computation**.
    
- Methods:
    
    - `get()` → waits and returns result
        
    - `isDone()` → checks if task completed
        
    - `cancel()` → cancels task
        
    - `isCancelled()` → checks if task cancelled

---
## **7. How do you create a Thread Pool in Java?**

`ExecutorService executor = Executors.newFixedThreadPool(5); ExecutorService single = Executors.newSingleThreadExecutor(); ExecutorService cached = Executors.newCachedThreadPool(); ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);`

---
## **8. Difference between execute() and submit()**

|Method|execute()|submit()|
|---|---|---|
|Returns|void|Future<V>|
|Accepts|Runnable|Runnable or Callable|
|Exception|Uncaught exceptions go to thread handler|Exceptions captured in Future|

---
## **9. What is ThreadPoolExecutor?**

**Answer:**

- Core class behind thread pools.
    
- Can configure:
    
    - `corePoolSize`, `maximumPoolSize`, `keepAliveTime`, `workQueue`, `RejectedExecutionHandler`
        
- Allows **fine-grained control over thread pool behavior**.
---

## **10. What are RejectedExecutionHandler policies?**

|Policy|Description|
|---|---|
|AbortPolicy|Throws RejectedExecutionException|
|CallerRunsPolicy|Caller thread runs task|
|DiscardPolicy|Silently discards task|
|DiscardOldestPolicy|Removes oldest task and adds new|

---
                ┌───────────────────────────────┐
                │        Executor Framework     │
                │  (java.util.concurrent)       │
                └───────────────┬───────────────┘
                                │
                                │
               ┌────────────────┴─────────────────┐
               │                                  │
          ┌───────────────┐                ┌───────────────┐
          │   Executor    │                │ ExecutorService│
          │ execute(Runnable)│             │ submit(Runnable/Callable)
          └───────────────┘                │ shutdown()/shutdownNow()
                                           │ invokeAll()/invokeAny()
                                           └───────────────┘
                                                     │
                                                     │
                                   ┌─────────────────┴─────────────────┐
                                   │                                   │
                     ┌─────────────────────────┐         ┌─────────────────────────┐
                     │ ScheduledExecutorService │         │ ThreadPoolExecutor      │
                     │ schedule()/scheduleAt…  │         │ core/max threads, queue│
                     │ delayed/fixed tasks     │         │ RejectionHandler       │
                     └─────────────────────────┘         └─────────────────────────┘

# 📘 ==ExecutorService== 
## 🔹 1. `execute(Runnable task)`

Runs a `Runnable` task without returning a result.

`ExecutorService ex = Executors.newSingleThreadExecutor(); ex.execute(() -> System.out.println("Task executed using execute()")); ex.shutdown();`

---

## 🔹 2. `submit(Runnable task)`

- Runs a `Runnable` task.
    
- Returns a `Future<?>` (but since Runnable returns nothing → result is `null`).
    

`ExecutorService ex = Executors.newSingleThreadExecutor(); Future<?> f = ex.submit(() -> System.out.println("Runnable via submit()")); System.out.println("Task done? " + f.isDone()); ex.shutdown();`

---

## 🔹 3. `submit(Callable<T> task)`

- Runs a `Callable` task.
    
- Returns a `Future<T>` containing result.
    

`ExecutorService ex = Executors.newSingleThreadExecutor(); Future<Integer> f = ex.submit(() -> 5 * 5); System.out.println("Result: " + f.get()); // 25 ex.shutdown();`

---

## 🔹 4. `Future` methods

A `Future` object represents the result of an async computation.

|Method|Use|
|---|---|
|`get()`|Waits & returns result|
|`get(timeout, unit)`|Waits up to time limit|
|`isDone()`|true if task completed|
|`isCancelled()`|true if cancelled|
|`cancel(true/false)`|cancels the task|

`ExecutorService ex = Executors.newSingleThreadExecutor(); Future<Integer> f = ex.submit(() -> {     Thread.sleep(1000);     return 42; });  System.out.println("Is done? " + f.isDone());  System.out.println("Result: " + f.get()); // blocks until ready System.out.println("Is done? " + f.isDone());  ex.shutdown();`

---

## 🔹 5. `invokeAll(Collection<? extends Callable<T>> tasks)`

Runs multiple tasks → waits for **all** to finish → returns `List<Future<T>>`.

`ExecutorService ex = Executors.newFixedThreadPool(2);  List<Callable<Integer>> tasks = List.of(     () -> 10,     () -> 20,     () -> 30 );  List<Future<Integer>> results = ex.invokeAll(tasks); for (Future<Integer> r : results) {     System.out.println("Result: " + r.get()); } ex.shutdown();`

**Output:**

`Result: 10 Result: 20 Result: 30`

---

## 🔹 6. `invokeAny(Collection<? extends Callable<T>> tasks)`

Runs multiple tasks → returns result of **first completed** task → cancels the rest.

`ExecutorService ex = Executors.newFixedThreadPool(3);  List<Callable<String>> tasks = List.of(     () -> { Thread.sleep(2000); return "Task 1"; },     () -> { Thread.sleep(1000); return "Task 2"; },     () -> "Task 3" );  String result = ex.invokeAny(tasks); System.out.println("First completed: " + result); ex.shutdown();`

**Output (may vary):**

`First completed: Task 3`

---

## 🔹 7. `shutdown()`

- Initiates **graceful shutdown**.
    
- Already submitted tasks finish, new tasks rejected.
    

`ExecutorService ex = Executors.newSingleThreadExecutor(); ex.submit(() -> System.out.println("Task running")); ex.shutdown(); System.out.println("Shutdown called");`

---

## 🔹 8. `shutdownNow()`

- **Immediately stops** all running tasks (interrupts).
    
- Returns list of pending tasks.
    

`ExecutorService ex = Executors.newFixedThreadPool(2);  ex.submit(() -> { while (true); }); // endless loop  List<Runnable> pending = ex.shutdownNow(); System.out.println("Pending tasks: " + pending.size());`

---

## 🔹 9. `isShutdown()` and `isTerminated()`

- `isShutdown()` → true if shutdown requested.
    
- `isTerminated()` → true if all tasks finished after shutdown.
    

`ExecutorService ex = Executors.newSingleThreadExecutor(); ex.submit(() -> System.out.println("Task")); ex.shutdown(); System.out.println("isShutdown: " + ex.isShutdown()); System.out.println("isTerminated: " + ex.isTerminated());`

---

## 🔹 10. `awaitTermination(long timeout, TimeUnit unit)`

- Waits for given time for tasks to finish after shutdown.
    

`ExecutorService ex = Executors.newFixedThreadPool(2);  ex.submit(() -> { Thread.sleep(1000); return null; }); ex.shutdown();  if (ex.awaitTermination(2, TimeUnit.SECONDS)) {     System.out.println("All tasks completed."); } else {     System.out.println("Timeout – some tasks still running."); }`

---

# 🎯 Quick Summary Table

| Method                | Purpose                               |
| --------------------- | ------------------------------------- |
| `execute(Runnable)`   | Run task (no result)                  |
| `submit(Runnable)`    | Run task, return `Future<?>`          |
| `submit(Callable<T>)` | Run task, return `Future<T>`          |
| `invokeAll()`         | Run many tasks, wait for all          |
| `invokeAny()`         | Run many tasks, return first finished |
| `Future.get()`        | Get result (blocks if needed)         |
| `Future.isDone()`     | Check if task finished                |
| `Future.cancel()`     | Cancel task                           |
| `shutdown()`          | Graceful stop                         |
| `shutdownNow()`       | Force stop immediately                |
| `isShutdown()`        | Check if shutdown initiated           |
| `isTerminated()`      | Check if all tasks finished           |
| `awaitTermination()`  | Wait for all tasks after shutdown     |

# 📒 ==JDBC==

---

## 📌 1. Layers of JDBC

JDBC has **two main layers**:

1. **JDBC API Layer (Application Level)**
    
    - Interfaces & classes provided by Java (`Connection`, `Statement`, `ResultSet`).
        
    - Developer writes code using these APIs.
        
2. **JDBC Driver Layer (Implementation Level)**
    
    - Vendor-specific driver (MySQL, Oracle, PostgreSQL).
        
    - Translates JDBC calls into database-specific calls.
        

🔹 Together → API + Driver = Database Independence.

---

## 📌 2. Types of JDBC Drivers

JDBC defines **4 types of drivers**:

1. **Type 1: JDBC-ODBC Bridge Driver**
    
    - Converts JDBC calls → ODBC calls → Database.
        
    - Needs ODBC driver installed.
        
    - **Disadvantage**: Slower, platform-dependent.
        
    - 🚫 Deprecated in Java 8.
        
2. **Type 2: Native API Driver**
    
    - Converts JDBC calls → Native API calls of DB.
        
    - Requires database client libraries on system.
        
    - Faster than Type 1 but still dependent.
        
3. **Type 3: Network Protocol Driver**
    
    - Converts JDBC calls → Middleware server → Database.
        
    - Database-independent, but requires middle-tier server.
        
4. **Type 4: Thin Driver (Pure Java Driver)**
    
    - Converts JDBC calls directly into **database protocol**.
        
    - 100% Java, no native libraries needed.
        
    - **Most widely used** (e.g., MySQL Connector/J).
        
    - ✅ Recommended in real projects.
        

---

## 📌 3. Most Important JDBC Interview Questions with Answers

### 🔹 Q1. What is JDBC?

👉 JDBC is an API that allows Java applications to connect to relational databases, execute SQL statements, and process results.

---

### 🔹 Q2. What are the steps to connect to a database in JDBC?

👉

1. Load Driver
    
2. Establish Connection
    
3. Create Statement / PreparedStatement
    
4. Execute Query
    
5. Process Results
    
6. Close Connection
    
```import java.sql.Connection;
import java.sql.DriverManager;

public class JdbcDemo {
    public static void main(String[] args) {
        try {
            Connection con = DriverManager.getConnection(
                "jdbc:mysql://localhost:3306/testdb",
                "root",
                "root"
            );

            System.out.println("Connection successful");

            con.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```
---

### 🔹 Q3. Difference between `Statement` and `PreparedStatement`?

- **Statement** → Executes static queries (slower, prone to SQL injection).
    
- **PreparedStatement** → Executes precompiled queries with parameters (faster, safer).
    

Example:

`Statement:       "SELECT * FROM users WHERE id = " + id; 
PreparedStatement: "SELECT * FROM users WHERE id = ?"`

---

### 🔹 Q4. What is `ResultSet`?

👉 `ResultSet` is a cursor-like object returned by executing SELECT queries.

- `rs.next()` → Moves to next row.
    
- `rs.getInt("id")` → Reads column value.
    

---

### 🔹 Q5. What are JDBC Driver types? Which one is used today?

👉 Type 1 (ODBC), Type 2 (Native), Type 3 (Middleware), Type 4 (Thin driver).  
👉 **Type 4 (Thin driver)** is used in modern applications.

---

### 🔹 Q6. What is connection pooling in JDBC?

👉 **Connection Pooling** = Reusing existing DB connections instead of creating new ones for each request.

- Improves performance.
    
- Provided by libraries like **HikariCP**, **Apache DBCP**.
    

---

### 🔹 Q7. How to handle transactions in JDBC?

👉

`con.setAutoCommit(false);   // execute queries 
con.commit();   // save 
con.rollback(); // undo if failure`

---

### 🔹 Q8. Difference between `executeQuery()`, `executeUpdate()`, `execute()`?

- `executeQuery()` → For **SELECT** (returns `ResultSet`).
    
- `executeUpdate()` → For **INSERT, UPDATE, DELETE** (returns int row count).
    
- `execute()` → For **DDL** or unknown queries (returns boolean).
    

---

### 🔹 Q9. What is the role of `DriverManager`?

👉 Manages registered JDBC drivers and establishes DB connections.

`Connection con = DriverManager.getConnection(url, user, pass);`

---

### 🔹 Q10. How do you prevent SQL Injection in JDBC?

👉 Use **PreparedStatement** instead of concatenating SQL strings.

---

### 🔹 Q11. What is difference between JDBC and Hibernate?

- JDBC → Low-level, manual queries, SQL-specific.
    
- Hibernate → ORM, maps Java objects to tables, auto-generates SQL, higher level.
    

---

## ✅ Summary (Quick Revision)

- **Layers** → API + Driver.
    
- **Driver Types** → Type 1 to Type 4 (Thin driver used today).
    
- **Steps** → Load driver → Connect → Statement → Query → Close.
    
- **Key Interfaces** → DriverManager, Connection, Statement, PreparedStatement, ResultSet.
    
- **Interview Topics** → Statement vs PreparedStatement, Transactions, Driver types, Connection Pooling, execute methods.