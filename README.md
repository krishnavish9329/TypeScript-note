# TypeScript Notes – Complete Beginner Guide

A beginner-friendly TypeScript learning guide covering basic concepts, data types, compiler configuration, type inference, type annotations, arrays, tuples, and more.

---

# 1. What is TypeScript?

**TypeScript (TS)** is a programming language built on top of JavaScript that adds static typing and other development features to JavaScript.

### In Simple Words

TypeScript is JavaScript with extra features that help you write cleaner, safer, and more maintainable code.

- Developed by Microsoft.
- It is a superset of JavaScript.
- It supports static typing.
- It helps identify errors during development.
- TypeScript code is compiled into JavaScript.

### Why Do We Need TypeScript?

We need TypeScript because it helps us catch type-related errors during development.

JavaScript allows variables to hold different types of values, while TypeScript helps us define and maintain expected data types.

---

# 2. JavaScript vs TypeScript

| Feature | JavaScript | TypeScript |
|---|---|---|
| Typing | Dynamic | Static (optional) |
| Error Detection | Mostly runtime | Compile-time type checking |
| Interfaces | Not supported natively | Supported |
| Type Safety | Less | More |
| Learning Curve | Easy | Slightly harder |
| Browser Support | Directly supported | Compiles to JavaScript |
| Compilation | Not required | Requires transpilation |

---

# 3. Data Types in TypeScript

TypeScript provides different data types to define what kind of values a variable can store.

### Main TypeScript Data Types

1. `number` – Numbers
2. `string` – Text
3. `boolean` – True or False
4. `any` – Any value without type safety
5. `unknown` – Any value with type checking
6. `void` – No meaningful return value
7. `never` – Represents values that never occur
8. `array` – Collection of values
9. `object` – Key-value pairs
10. `tuple` – Fixed types and positions
11. `enum` – Named constants
12. `union` – Multiple allowed types

---

# 4. What is tsconfig.json in TypeScript?

`tsconfig.json` is a configuration file that tells the TypeScript compiler (`tsc`) how to compile and check your TypeScript code.

### In Simple Words

Imagine you have a TypeScript project with 100 files. The TypeScript compiler needs to know:

- Which files should it compile?
- Where should it save the compiled JavaScript files?
- Which JavaScript version should it generate?
- How strictly should it check your code?
- Should it allow certain types of errors?

All these instructions are defined in `tsconfig.json`.

### Interview Definition

"tsconfig.json is the configuration file of a TypeScript project. It tells the TypeScript compiler which files to compile, which JavaScript version to target, where to generate output files, and which type-checking rules to apply. It helps maintain consistent compiler settings across the entire project."

---

# 5. How to Create tsconfig.json?

Use the following command:

```bash
npx tsc --init
```

This command generates a `tsconfig.json` file in your project.

---

# 6. TypeScript Compiler (tsc)

The **TypeScript Compiler (tsc)** is a tool that checks TypeScript code and compiles it into JavaScript code.

### In Simple Words

You write TypeScript → `tsc` checks and compiles it → JavaScript is generated.

Browsers and Node.js execute JavaScript, not TypeScript directly.

### Example

Create a file named `index.ts`:

```typescript
let username: string = "Krishna";

console.log(username);
```

Compile the TypeScript file:

```bash
npx tsc index.ts
```

Output file: `index.js`

Run the generated JavaScript:

```bash
node index.js
```

---

# 7. Type Inference in TypeScript

**Type Inference** is a feature in TypeScript that automatically detects the data type of a variable based on the value assigned to it.

### In Simple Words

You don't always need to explicitly write the data type. TypeScript can understand the type automatically.

### Without Type Inference (Explicit Typing)

```typescript
let username: string = "Krishna";
let age: number = 22;
let isDeveloper: boolean = true;
```

Here, we explicitly define the data types.

### With Type Inference (Implicit Typing)

```typescript
let username = "Krishna";
let age = 22;
let isDeveloper = true;
```

Here, TypeScript automatically identifies:

- `username` → string
- `age` → number
- `isDeveloper` → boolean

### Interview Definition

"Type Inference is a TypeScript feature that automatically determines the type of a variable, function return value, or expression based on the available information, without requiring explicit type annotations."

---

# 8. Type Annotations in TypeScript

**Type Annotations** are used to explicitly specify the data type of a variable, function parameter, function return value, or object property in TypeScript.

### In Simple Words

Type Annotations tell TypeScript what type of data a variable should accept.

We use a colon (`:`) to define a type.

### Example

```typescript
let username: string = "Krishna";
let age: number = 23;
let isDeveloper: boolean = true;
```

---

# 9. Basic Data Types in TypeScript

## 9.1 String

The `string` data type is used to store text values.

```typescript
let username: string = "Krishna";

console.log(username);
```

## 9.2 Number

The `number` data type is used to store numeric values, including integers and decimal numbers.

```typescript
let age: number = 23;
let price: number = 99.99;

console.log(age);
console.log(price);
```

## 9.3 Boolean

The `boolean` data type stores only two values: `true` or `false`.

```typescript
let isDeveloper: boolean = true;
let isLoggedIn: boolean = false;

console.log(isDeveloper);
console.log(isLoggedIn);
```

## 9.4 Null

`null` represents the intentional absence of a value.

### In Simple Words

When you want to indicate that a variable currently has no value, you can assign `null` to it.

### Examples

- A user has no profile picture.
- An employee has no manager assigned.
- An API response has no data.
- A selected item has been cleared.

```typescript
let name: string | null = "Krishna";

name = null;       // Allowed
name = "Krishna";  // Allowed
```

## 9.5 Undefined

`undefined` represents a value that has not been assigned.

### In Simple Words

When a variable exists but doesn't have an assigned value, its value is usually `undefined`.

### Examples

- A variable is declared but no value is assigned.
- An object property does not exist.
- A function does not return anything explicitly.
- An API response is missing an optional field.

```typescript
let age: string | undefined;

console.log(age); // Output: undefined
```

### Interview Definition

"`undefined` is a primitive value that indicates a variable has not been assigned a value or a property is missing. In TypeScript, with strictNullChecks enabled, we need to explicitly include undefined in a variable's type if we want it to accept undefined."

## 9.6 Any

`any` is a special TypeScript data type that allows a variable to store values of any data type without generating type errors.

### Example

```typescript
let data: any = "Krishna";

data = 22;
data = true;
data = [10, 20, 30];
data = { name: "Krishna" };
data = null;
data = undefined;

console.log(data);
```

### Why Should We Avoid any?

```typescript
let username: any = "Krishna";

console.log(username.toUpperCase()); // Works

console.log(username.toFixed(2)); // Runtime Error
```

The first statement works because strings have the `toUpperCase()` method.

But the second statement causes a runtime error because strings don't have the `toFixed()` method.

**Problem:** TypeScript doesn't catch this mistake because the variable is declared as `any`.

### Interview Definition

"`any` is a special TypeScript type that allows a variable to hold values of any data type. It disables most type checking for that variable, so TypeScript cannot catch many type-related errors. Therefore, it should be avoided when possible."

## 9.7 Unknown

`unknown` is a data type that allows you to store values of any data type, but requires you to check the type before performing operations on that value.

### In Simple Words

`unknown` accepts any value, but TypeScript doesn't allow you to use that value until you verify its data type.

It is a safer alternative to `any`.

### Example

```typescript
let data: unknown = "Krishna";

if (typeof data === "string") {
    console.log(data.toUpperCase());
}
```

### Difference Between any and unknown

| any | unknown |
|---|---|
| Accepts any value | Accepts any value |
| No meaningful type safety | Type safety is maintained |
| Allows operations without checking | Requires type checking before operations |
| Less safe | More safe |

### Interview Definition

"`unknown` is a special TypeScript type that can hold values of any data type. Unlike `any`, it does not allow us to perform operations directly on the value without first checking or narrowing its type. It provides better type safety and is useful when handling dynamic or external data."

## 9.8 Void

`void` is used to indicate that a function does not return a meaningful value.

### Example 1

```typescript
function greet(): void {
    console.log("Hello Krishna");
}

greet();
```

### Example 2

```typescript
function displayUser(name: string): void {
    console.log(`Welcome ${name}`);
}

displayUser("Krishna");

// Output: Welcome Krishna
```

### Interview Definition

"`void` is a TypeScript type primarily used as a function return type. It indicates that a function does not return a meaningful value. It is commonly used with functions that perform actions such as logging messages, updating data, or handling events."

## 9.9 Never

`never` represents a value that never occurs.

### In Simple Words

`never` is used when a function never completes normally or when a variable cannot have any possible value.

### Common Use Cases

- Functions that always throw errors.
- Functions that never stop executing.
- Exhaustive type checking.
- Handling impossible conditions in TypeScript.

### Example 1: Function That Throws an Error

```typescript
function throwError(): never {
    throw new Error("Something went wrong!");
}
```

### Example 2: Infinite Loop

```typescript
function infiniteLoop(): never {
    while (true) {
        console.log("Running...");
    }
}
```

## 9.10 Object

The `object` type is used to represent non-primitive values, such as objects, arrays, and functions.

In TypeScript, we can define the structure of an object by specifying its properties and their types.

### Example

```typescript
let user: {
    name: string;
    age: number;
    email: string;
    isActive: boolean;
} = {
    name: "Krishna",
    age: 23,
    email: "krishna@example.com",
    isActive: true
};
```

### Optional Properties (?)

Sometimes an object property is not required. We can use `?` to make a property optional.

```typescript
type User = {
    id: number;
    name: string;
    email: string;
    age?: number;
};
```

### Object Using type (Recommended)

Instead of writing the object structure repeatedly, you can create a reusable type.

```typescript
type User = {
    id: number;
    name: string;
    email: string;
    age?: number;
};

let user1: User = {
    id: 1,
    name: "Krishna",
    email: "krishna@example.com"
};

let user2: User = {
    id: 2,
    name: "Rahul",
    email: "rahul@example.com",
    age: 25
};
```

### Object Using interface

You can also define object structures using an interface.

```typescript
interface User {
    id: number;
    name: string;
    email: string;
}

const user: User = {
    id: 1,
    name: "Krishna",
    email: "krishna@example.com"
};
```

---

# 10. Arrays in TypeScript

An **Array** is used to store multiple values in a single variable.

In TypeScript, we can define the data type of array elements.

### Method 1: Using Type[]

```typescript
let numbers: number[] = [10, 20, 30, 40];

let names: string[] = ["Krishna", "Rahul", "Amit"];

console.log(numbers);
console.log(names);
```

### Method 2: Using Array<type>

```typescript
let numbers: Array<number> = [10, 20, 30];

let names: Array<string> = ["Krishna", "Rahul"];
```

### Array of Objects

```typescript
type User = {
    id: number;
    name: string;
};

let users: User[] = [
    {
        id: 1,
        name: "Krishna"
    },
    {
        id: 2,
        name: "Rahul"
    }
];

console.log(users);
```

### Mixed Type Array Using Union

```typescript
let data: (string | number)[] = [
    "Krishna",
    22,
    "Rahul",
    25
];
```

---

# 11. Tuples in TypeScript

A **Tuple** is a special type of array in TypeScript where you define the type of each element at a specific position.

In a normal array, all elements usually have the same type. In a tuple, different positions can have different types.

### Example

```typescript
let user: [number, string, boolean] = [
    101,
    "Krishna",
    true
];
```

Here:

- First position → number
- Second position → string
- Third position → boolean

### Tuple with Optional Elements

We can make tuple elements optional using `?`.

```typescript
let user: [number, string, boolean?];

user = [101, "Krishna"];

user = [102, "Rahul", true];
```

### Named Tuples

Named tuples allow us to provide meaningful names to tuple elements.

```typescript
let user: [
    id: number,
    name: string,
    isActive: boolean
] = [101, "Krishna", true];
```

### Readonly Tuple

A readonly tuple does not allow modification of its elements.

```typescript
let user: readonly [number, string] = [
    101,
    "Krishna"
];

console.log(user[0]); // Valid

// user[0] = 102; // Error
// user.push(103); // Error
```

---

# Learning Progress

- [x] What is TypeScript?
- [x] JavaScript vs TypeScript
- [x] Data Types Overview
- [x] tsconfig.json
- [x] TypeScript Compiler (tsc)
- [x] Type Inference
- [x] Type Annotations
- [x] Basic Data Types
- [x] Arrays
- [x] Tuples

**More topics to learn:** Union Types, Intersection Types, Enums, Type Aliases, Interfaces, Functions, Generics, Type Narrowing, Utility Types, Classes, Modules, and Advanced TypeScript.

---

**Author:** Krishna Kumar Vishwakarma

**Language:** TypeScript

**Level:** Beginner
