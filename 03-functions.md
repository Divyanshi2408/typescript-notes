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
