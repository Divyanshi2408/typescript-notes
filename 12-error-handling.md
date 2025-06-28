# 🚨 13. Handling Errors & Strict Types in TypeScript

---

## ❗ Error Handling Basics

TypeScript doesn’t change how JavaScript handles errors but makes error handling safer and more predictable through type checks.

### ✅ Try-Catch Block

```ts
try {
  const result = riskyOperation();
  console.log(result);
} catch (error) {
  console.error("Error occurred:", (error as Error).message);
}
```
Use as Error to assert the correct error type inside catch.

## 🧱 Custom Error Types
You can define and throw typed custom errors:

```
class NotFoundError extends Error {
  constructor(message: string) {
    super(message);
    this.name = "NotFoundError";
  }
}

function fetchData(): never {
  throw new NotFoundError("Data not found");
}
```
## 🧪 Safe Return Patterns
Use union types or Result-like patterns to avoid throwing:

```
type Result<T> = { success: true; data: T } | { success: false; error: string };

function parseJSON(input: string): Result<object> {
  try {
    return { success: true, data: JSON.parse(input) };
  } catch {
    return { success: false, error: "Invalid JSON" };
  }
}
```
## 🚧 Strict Mode in tsconfig.json
Enable strong type checking for safer code:

```
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "strictNullChecks": true,
    "strictFunctionTypes": true,
    "strictPropertyInitialization": true
  }
}
```
These settings catch common bugs and improve code robustness.

## 🔐 Common Strict Checks

| Option                      | What It Does                                             |
|-----------------------------|----------------------------------------------------------|
| `noImplicitAny`             | Disallows variables/functions with implied `any`         |
| `strictNullChecks`          | Enforces handling of `null` and `undefined`              |
| `strictFunctionTypes`       | Enforces safer function assignment compatibility         |
| `strictPropertyInitialization` | Ensures all class properties are initialized        |

## ✅ Summary

| Concept                  | Description                                                  |
|--------------------------|--------------------------------------------------------------|
| Try-Catch + `as Error`   | Safely access error properties                               |
| Custom Error Classes     | Create reusable, typed error objects                         |
| Union Result Types       | Return result/error objects instead of throwing              |
| Strict Mode Options      | Enable type safety and better error prevention               |
| `tsconfig.json` Strictness | Enables full strict mode and related checks                |

## 🔚 You’ve completed the TypeScript Core Notes!

- Looking to expand more? Explore:
- TS with Redux Toolkit
- Type Guards & Advanced Generics
- Real-world Project Scaffolding

## 🚨 Interview / Tricky Questions for “Error Handling & Strict Types”

### Q1. Why do we use `as Error` in a catch block?
In TypeScript (especially in strict mode), the `catch` block infers `error` as `unknown`.  
So we need type assertion to safely access properties like `.message`.

```ts
catch (error) {
  console.error((error as Error).message); // ✅ Safe
}
```

✅ This is safer than assuming it’s always an `Error`.

---

### Q2. What's the difference between `never` and `void` in error-throwing functions?

| Type  | Meaning                               | Example Use                     |
|--------|----------------------------------------|----------------------------------|
| `void` | Function returns nothing               | Logging, side effects            |
| `never`| Function never returns (throws/errors) | Error handling, crash guards     |

```ts
function fail(): never {
  throw new Error("Something went wrong");
}
```

---

### Q3. What does `strictNullChecks` actually prevent?
It forces you to **explicitly handle `null` or `undefined`**.

```ts
let name: string | null;

function greet(user: string) {
  console.log("Hi", user.toUpperCase());
}

greet(name); // ❌ Error in strictNullChecks mode
```

✅ Without `strictNullChecks`, this could lead to runtime errors.

---

### Q4. How do union result types improve error handling over throwing exceptions?

- ✅ Make errors part of the type system  
- ✅ Avoid try-catch nesting  
- ✅ Easier to reason about and test

```ts
type Result<T> = 
  | { success: true; data: T } 
  | { success: false; error: string };
```

---

### Q5. How can you ensure all class properties are initialized in strict mode?

You must either:
- Assign values in the constructor, **or**
- Use the definite assignment assertion (`!`)

```ts
class Person {
  name!: string; // ❗ Tell TS you’ll initialize it later
}
```

⚠️ Use `!` sparingly — it's like saying *"Trust me, I got this."*

---

### Q6. Why is enabling `"strict": true` in `tsconfig.json` recommended?

✅ It enables all major type-safety checks:
- Catch `null` / `undefined` bugs
- Prevent unsafe `any` usage
- Ensure functions and properties are properly typed
