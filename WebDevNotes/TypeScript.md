`# TYPESCRIPT NOTES  ## Install TypeScript globally: ```bash npm i typescript -g`

---

## Types:

1. **Primitives**: `number`, `boolean`, `undefined`, `string`, `bigint`, `symbol`
2. **References**: objects, classes, functions, arrays, tuples

---

## To compile a file, use the terminal:

`tsc [filename.ts]`

This will convert the `.ts` file to `.js`.
`tsc--watch` will compile ts file in real time.

---

## Basic Types:

- **Number**, **String**, **Boolean**
- **Array**, **Tuples**
- **Any**, **Unknown**, **Never**, **Void**

### Note:

Avoid using `any` in TypeScript, as it disables type checking.

Example:

typescript

Copy code

`let a: number = 3;`

### Tuple Example:

typescript

`let arr: [number, string] = [1, "hello"];`

- **Never**: Represents the type of values that never occur (e.g., functions that throw errors or infinite loops).
- **Void**: Used for functions that don't return a value.
- **Enums**: An enum is a special "class" that represents a group of constants.

Example:

typescript



`enum Direction {   Up,   Down,   Left,   Right }`

---

## Type Inference:

TypeScript automatically infers the type based on the assigned value.

---

## Union and Intersection Types:

Union types are used when a value can be more than one type.

Example:

typescript

``let variable: string | null;  function printStatusCode(code: string | number) {   console.log(`My status code is ${code}.`); }  printStatusCode(404); printStatusCode('404');``

##  Type- [&]
eg.
```
`type CarYear = number;
type CarType = string;
type CarModel = string;
type Car = {
  year: CarYear,
  type: CarType,
  model: CarModel
};
const carYear: CarYear = 2001
const carType: CarType = "Toyota"
const carModel: CarModel = "Corolla"
const car: Car = {
  year: carYear,
  type: carType,
  model: carModel
};
console.log(car);
```
## Interfaces

Interfaces are similar to type aliases, except they **only** apply to `object` types.

## Implicit Return Type-
**Automatically decide** the return type based on the value that is returned.

## Explicit Return Type-
manually define the return type

## Rest Parameter-
**rest parameter** allows a function to accept an indefinite number of arguments as an array
```
function greet(...names: string[]): void { console.log(`Hello, ${name}`); }
```

### Options in TS (tsconfig.json)
	rootDir- used to store TS converted JS files.
	 noImplicitAny - Loosen the strictness of TS
	 
## Interfaces-
An **interface** in TypeScript is like a **blueprint** for an object. It tells what properties and methods an object should have and their types.

#### Basic Object Interface

`interface User {   name: string;   age: number; }  const user: User = {   name: "John",   age: 30, }; console.log(user.name); // Output: John`

if u use interface User{
fnm:string,
		==email?:string [It means it is optional parameter.]==
 }

### **Class Implements Interface in TypeScript**

When a class **implements** an interface, it means the class must follow the structure defined by the interface. This ensures the class has all the properties and methods specified in the interface.


```
interface Animal {
  name: string;
  makeSound(): void;
}

class Dog implements Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  makeSound() {
    console.log("Woof! Woof!");
  }
}

const myDog = new Dog("Buddy");
console.log(myDog.name); // Output: Buddy
myDog.makeSound(); // Output: Woof! Woof!
```

#### **What are Types?**

In TypeScript, **types** define the shape of data. They help ensure variables, functions, and objects are used consistently.

---

#### **2. Common Types in TypeScript:**

- **Primitive Types**: `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`.
- **Special Types**: `any`, `unknown`, `void`, `never`.
- **Custom Types**: `type` and `interface`.

---

#### **3. Type Aliases (`type`)**

- A way to name a custom type for reuse.

**Example:**

typescript

Copy code

`type Point = { x: number; y: number };  const p: Point = { x: 10, y: 20 };`

---

#### **4. Union Types (`|`)**

- A variable can have **one of multiple types**.

**Example:**

typescript

Copy code

`type ID = string | number;  let userId: ID; userId = 123;    // Valid userId = "abc";  // Valid`

**When to Use?**  
When you want flexibility between multiple types.

---

#### **5. Intersection Types (`&`)**

- Combines multiple types into a **single type** that includes all properties.

**Example:**

typescript

Copy code

`type Person = { name: string }; type Employee = { company: string };  type WorkingPerson = Person & Employee;  const worker: WorkingPerson = {   name: "John",   company: "TechCorp", };`

# Pick
### **`Pick` in TypeScript**

The **`Pick` utility type** in TypeScript is used to create a new type by selecting specific keys from an existing type. It helps in creating a subset of a type by picking only the required properties.

---
### **Syntax:**

typescript

`Pick<Type, Keys>`

- **`Type`**: The original type you want to pick properties from.
- **`Keys`**: The keys you want to include in the new type.

---
### **Why Use `Pick`?**

- To extract only the required properties from a large type.
- Helps in reducing type duplication.
- Useful for APIs where only a subset of data is needed.

---
### **Example:**

typescript

```
// Original Type 
type User = {   id: number;   name: string;   email: string;   isAdmin: boolean; }; 
// Create a new type with only `id` and `name` 
type UserPreview = Pick<User, "id" | "name">;  
const user: UserPreview = {   id: 1,   name: "Pratik", };
console.log(user); // Output: { id: 1, name: "Pratik" }
`````

# Partial
### **TypeScript `Partial` Utility Type**

The `Partial` utility type in TypeScript is used to make all properties of an object type optional.

​when you want to work with objects that might only have some properties of a defined type.

---

### **Example**

typescript

```
interface User {   id: number;   name: string;   email: string; }
// Use Partial to make all properties optional 
const updateUser = (id: number, userData: Partial<User>): void =>
{   console.log(`Updating user ${id} with data:`, userData); };  
updateUser(1, { name: "Pratik" });
// Only updates the name 
updateUser(2, { email: "pratik@example.com" }); // Only updates the email
```

### ** Readonly Utility Type**

The `Readonly` utility type in TypeScript is used to make all properties of an object type immutable. Once a property is set, it cannot be changed.

---

You use `Readonly` when you want to ensure that the properties of an object are not accidentally modified.

---

### **Example**

typescript

Copy code

`interface User {   id: number;   name: string;   email: string; }  // Make all properties readonly const user: Readonly<User> = {   id: 1,   name: "Pratik",   email: "pratik@example.com", };  // user.id = 2; // Error: Cannot assign to 'id' because it is a read-only property console.log(user.id); // Works fine: Output is 1`

---

### **TypeScript `Record` Utility Type**

The `Record` utility type is used to construct a type with a set of keys and their corresponding values. It allows you to define an object type with specified keys and the type of their values.

---
### **Example**

typescript

```
type UserRoles = Record<string, string>;  
const roles: UserRoles = {   admin: "John",   editor: "Jane",   viewer: "Doe", };  
console.log(roles.admin); // Output: John
````
