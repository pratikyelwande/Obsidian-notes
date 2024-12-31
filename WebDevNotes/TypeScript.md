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

