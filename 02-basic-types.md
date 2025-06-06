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
