# 📘 01. Introduction to TypeScript

---

## 📌 What is TypeScript?

TypeScript is an open-source programming language developed and maintained by Microsoft. It is a superset of JavaScript, meaning that any valid JavaScript code is also valid TypeScript code. The key distinction of TypeScript is the addition of static typing, which allows developers to define the types of variables, function parameters, and return values. 

> ✅ TypeScript = JavaScript + Types

- It adds optional static types to JavaScript.
- The code is written in `.ts` files and compiled to plain JavaScript (`.js`) using the TypeScript compiler (`tsc`).

---

## 💡 Why use TypeScript?

| Feature | JavaScript | TypeScript |
|--------|------------|------------|
| Type Safety | ❌ No | ✅ Yes |
| Compile-time Error Detection | ❌ No | ✅ Yes |
| Better IDE Support | ⚠️ Partial | ✅ Full |
| Large Codebase Scalability | ❌ Difficult | ✅ Easier |

### 🚀 Benefits in React/Next.js:
- Auto-completion & IntelliSense
- Catch bugs at compile-time
- Define Prop & State types in components
- Enforces cleaner code and contracts between components

---

## 🛠️ Installing TypeScript

To install TypeScript globally on your system:

```
npm install -g typescript
```
Or as a dev dependency in a project:

```
npm install --save-dev typescript
```
## Check if installed:

```
tsc --version
```
## ⚙️ Setting Up tsconfig.json
TypeScript uses tsconfig.json to configure the compiler options.

Create it manually:
```
npx tsc --init
```
This generates a tsconfig.json file like:

```
{
  "compilerOptions": {
    "target": "ES6",
    "module": "CommonJS",
    "strict": true,
    "esModuleInterop": true,
    "outDir": "./dist",
    "rootDir": "./src"
  }
}
```

## 🔧 You can modify it based on your project setup.

Example folder structure:
```
project/
├── src/
│   └── index.ts
├── dist/
└── tsconfig.json
```
To compile the project:

```
npx tsc
```

## Summary
- TypeScript is a superset of JavaScript with type safety.
- It improves developer experience, especially in large React/Next.js apps.
- Easy to install via NPM and set up with a tsconfig.json file.
