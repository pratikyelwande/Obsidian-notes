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
```function greet(...names: string[]): void { console.log(`Hello, ${name}`); }
```
