# 📘 02. Basic Types in TypeScript

---

## Core Primitive Types

### ✅ `string`
```ts
let userName: string = "Divyanshi";
```

### ✅ `number`
```
let age: number = 22;
```

### ✅ `boolean`
```
let isLoggedIn: boolean = true;
```

## ⚠️ Flexible Types

### ✅ any (Avoid when possible)
Disables type checking.

```
let data: any = "Text";
data = 10; // No error
```

### ✅ unknown (Safer than any)
```
let input: unknown;
input = 10;
input = "hello";

if (typeof input === "string") {
  console.log(input.toUpperCase());
}
```

### ✅ void (Used in functions with no return)
```
function greet(): void {
  console.log("Hello");
}
```

### ✅ never (Function never returns)
```
function throwError(message: string): never {
  throw new Error(message);
}
```

## 🧾 Arrays

### ✅ Number Array
```
let numbers: number[] = [1, 2, 3];
```

### ✅ String Array
```
let colors: string[] = ["red", "blue"];
```

### ✅ Generic Array
```
let scores: Array<number> = [95, 85, 76];
```

## 🎯 Tuples

Fixed-length array with specific types.

```
let user: [string, number] = ["Divyanshi", 22];
```

## 🏷️ Enums

A set of named constants.

### ✅ Numeric Enum
```
enum Direction {
  Up,    // 0
  Down,  // 1
  Left,  // 2
  Right  // 3
}
let move: Direction = Direction.Left;
```

### ✅ String Enum
```
enum Status {
  Success = "SUCCESS",
  Failure = "FAILURE"
}
let result: Status = Status.Success;
```
## ✅ Summary

| Type     | Description                                 |
|----------|---------------------------------------------|
| `string` | Text data                                   |
| `number` | Numeric values                              |
| `boolean`| true/false                                  |
| `any`    | Any value, disables type checking           |
| `unknown`| Like `any` but safer                        |
| `void`   | No return value                             |
| `never`  | Function that never returns                 |
| Arrays   | List of values of a single type             |
| Tuples   | Fixed-size array with specific types        |
| Enums    | Named constants (numeric or string values)  |

## ✅ TypeScript Interview Q&A

### Q1. What’s the difference between `any` and `unknown`?
- `any` bypasses all type checking.
- `unknown` is safer—you must do a type check before using it.
- ✅ Prefer `unknown` over `any` when you don’t know the type yet.

---

### Q2. What is the use of the `never` type?
Indicates a function that never returns (e.g., throws an error or enters an infinite loop).

```ts
function fail(): never {
  throw new Error("Something went wrong");
}
```

---

### Q3. What is the key difference between `void` and `never`?

| Feature  | `void`               | `never`                            |
|----------|----------------------|-------------------------------------|
| Returns  | No value             | Never returns                       |
| Example  | Logging function     | Error throwing or infinite loop     |
| Usage    | `function foo(): void {}` | `function foo(): never {}`         |

---

### Q4. Why are string enums considered safer than numeric enums in frontend applications?
- String enums provide more readable values (`"SUCCESS"` vs `0`).
- Less prone to bugs due to accidental number misassignment.

---

### Q5. Is `number[]` the same as `Array<number>`?
✅ Yes, both are equivalent:

```ts
let arr1: number[] = [1, 2];
let arr2: Array<number> = [1, 2];
```

- Use `number[]` for simplicity.
- `Array<Type>` is preferred in generic contexts.

