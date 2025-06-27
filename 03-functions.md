# 📘 03. Functions in TypeScript

---

## ✅ Function Return Types

You can explicitly define the return type of a function:

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

If no return value is expected:

```
function logMessage(message: string): void {
  console.log(message);
}
```

## 🔹 Optional & Default Parameters
### ✅ Optional Parameters (?)
Parameters that may or may not be passed.

```
function greet(name?: string): string {
  return `Hello, ${name || "Guest"}`;
}
```

### ✅ Default Parameters
Provide a fallback value.

```
function multiply(a: number, b: number = 2): number {
  return a * b;
}
```

## 🔁 Function Types & Callbacks
### ✅ Function Type Annotation
```
let sum: (a: number, b: number) => number;

sum = (x, y) => {
  return x + y;
};
```

### ✅ Callback Functions
```
function handleClick(callback: () => void) {
  console.log("Button clicked");
  callback();
}

handleClick(() => {
  console.log("Callback executed");
});
```

## 🚫 `void` vs `never`

| Keyword | Meaning                                    | Example Use                      |
|---------|--------------------------------------------|----------------------------------|
| `void`  | Function does not return anything          | Logging or side-effect functions |
| `never` | Function never completes or always throws  | Infinite loops, throw errors     |


🔹 void Example
```
function printMessage(msg: string): void {
  console.log(msg);
}
```
🔹 never Example
```
function throwError(message: string): never {
  throw new Error(message);
}
```

## ✅ Summary

| Concept                 | Description                                      |
|-------------------------|--------------------------------------------------|
| Return Types            | Define what a function returns                   |
| Optional Parameters     | Allow skipping parameters using `?`              |
| Default Parameters      | Use default values for missing arguments         |
| Function Type Annotation| Define function signatures using types           |
| Callbacks               | Pass functions as arguments                      |
| `void`                  | No return value                                  |
| `never`                 | Function that throws or never finishes           |

## 🧠 Interview Questions for “Functions in TypeScript”

### Q1. What is the difference between `?` (optional) and default parameters?
- `?` means the parameter might be `undefined`.
- Default parameters guarantee a value even if none is passed.

```ts
function greet(name?: string) {}
function greet2(name: string = "Guest") {}
```

---

### Q2. Can we define a function with both optional and default parameters?
✅ Yes, but optional parameters must come last, and default parameters can be anywhere.

```ts
function example(a: string, b: string = "default", c?: number) {}
```

---

### Q3. What’s the difference between `void` and `undefined` return types?
- `void`: Indicates no value is returned (e.g., `console.log()`).
- `undefined`: You can explicitly return `undefined`.

```ts
function foo(): void {
  return; // ✅ OK
}

function bar(): undefined {
  return undefined; // ✅ Only undefined allowed
}
```

---

### Q4. Can you define a function type that takes another function as an argument?
✅ Yes, use a callback type.

```ts
type Callback = (data: string) => void;

function process(cb: Callback) {
  cb("data");
}
```

---

### Q5. How does TypeScript help catch function-related bugs?
- Ensures correct number and type of parameters
- Prevents accidental return types
- Safer callback functions with explicit types

