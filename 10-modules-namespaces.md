# 📦 10. Modules & Namespaces

---

## 📁 What are Modules?

Modules help organize code into separate files and reuse it across the application.

> ✅ Each file is a module in TypeScript if it uses `import` or `export`.

---

### 🔄 Exporting & Importing

```ts
// mathUtils.ts
export function add(a: number, b: number): number {
  return a + b;
}

// main.ts
import { add } from "./mathUtils";
console.log(add(2, 3));
```
## You can export:

- Functions
- Variables
- Classes
- Interfaces
- Types

## 🌐 Default Export
```
// greet.ts
export default function greet(name: string) {
  return `Hello, ${name}`;
}

// main.ts
import greet from "./greet";
console.log(greet("Divyanshi"));
```
⚠️ You can have only one default export per file.

## 📦 What are Namespaces?
Namespaces group related code together in the global scope.

```
namespace Geometry {
  export function area(width: number, height: number): number {
    return width * height;
  }
}

console.log(Geometry.area(5, 10));
```
⚠️ Namespaces are used mostly in older codebases or in non-module environments.

## ⚖️ Modules vs Namespaces

| Feature        | Modules                 | Namespaces                      |
|----------------|-------------------------|----------------------------------|
| Scope          | File-based              | Global                           |
| Syntax         | `import` / `export`     | `namespace`                      |
| Best Practice  | ✅ Recommended (modern) | 🚫 Legacy (avoid in modern apps) |


## ✅ Summary

| Concept           | Description                                                      |
|-------------------|------------------------------------------------------------------|
| Modules           | File-based code organization using `import` and `export`         |
| Default Export    | Exports a single value per file                                  |
| Named Export      | Export multiple values                                            |
| Namespaces        | Legacy way to organize code in the global scope                  |
| Recommendation    | Use modules for modern TypeScript projects                       |

## 📦 Interview / Tricky Questions for “Modules & Namespaces”

### Q1. What is the main difference between a `module` and a `namespace` in TypeScript?

| Aspect        | Module (ESM)              | Namespace                     |
|---------------|----------------------------|-------------------------------|
| Scope         | File-based                 | Global                        |
| Syntax        | `import` / `export`        | `namespace {}`                |
| Use Case      | Modern apps                | Script-based projects         |
| Tree-shaking  | ✅ Supported                | ❌ Not supported               |

---

### Q2. Can a file be both a module and a script in TypeScript?
❌ No.  
- If a file uses `import` or `export`, it is treated as a **module** and has its own scope.  
- Otherwise, it’s a **script**, and all declarations live in the global scope.

---

### Q3. What is a **barrel file** and when should you use it?
A **barrel file** is an `index.ts` file that **re-exports members** from other modules.  
It helps in **organizing** and **simplifying import paths**.

---

### Q4. Can you use **default and named exports** together?
✅ Yes, but imports need to match:

```ts
// lib.ts
export default function main() {}
export const helper = () => {};

// usage:
import main, { helper } from "./lib";
```

---

### Q5. Why are `namespaces` discouraged in modern TypeScript development?
- They **pollute the global scope**
- Not compatible with **module bundlers** (Webpack, Vite, etc.)
- **Better alternatives** exist using `import` / `export`

