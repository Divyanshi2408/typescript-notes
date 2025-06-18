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
